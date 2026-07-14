# Qué es Kigo Premium

Kigo Premium se obtiene de dos formas:

1. **Suscripción en Stripe** (pago automático). Ejecutas `/premium comprar` en Discord, el bot crea un checkout de Stripe, pagas con tarjeta, y el premium se activa solo.
2. **Canjear un código gratuito** que el autor distribuye en eventos, colaboraciones o promociones puntuales. Usa `/premium canjear código:<código>`.

## Qué incluye

Todos los planes premium activan las mismas funciones avanzadas, sin importar el plan:

- **Castigo Progresivo de warns.** Configura reglas automáticas: a 3 warns, mute de 1h. A 5, mute de 1d. A 7, kick. Totalmente personalizable desde el panel de configuración (`/configuración` → Premium → Auto-Escalación).
- **Filtro Evasivo.** Detecta mensajes que intentan esquivar el automod usando homoglyphs (letras cirílicas que parecen latinas), base64, ROT13, zalgo, caracteres de ancho cero y otras técnicas de ofuscación. Emite un auto-warn automático al detectarlo.
- **Análisis de Amenazas.** El comando `/amenazas @usuario` muestra un perfil de riesgo 0-100 basado en warns, detecciones de automod, multicuentas, evasión, edad de la cuenta y más señales.

Estas tres funciones están activas en todos los servidores donde hayas activado premium.

## Los tres planes

La única diferencia entre planes es **cuántos servidores puedes activar premium**:

| Plan | Servidores | Cuándo tiene sentido |
|---|---|---|
| **Plan 1** | 3 | Un owner con 1-3 servidores propios |
| **Plan 2** | 5 | Un owner con una comunidad mediana en varios servidores |
| **Plan 3** | 7 | Redes de servidores, comunidades multi-idioma, equipos grandes |

### Precios

| Plan | Mensual | Anual (17% dto) |
|---|---|---|
| Plan 1 | 2,99 €/mes | 29,90 €/año |
| Plan 2 | 5,99 €/mes | 59,90 €/año |
| Plan 3 | 8,99 €/mes | 89,90 €/año |

## Cómo se obtiene

### Vía Stripe (pago)

1. En cualquier servidor con Kigo, ejecuta `/premium comprar plan:1 periodo:mensual`.
2. El bot crea un Checkout de Stripe y te da un botón link.
3. Paga con tarjeta (o Apple Pay / Google Pay si estás en móvil).
4. El premium se activa en unos segundos y te llega un DM de bienvenida.
5. Usa `/premium usar` en cada servidor donde quieras premium (requiere ser owner del servidor).

Si no recibes el DM tras pagar, abre un ticket en el [servidor de soporte](https://discord.gg/wmky5nBRR2) con el email que usaste en Stripe.

### Vía código gratuito

1. Consigue un código (los publica el autor en eventos o en su Discord de soporte).
2. En cualquier servidor con Kigo, ejecuta `/premium canjear código:<código>`.
3. El bot te asigna el plan del código. Luego usa `/premium usar` para activarlo en tus servidores.

Los códigos gratuitos siempre asignan **Plan 1** (3 servidores) y duran **30 días**.

## Personalizar el castigo progresivo

Con premium activo, puedes configurar las reglas de auto-escalación desde el panel de configuración:

1. Ve a `/configuración` → **Premium** → **Auto-Escalación**.
2. Añade reglas del tipo: "cuando el usuario alcance X warns, aplica Y acción (mute/ban/kick)".
3. Cada regla tiene duración configurable para el mute.
4. Las reglas se evalúan en orden al añadir un warn. La primera que coincida se ejecuta.

Esto te permite, por ejemplo:
- A 3 warns → mute de 1 hora
- A 5 warns → mute de 24 horas
- A 7 warns → kick
- A 10 warns → ban automático

## Gestión de la suscripción

| Acción | Comando |
|---|---|
| Suscribirse | `/premium comprar plan:X periodo:mensual\|anual` |
| Cancelar | `/premium cancelar` (sigue activo hasta fin de ciclo) |
| Cambiar de plan | `/premium cambiar plan:X` (Stripe cobra/devuelve la diferencia) |
| Ver estado actual | `/premium estado` |
| Activar en un servidor | `/premium usar` (siendo owner) |
| Quitar de un servidor | `/premium liberar` (siendo owner) |
| Canjear free code | `/premium canjear código:<código>` |

## Limitaciones

- Premium se paga solo vía Stripe. No se aceptan otros métodos de pago.
- Si un servidor cambia de owner, el premium sigue activo (el slot está vinculado al usuario que canjeó o pagó).
- Si tu suscripción vence, los slots se liberan. La configuración del servidor (warns, casos, automod) **se mantiene**, pero las funciones premium se desactivan hasta renovar.
- El premium **no incluye** backups automáticos, dashboard web premium, ni badges. Es solo acceso a las funciones premium.
- **No hay Customer Portal web**: toda la gestión (cancelar, cambiar plan) se hace desde Discord con `/premium`.

## Desactivar premium

Si quieres dejar de pagar o quitar premium de un servidor:

- **Quitar de un servidor**: usa `/premium liberar` dentro de ese servidor (siendo owner). El slot vuelve a tu cuota.
- **Cancelar la suscripción**: ejecuta `/premium cancelar`. La renovación no se cobra pero el premium sigue hasta el final del ciclo de facturación que ya pagaste.
- **No hay reembolso proporcional**. Si pagas un mes y cancelas al día 5, no se devuelve la parte proporcional. Sigues teniendo premium hasta el día 30.
