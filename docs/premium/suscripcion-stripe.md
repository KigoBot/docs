# Suscripción de pago en Stripe

Kigo Premium se paga a través de **Stripe**, no a través del bot. Cuando un usuario ejecuta `/premium comprar`, el bot crea una Checkout Session de Stripe con el Discord ID pre-rellenado en la metadata, y devuelve un link de pago. Tras pagar, Stripe envía un webhook al bot que activa el premium automáticamente.

## Arquitectura

```
Usuario (Discord)            Bot (Docker)                  Stripe                GitHub Pages
       │                          │                          │                       │
       │ /premium comprar         │                          │                       │
       ├─────────────────────────►│                          │                       │
       │                          │ 1. create Checkout       │                       │
       │                          ├─────────────────────────►│                       │
       │                          │◄────────  session.url ───┤                       │
       │◄── mensaje con link ─────┤                          │                       │
       │                          │                          │                       │
       │ clic en link de pago    │                          │                       │
       ├─────────────────────────────────────────────────────►│                       │
       │                          │                          │ 2. user pays          │
       │                          │                          │                       │
       │◄── redirect browser ─────────────────────────────────┤                       │
       │   (success_url)          │                          │                       │
       │   https://kigobot.github.io/docs/pago-completado.html?session_id=cs_xxx     │
       │                          │                          │                       │
       │                          │ 3. POST /wh_xxxx/stripe  │                       │
       │                          │◄─────────────────────────┤                       │
       │                          │  (verifica firma HMAC)  │                       │
       │                          │  upsert DB, max_slots,   │                       │
       │                          │  manda DM                │                       │
       │◄── DM bienvenida ────────┤                          │                       │
       │                          │                          │                       │
       │ /premium estado          │                          │                       │
       ├─────────────────────────►│                          │                       │
       │◄── "Suscripción Stripe" ─┤                          │                       │
```

### Componentes

| Componente | Dónde corre | Responsabilidad |
|---|---|---|
| **Bot** | Tu servidor (Docker, `127.0.0.1:9180` interno) | Crea Checkout Sessions, recibe webhooks, gestiona premium en BD. |
| **Webhook URL** | URL pública (tunnel) → `127.0.0.1:9180/wh_xxxxxxxxxxxx/stripe` | Endpoint POST que valida la firma y procesa el evento. |
| **Success/Cancel pages** | GitHub Pages (`pago-completado.html`, `pago-cancelado.html`) | HTML estático, `noindex`, no enlazadas. Son solo cosméticas: la activación real la dispara el webhook. |
| **Stripe Dashboard** | dashboard.stripe.com | Define los Prices con metadata, el webhook endpoint con URL pública, y guarda el `whsec_...` que va en `.env`. |

## Flujo end-to-end

1. El usuario ejecuta `/premium comprar plan:1 periodo:mensual` en Discord.
2. El bot crea una `Checkout Session` en modo suscripción con `metadata.discord_id` y `metadata.plan` y devuelve un link de pago en el mensaje.
3. El usuario abre el link, ve el Checkout de Stripe, paga con tarjeta (u otro método habilitado).
4. Stripe redirige el navegador del usuario a `https://kigobot.github.io/docs/pago-completado.html?session_id=cs_xxx` (página estática en la doc).
5. **En paralelo**, Stripe envía el webhook `checkout.session.completed` (y otros) al endpoint público del bot.
6. El bot verifica la firma HMAC-SHA256, extrae el Discord ID, hace upsert en `premium_subscriptions` y `users`, y manda un DM de bienvenida.
7. El usuario ejecuta `/premium usar` en cada servidor donde quiera premium (siendo owner).
8. La suscripción se renueva automáticamente cada mes/año hasta que el usuario ejecute `/premium cancelar`.

> **Importante**: la redirección a la página de éxito (paso 4) NO activa el premium. Es solo visual. La activación ocurre en el paso 6 vía webhook. Si el usuario ve "Pago completado" pero el premium no se activa, el problema es que el webhook no llegó al bot.

## Setup en el dashboard de Stripe

### 1. Crear cuenta y activar Tax

1. Crea una cuenta en [dashboard.stripe.com](https://dashboard.stripe.com).
2. En **Settings → Tax**, activa Stripe Tax (0,5% por transacción, calcula IVA/impuestos automáticamente).
3. Activa el **modo test** mientras desarrollas (es el interruptor arriba a la derecha).

### 2. Crear los productos y precios

Crea 3 productos (uno por plan), cada uno con 2 precios (mensual y anual). La metadata se pone en los **Prices**, no en los Products:

**Metadata del Price (clave=valor):**

| Price | Metadata |
|---|---|
| Plan 1 mensual (2,99 €/mes) | `plan = plan1`, `duration = monthly` |
| Plan 1 anual (29,90 €/año) | `plan = plan1`, `duration = annual` |
| Plan 2 mensual (5,99 €/mes) | `plan = plan2`, `duration = monthly` |
| Plan 2 anual (59,90 €/año) | `plan = plan2`, `duration = annual` |
| Plan 3 mensual (8,99 €/mes) | `plan = plan3`, `duration = monthly` |
| Plan 3 anual (89,90 €/año) | `plan = plan3`, `duration = annual` |

> Importante: la metadata `plan` y `duration` es la fuente de verdad del mapeo. El bot NO guarda los Price IDs en variables de entorno, los descubre leyendo la metadata de los Prices al arrancar.

### 3. Exponer el endpoint del webhook (necesario)

El bot corre en tu servidor en `127.0.0.1:9180` (dentro del contenedor Docker). Stripe necesita una URL pública para hacer `POST`. **No abres puertos en tu router/firewall**: usas un tunnel que inicia una conexión saliente.

**Opción A: Cloudflare Tunnel (recomendado)**

Requiere un dominio en Cloudflare (gratis). Setup en 5 minutos:

1. Instala `cloudflared` en el host (no en el contenedor).
2. `cloudflared tunnel login` (autoriza tu dominio).
3. `cloudflared tunnel create kigo-bot`.
4. Crea `~/.cloudflared/config.yml`:
   ```yaml
   tunnel: kigo-bot
   credentials-file: /home/TU_USUARIO/.cloudflared/<TUNNEL_ID>.json
   ingress:
     - hostname: kigo.tu-dominio.com
       service: http://host.docker.internal:9180
     - service: http_status:404
   ```
5. `cloudflared tunnel route dns kigo-bot kigo.tu-dominio.com`.
6. `cloudflared tunnel run kigo-bot` (déjalo corriendo, o como servicio systemd).

Con esto, `https://kigo.tu-dominio.com/wh_xxxxxxxxxxxx/stripe` se reenvía al `127.0.0.1:9180/wh_xxxxxxxxxxxx/stripe` del contenedor.

**Opción B: trycloudflare.com (sin cuenta, temporal)**

Sin cuenta de Cloudflare ni dominio. Te da una URL random que cambia cada vez:

```bash
cloudflared tunnel --url http://host.docker.internal:9180
```

Imprime algo como `https://random-word-random.trycloudflare.com`. **La URL cambia cada vez que arrancas `cloudflared`**, así que solo vale para pruebas cortas. Para cada sesión, tendrías que actualizar el webhook en el Dashboard de Stripe.

**Opción C: VPS propio con reverse proxy**

Si tienes un servidor accesible desde internet (VPS, dedicated) con nginx o caddy:

```nginx
location /wh_xxxxxxxxxxxx/stripe {
  proxy_pass http://TU_IP_LOCAL:9180/wh_xxxxxxxxxxxx/stripe;
  proxy_set_header Host $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-Forwarded-Proto $scheme;
}
```

### 4. Crear el webhook en el Dashboard

1. Ve a **Developers → Webhooks → Add endpoint**.
2. **URL:** `https://<tu-dominio-o-tunnel>/wh_xxxxxxxxxxxx/stripe` (mismo path ofuscado que `STRIPE_WEBHOOK_PATH` en `src/config/stripe.ts`).
3. **Eventos a enviar:**
   - `checkout.session.completed`
   - `customer.subscription.created`
   - `customer.subscription.updated`
   - `customer.subscription.deleted`
   - `invoice.paid`
   - `invoice.payment_failed`
   - `charge.refunded`
4. Copia el **Signing secret** (`whsec_...`) que muestra el dashboard al crear el endpoint → `.env` como `STRIPE_WEBHOOK_SECRET`.

> **Por qué el path está ofuscado**: el path por defecto `/webhook/stripe` es adivinable y bots automatizados lo escanean en millones de dominios. Cambiándolo a `/wh_<token-aleatorio>/stripe` reduces la superficie de discovery. La firma HMAC-SHA256 de Stripe protege la lógica igualmente: sin firma válida, el bot rechaza el POST con 401. Un atacante que descubra la URL no puede hacer nada útil.

### 5. Variables de entorno

Añade a `.env`:

```bash
STRIPE_SECRET_KEY=sk_test_xxx      # sk_live_... en producción
STRIPE_WEBHOOK_SECRET=whsec_xxx    # el signing secret del Dashboard
PUBLIC_URL=https://kigobot.github.io/docs/   # URL de la doc (para success/cancel URLs)
```

> **Sobre `stripe listen`**: ya NO se usa en producción. Era solo para desarrollo local. En producción el webhook se crea en el Dashboard y se queda ahí permanente. Si quieres seguir usando `stripe listen` para tests locales, puedes, pero la URL del webhook en el Dashboard apunta a tu dominio público (no a localhost), así que `stripe listen` no interviene.

## Páginas de éxito y cancelación

Stripe redirige el navegador del usuario tras pagar (o cancelar) a una de estas URLs:

| URL | Cuándo se muestra |
|---|---|
| `https://kigobot.github.io/docs/pago-completado.html?session_id=cs_xxx` | El usuario completó el pago. |
| `https://kigobot.github.io/docs/pago-cancelado.html` | El usuario cerró Stripe sin pagar. |

Estas páginas son **HTML estático** servido por GitHub Pages, no por el bot. Están en `docs-site/docs/pago-completado.html` y `docs-site/docs/pago-cancelado.html`, declaradas como `extra_files` en `mkdocs.yml` para que se copien al output sin procesarse como Markdown.

**Características de seguridad:**

- `<meta name="robots" content="noindex, nofollow, noarchive">` → Google no las indexa.
- `<meta name="googlebot" content="noindex, nofollow">` → belt and suspenders.
- NO aparecen en `nav:` del `mkdocs.yml`, así que no hay link en la navegación.
- NO aparecen en el `sitemap.xml` (MkDocs solo sitemap-ea las páginas en `nav:`).
- NO aparecen en el `search_index.json` (idem).
- La URL exacta lleva un `session_id=cs_xxx` aleatorio: solo la conoce el comprador y Stripe.

> Si quieres verificarlas en local: `mkdocs serve` desde `docs-site/`. Las páginas se ven en `http://localhost:8000/pago-completado.html` y `http://localhost:8000/pago-cancelado.html`.

## Cambiar de test a live

1. Apaga el bot.
2. En el dashboard de Stripe, desactiva el **modo test** (es un interruptor global).
3. **Crea 6 nuevos Prices en live mode** con `--live` en la CLI. Los Prices de test NO se pueden migrar a live, hay que crearlos de nuevo con la misma metadata.
4. Crea un nuevo webhook endpoint en live mode apuntando a `https://<tu-dominio>/wh_xxxxxxxxxxxx/stripe` y suscríbete a los 7 eventos. Copia el nuevo `whsec_...`.
5. Activa **Stripe Tax** (Settings → Tax → Enable) si no lo hiciste antes.
6. Cambia `.env`:
   - `STRIPE_SECRET_KEY=sk_live_...` (una NUEVA, no la que esté comprometida)
   - `STRIPE_WEBHOOK_SECRET=whsec_...` (el del nuevo endpoint de producción)
7. Re-arranca el bot.

> **Rota las claves antes de producción**: si alguna vez pegaste `sk_live_` o `pk_live_` en un chat, log, o issue tracker, rótala desde Dashboard → Developers → API keys → Roll antes de salir a producción.

## Eventos y su manejo

| Evento de Stripe | Qué hace el bot |
|---|---|
| `checkout.session.completed` | Activa premium: lee `session.metadata.discord_id`, busca el `subscription` en Stripe, extrae el plan del `price.metadata`, hace upsert en `premium_subscriptions` y `users`, y envía DM de bienvenida. |
| `customer.subscription.created` | Misma lógica que el anterior pero buscando el Discord ID por `customer.id` en la BD (por si llega antes el evento de subscripción que el de checkout, lo cual es raro pero posible). |
| `customer.subscription.updated` | Actualiza el `plan`, `current_period_end` y `cancel_at_period_end`. Si el usuario acaba de marcar `cancel_at_period_end`, envía DM avisando. |
| `customer.subscription.deleted` | Marca la suscripción como `expired`, pone `users.max_slots=0` y envía DM de expiración. |
| `invoice.paid` | Actualiza `current_period_end` (renovación). |
| `invoice.payment_failed` | Marca la suscripción como `past_due` pero NO revoca slots. Stripe hace Smart Retries automáticamente durante ~3 semanas. Envía DM al usuario avisando. |
| `charge.refunded` | Revoca slots inmediatamente y envía DM. |

## Política de pagos fallidos

**Decisión:** mantener los slots activos durante los Smart Retries de Stripe (hasta ~3 semanas). Solo se revocan cuando llega `customer.subscription.deleted` después de que agoten los reintentos. Esto es más user-friendly que revocar al primer fallo.

Si en el futuro quieres ser más estricto, edita el handler de `invoice.payment_failed` en `src/billing/providers/StripeProvider.ts` y cambia el `set({ status: 'past_due' })` por una llamada a `markExpiredAndRevoke()`.

## Cancelar y cambiar plan

| Acción | Comando | Lo que hace |
|---|---|---|
| Cancelar | `/premium cancelar` | `stripe.subscriptions.update({ cancel_at_period_end: true })`. El premium sigue hasta el fin del ciclo, luego Stripe envía `subscription.deleted` y se revocan slots. |
| Cambiar plan | `/premium cambiar plan:2` | `stripe.subscriptions.update` con `proration_behavior: 'create_prorations'`. Stripe cobra/devuelve la diferencia automáticamente. Los slots se actualizan al recibir el webhook. |

## No hay Customer Portal

No usamos Stripe Billing de pago, así que **no hay portal de auto-gestión**. Todo se hace desde Discord:
- Cancelar: `/premium cancelar`
- Cambiar plan: `/premium cambiar`
- Actualizar método de pago: contactar soporte (el admin lo cambia desde el Dashboard de Stripe).

Si en el futuro quieres self-service completo, hay que activar Stripe Billing (0,5-0,8% extra por transacción) y añadir un comando `/premium gestionar` que abra el Customer Portal.

## Troubleshooting: "Pagué pero no se activó"

El webhook es el que activa el premium. Si la página de éxito sale pero el premium no se activa, el webhook no llegó. Diagnóstico en orden:

1. **¿El tunnel / reverse proxy está corriendo?**
   - `cloudflared tunnel info kigo-bot` debe mostrar el tunnel activo.
   - O `curl https://kigo.tu-dominio.com/health` debe responder 200.
   - Si el tunnel se cayó, los webhooks se pierden (Stripe reintenta durante 3 días, pero en este tiempo el usuario está sin premium).

2. **¿El `STRIPE_WEBHOOK_SECRET` del `.env` coincide con el del Dashboard?**
   - Dashboard → Developers → Webhooks → click en el endpoint → "Reveal" signing secret.
   - Compara con `grep STRIPE_WEBHOOK_SECRET .env`.
   - Si no coinciden (porque creaste un nuevo endpoint), actualiza y reinicia.

3. **¿El bot está vivo?**
   - `docker compose ps kigo-bot` debe decir `running`.
   - `docker logs kigo-bot --tail 50 | grep webhook` debería mostrar el último webhook procesado.

4. **¿Aparecen los webhooks en los logs del Dashboard?**
   - Dashboard → Developers → Webhooks → click en el endpoint → "Logs" o "Attempts".
   - Si ves 200, el bot respondió bien. Si ves 4xx/5xx, hay un error.
   - Si no aparece nada, Stripe no llegó a tu endpoint (tunnel caído o URL mal escrita).

5. **Reenviar el webhook manualmente**:
   - Dashboard → Developers → Events → busca el evento perdido → "Resend" (lo envía de nuevo a la misma URL).
   - O desde la CLI: `stripe events resend evt_xxx`.

## Runbook para soporte

| Situación | Pasos |
|---|---|
| El usuario pagó pero no se activó | 1. Verificar logs del Dashboard (Developers → Webhooks → Logs). 2. Si ves un 200 ahí, el bot lo procesó — busca el error en `docker logs kigo-bot`. 3. Si ves un 4xx/5xx, mira el cuerpo de la respuesta y arregla el bug. 4. Si no ves nada, el tunnel está caído o la URL está mal. 5. Como último recurso, buscar el `sub_xxx` en Dashboard → Customers y meterlo a mano en la BD (ver filas siguientes). |
| Reembolsar | 1. Dashboard → Payments → click en el pago → Refund. 2. Stripe envía `charge.refunded`, el bot revoca los slots automáticamente. 3. Si no llega el webhook, en la BD: `UPDATE premium_subscriptions SET status='expired' WHERE id='sub_xxx';` y `UPDATE users SET max_slots=0 WHERE id='userId';`. |
| Pago fallido persistente | El usuario no actualizó su método de pago y agotó los reintentos. Stripe envía `subscription.deleted`, el bot revoca. Si quieres reactivar manualmente: pedirle que compre de nuevo. |
| Cambiar de plan manualmente | 1. Pedir al usuario que use `/premium cambiar`. 2. Si hay error, hacerlo desde Dashboard → Subscriptions → click en la sub → Update subscription → cambiar el price. 3. El webhook `subscription.updated` actualiza la BD. |
| Webhook perdido | 1. En Dashboard → Webhooks → click en el endpoint → Resend. 2. O ejecutar `stripe events resend evt_xxx`. 3. O esperar a la próxima ejecución del cron de sync (cada 60 min), que reconcilia. |

## Estructura del código

```
src/
├── billing/
│   ├── errors.ts                       BillingError normalizado
│   ├── types.ts                        Interfaz BillingProvider
│   ├── registry.ts                     Routing de webhooks por path
│   ├── sync.ts                         Cron de sincronización
│   ├── index.ts                        Barrel
│   └── providers/
│       └── StripeProvider.ts           Única implementación actual
├── config/
│   └── stripe.ts                       STRIPE_PUBLIC_URL, STRIPE_WEBHOOK_PATH ofuscado
├── services/
│   ├── StripeCheckout.ts               Helpers para crear/cancelar/cambiar
│   └── StripePriceCache.ts             Caché (plan, duration) → price_id
└── slashCommands/Premium/
    └── premium.ts                      /premium comprar|cancelar|cambiar|...
```

```
docs-site/
├── mkdocs.yml                          Declara extra_files para las páginas
└── docs/
    ├── pago-completado.html            Success page (noindex, no en nav)
    └── pago-cancelado.html             Cancel page (noindex, no en nav)
```

## Limitaciones conocidas

- **No hay Customer Portal**: el self-service se hace vía comandos en Discord. Si quieres portal web, hay que activar Stripe Billing.
- **Reintentos de pago**: no se pueden customizar desde el bot. Se usa la configuración por defecto de Stripe (4 reintentos en 3 semanas).
- **Códigos de descuento**: están habilitados en Checkout (`allow_promotion_codes: true`). El bot NO crea cupones, se crean desde el Dashboard de Stripe.
- **Apple Pay / Google Pay**: habilitados automáticamente por Stripe en dispositivos compatibles. No requiere config extra.
- **Multi-currency**: el bot asume EUR. Si quieres otras monedas, hay que añadir opciones a `/premium comprar` y crear Prices en esas monedas.
- **Webhook path ofuscado está hardcodeado**: si quieres cambiarlo, edita `STRIPE_WEBHOOK_PATH` en `src/config/stripe.ts` Y la URL del webhook en el Dashboard de Stripe (deben coincidir). Se eligió hardcodeado (vs `env var`) porque cambiarlo es raro y queremos que el código sea la fuente de verdad.
