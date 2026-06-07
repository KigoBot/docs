# Premium

Kigo Premium añade tres funciones avanzadas a la protección del servidor:

- **Castigo Progresivo de warns** — reglas automáticas que escalan la sanción.
- **Filtro Evasivo** — detecta mensajes que esquivan el automod.
- **Análisis de Amenazas** — `/amenazas @usuario` con perfil de riesgo 0-100.

Todas las funciones premium están activas en cada servidor donde actives premium. No hay tiers por función.

## Cómo se consigue

- **Vía Stripe** (pago automático). Ejecuta `/premium comprar`, el bot crea un checkout de Stripe, pagas con tarjeta, y el premium se activa solo. Sin códigos.
- **Vía código gratuito**. El autor reparte códigos en eventos, colaboraciones y promociones. Se canjean con `/premium canjear código:<código>`.

## Los tres planes

Lo único que cambia entre planes es cuántos servidores puedes activar premium:

| Plan | Servidores |
|---|---|
| Plan 1 | 3 |
| Plan 2 | 5 |
| Plan 3 | 7 |

Más detalles en [Qué es Kigo Premium](que-es.md).

## Páginas

- [Qué es Kigo Premium](que-es.md) — qué incluye, cómo se obtiene, planes.
- [Suscripción con Stripe](suscripcion-stripe.md) — setup del dashboard, eventos, runbook de soporte.
- [Canjear un código](canjear.md) — paso a paso de cómo canjear un free code.
- [Análisis de Amenazas](amenazas.md) — el comando `/amenazas` y cómo interpretar el puntaje.

## Lo que NO incluye premium

Para que quede claro:

- **No hay backups automáticos.** La configuración no se respalda sola. Si la pierdes, la recuperas con un backup que hayas exportado tú.
- **No hay dashboard web premium.** Toda la configuración se hace desde Discord con `/configuración`.
- **No hay badge premium visible en otros servidores.** El premium no se anuncia públicamente.
- **No hay soporte prioritario extra.** El soporte en el servidor de Discord es igual para todos.

Premium solo desbloquea las tres funciones mencionadas arriba. Si necesitas alguna de ellas, premium vale la pena. Si no, el bot funciona perfectamente bien sin premium.
