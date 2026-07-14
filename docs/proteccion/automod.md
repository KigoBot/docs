# Automod

Filtra mensajes individuales. Complementa al anti-raid: este se ocupa de eventos en masa, el automod de cada mensaje por separado.

## Qué detecta

Kigo implementa **6 reglas de automod**, todas configurables desde `/configuración` → **Auto Moderación**:

**`everyone` (EveryOne/Here)** — Bloquea mensajes que contienen `@everyone` o `@here`. Gestionado por AutoMod de Discord.

**`discord_links` (Enlaces a Discord)** — Bloquea mensajes que contienen invitaciones a otros servidores de Discord. Gestionado por AutoMod de Discord.

**`webs_links` (Enlaces web)** — Bloquea mensajes que contienen enlaces a páginas web. Gestionado por AutoMod de Discord. Acepta una `allowList` de dominios permitidos (configurable, separado por comas).

**`maliciosos_links` (Enlaces externos)** — Bloquea cualquier enlace que no sea de Discord. Kigo lo gestiona directamente: al detectar un enlace externo, silencia al autor. Cubre todos los URLs que no detecte la regla de Discord AutoMod.

**`ghostping` (Menciones fantasma)** — Detecta cuando un usuario menciona a otro miembro y luego borra su propio mensaje. Es una técnica muy común para molestar. Kigo silencia al autor 7 minutos y registra el evento en logs.

**`spam` (Prevenir Flood)** — Si alguien envía muchos mensajes en poco tiempo, se le silencia. Por defecto: 5 mensajes en 5 segundos y silencio de 15 minutos. El límite es configurable entre 1 y 25 mensajes.

## Lo que Kigo NO detecta

- **Palabras bloqueadas:** Kigo no tiene una lista de palabras bloqueadas. Si quieres filtrar slurs, marcas o palabras concretas, no hay forma nativa de hacerlo.
- **Repetición de mensajes:** Kigo no detecta si alguien envía el mismo mensaje varias veces seguidas (aunque el spam sí detecta frecuencia alta).
- **Menciones masivas a muchos usuarios:** Kigo solo bloquea `@everyone` y `@here`. Si alguien menciona a 50 usuarios uno a uno, no se detecta.
- **Imágenes con texto ofensivo:** No hay OCR ni moderación de imágenes.
- **Deepfakes ni voice cloning.** Fuera de su scope.

## Cómo funciona cada filtro

Cada filtro es independiente. Puedes activar todos o solo los que necesites.

### Reglas de AutoMod de Discord (`everyone`, `discord_links`, `webs_links`)

Kigo usa el sistema nativo de AutoMod de Discord. Cuando la regla está activa, Kigo crea una regla de AutoMod con el prefijo `KIGO-` y un mensaje de aviso predeterminado (no es personalizable por servidor). Si la regla está desactivada, Kigo elimina la regla de AutoMod correspondiente.

### Reglas gestionadas por Kigo (`maliciosos_links`, `ghostping`, `spam`)

Estas reglas las aplica Kigo directamente sobre los mensajes, no Discord.

- **`maliciosos_links`:** silencia al autor al detectar un enlace externo.
- **`ghostping`:** silencia al autor 7 minutos.
- **`spam`:** silencia al autor 15 minutos (con el límite por defecto).

## Configuración paso a paso

Ve a `/configuración` y entra en la sección **Auto Moderación** (o al paso 11 del asistente `/setup`). Verás un botón por regla:

- `Everyone/Here` (on/off)
- `Enlaces Discord` (on/off)
- `Enlaces Webs` (on/off + `allowList` de dominios permitidos)
- `Enlaces Externos` (on/off)
- `Menciones Fantasma` (on/off)
- `Prevenir Flood` (on/off + límite de mensajes)

Pulsa un botón para activarlo o desactivarlo. Para `Enlaces Webs`, además puedes editar la lista de dominios permitidos con un modal.

## Las sanciones

| Regla | Acción |
|---|---|
| `everyone` | AutoMod de Discord: borra el mensaje |
| `discord_links` | AutoMod de Discord: borra el mensaje |
| `webs_links` | AutoMod de Discord: borra el mensaje |
| `maliciosos_links` | Silencio (timeout) al autor |
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
- **No tiene listas negras de palabras.** Si quieres filtrar vocabulario concreto, no es posible con Kigo hoy por hoy.

## Siguiente paso

[Aprende cómo funciona la verificación →](verificacion.md), que es la forma más efectiva de filtrar multicuentas.
