# Automod

Filtra mensajes individuales. Complementa al anti-raid: este se ocupa de eventos en masa, el automod de cada mensaje por separado.

## Qué detecta

Kigo implementa **5 reglas de automod**, todas configurables desde `/configuración` → **Auto Moderación**:

**`everyone` (EveryOne/Here)** — Bloquea mensajes que contienen `@everyone` o `@here`. Las sanciones las aplica Discord nativamente, no Kigo. Kigo crea una regla de AutoMod de Discord con un mensaje de aviso predefinido.

**`discord_links` (Enlaces a Discord)** — Bloquea mensajes que contienen invitaciones a otros servidores de Discord (tipo `discord.gg/...`, `discord.com/invite/...`, etc.). Implementado como regla de AutoMod de Discord.

**`webs_links` (Enlaces web)** — Bloquea mensajes que contienen enlaces a páginas web. Implementado como regla de AutoMod de Discord. Acepta una `allowList` de dominios permitidos (configurable, separado por comas).

**`ghostping` (Menciones fantasma)** — Detecta cuando un usuario menciona a otro miembro y luego borra su propio mensaje. Es una técnica muy común para molestar. Kigo silencia al autor 7 minutos y registra el evento en logs.

**`spam` (Prevenir Flood)** — Si alguien envía muchos mensajes en poco tiempo, se le silencia. Por defecto: 5 mensajes en 5 segundos y silencio de 15 minutos. El límite es configurable entre 1 y 25 mensajes.

![Reglas activas del AutoMod](images/automod-reglas.png) — _pendiente de captura real_

## Lo que Kigo NO detecta (por ahora)

Aclaración importante: el automod de Kigo **no incluye** las siguientes features. Si las necesitas, avisa en el servidor de soporte para próximas versiones.

- **Palabras bloqueadas:** Kigo no tiene una lista de palabras bloqueadas. Si quieres filtrar slurs, marcas o palabras concretas, no hay forma nativa de hacerlo.
- **Enlaces acortados (bit.ly, tinyurl, etc.):** Kigo no detecta URLs acortadas en mensajes de usuarios. Si alguien comparte un enlace acortado, pasa el filtro.
- **Repetición de mensajes:** Kigo no detecta si alguien envía el mismo mensaje varias veces seguidas.
- **Menciones masivas a muchos usuarios:** Kigo solo bloquea `@everyone` y `@here`. Si alguien menciona a 50 usuarios uno a uno, no se detecta.
- **Imágenes con texto ofensivo:** No hay OCR ni moderación de imágenes.
- **Mensajes en otros idiomas:** El filtro es agnóstico al idioma, pero Kigo no busca frases concretas en inglés/español/lo que sea.

## Cómo funciona cada filtro

Cada filtro es independiente. Puedes activar todos o solo los que necesites. Por ejemplo, en un servidor de programación puede que te interese desactivar `webs_links` para permitir compartir enlaces a documentación.

### Reglas de AutoMod de Discord (`everyone`, `discord_links`, `webs_links`)

Kigo usa el sistema nativo de AutoMod de Discord. Cuando la regla está activa, Kigo crea una regla de AutoMod con el prefijo `KIGO-` y un mensaje de aviso predeterminado (no es personalizable por servidor). Si la regla está desactivada, Kigo elimina la regla de AutoMod correspondiente.

### Reglas gestionadas por Kigo (`ghostping`, `spam`)

Estas reglas las aplica Kigo directamente sobre los mensajes, no Discord. Cuando alguien las incumple:

- **`ghostping`:** se silencia al autor 7 minutos.
- **`spam`:** se silencia al autor 15 minutos (con el límite por defecto).

## Configuración paso a paso

Ve a `/configuración` y entra en la sección **Auto Moderación** (o al paso 11 del asistente `/setup`). Verás un botón por regla:

- `Everyone/Here` (on/off)
- `Enlaces Discord` (on/off)
- `Enlaces Webs` (on/off + `allowList` de dominios permitidos)
- `Menciones Fantasma` (on/off)
- `Prevenir Flood` (on/off + límite de mensajes)

Pulsa un botón para activarlo o desactivarlo. Para `Enlaces Webs`, además puedes editar la lista de dominios permitidos con un modal.

## Las sanciones

| Regla | Acción |
|---|---|
| `everyone` | Regla de AutoMod de Discord: borra el mensaje y aplica la acción definida por Discord |
| `discord_links` | Regla de AutoMod de Discord: borra el mensaje y aplica la acción definida por Discord |
| `webs_links` | Regla de AutoMod de Discord: borra el mensaje y aplica la acción definida por Discord |
| `ghostping` | Silencio (timeout) de 7 minutos al autor |
| `spam` | Silencio (timeout) de 15 minutos al autor (con el límite por defecto) |

El usuario ve el borrado y el silencio aplicados, pero Kigo **no le envía ningún DM** con la norma que incumplió. La sanción la ve al intentar escribir y no poder (o al ver su mensaje desaparecer).

## Mensajes de aviso

Los mensajes de aviso que ves cuando se dispara una regla de AutoMod de Discord (los textos como "No hagas menciones a everyone o here.") **no se pueden personalizar por servidor**. Son textos fijos definidos en el código de Kigo.

## Whitelist en automod

Cualquier usuario, canal o rol en la lista blanca está exento del automod. Esto es crítico para:

- **Canales de staff:** donde los mods hablan entre ellos con jerga que dispararía el filtro.
- **Roles de moderación:** para que los mods puedan publicar enlaces de Discord o webs sin problemas.
- **Bots de utilidad:** bots que publican mensajes automáticos con URLs o menciones.

Más detalles en [Lista blanca](whitelist.md).

## Lo que NO hace

- **No entiende contexto.** Si alguien dice "voy a borrar este servidor mañana" en un canal de planificación, se borrará igual. El filtro no distingue ironías.
- **No procesa imágenes.** Si alguien envía una imagen con texto ofensivo, Kigo no lo detectará.
- **No detecta deepfakes ni voice cloning.** Fuera de su scope.
- **No tiene listas negras de palabras.** Si quieres filtrar vocabulario concreto, no es posible con Kigo hoy por hoy.

## Siguiente paso

[Aprende cómo funciona la verificación →](verificacion.md), que es la forma más efectiva de filtrar multicuentas.
