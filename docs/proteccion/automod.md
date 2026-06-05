# Automod

Filtra mensajes individuales. Complementa al anti-raid: este se ocupa de eventos en masa, el automod de cada mensaje por separado.

## Qué detecta

**Spam y flood** — Si alguien envía muchos mensajes en poco tiempo (configurable, por defecto 5 mensajes en 5 segundos), se le silencia 15 minutos y se borran los mensajes.

**Palabras bloqueadas** — Una lista de palabras que se borran automáticamente. Configurable, con tolerancia a mayúsculas y caracteres especiales.

**Enlaces a sitios peligrosos** — URLs acortadas (bit.ly, tinyurl, etc.) y dominios conocidos de phishing o malware. Se borran los mensajes y se advierte al usuario.

**Invites de Discord** — Mensajes que contengan invitaciones a otros servidores de Discord. Opcional: puedes permitir invitaciones a servidores específicos.

**Menciones masivas** — Si alguien menciona a @everyone, @here, o a más de X usuarios en un solo mensaje, se borra el mensaje y se silencia al autor.

**"Ghost pings"** — Mensajes que mencionan a usuarios y luego se borran. Es una técnica común para molestar. Kigo detecta cuando un mensaje con menciones se elimina y silencia al autor 7 minutos.

**Repetición de mensajes** — Si alguien envía el mismo mensaje varias veces en poco tiempo, se trata como spam.

## Cómo funciona cada filtro

Cada filtro es independiente. Puedes activar todos o solo los que necesites. Por ejemplo, si tu servidor es de programación, desactiva el filtro de "palabras bloqueadas" porque probablemente disparará falsos positivos con términos técnicos.

## Configuración paso a paso

Ve a `/configuración` y entra en la sección **Automod**. Verás una lista de interruptores:

- `Spam` (on/off + umbral)
- `Palabras bloqueadas` (on/off + lista de palabras)
- `Enlaces peligrosos` (on/off)
- `Invites de Discord` (on/off + lista de servidores permitidos)
- `Menciones masivas` (on/off + umbral)
- `Ghost pings` (on/off)
- `Mensajes repetidos` (on/off)

Para cada filtro, Kigo te muestra la configuración actual y te permite cambiarla con un menú o con texto.

## Las sanciones

Kigo usa el sistema nativo de AutoMod de Discord para la mayoría de los filtros. Cuando alguien incumple, Discord aplica las acciones configuradas en la regla. Las acciones concretas dependen de cada filtro:

**Menciones masivas (`@everyone` / `@here`)** — Borrar el mensaje, silenciar al usuario 7 minutos, registrar el evento en el canal de logs.

**Invites de Discord** — Borrar el mensaje, silenciar al usuario 10 minutos, registrar el evento en el canal de logs.

**Enlaces web sospechosos** — Borrar el mensaje, silenciar al usuario 10 minutos, registrar el evento en el canal de logs.

**Spam y flood** — Borrar los mensajes recientes del usuario, silenciar al usuario 15 minutos, publicar un aviso en el canal y registrar el evento en el canal de logs.

**Ghost pings** — Silenciar al usuario 7 minutos y registrar el evento en el canal de logs.

El usuario ve el borrado y el silencio aplicados por Discord, pero Kigo **no le envía ningún DM** con la norma que incumplió. La sanción se entera al intentar escribir y no poder (o al ver su mensaje desaparecer). Si quieres que reciba un aviso, configura el campo `customMessage` en `/configuración` → **Automod** → filtro correspondiente.

## Listas de palabras

Kigo viene con una lista por defecto de palabras bloqueadas (palabras malsonantes en español e inglés). Puedes:

- **Añadir palabras** a la lista
- **Quitar palabras** de la lista
- **Importar una lista** completa (por ejemplo, una lista de slurs o de marcas)

La lista distingue mayúsculas y minúsculas por defecto. Si quieres que "TONTO", "Tonto" y "tOnTo" se traten igual, activa la opción "ignorar mayúsculas".

## Whitelist en automod

Cualquier usuario, canal o rol en la lista blanca está exento del automod. Esto es crítico para:

- **Canales de staff**: donde los mods hablan entre ellos con jerga que dispararía el filtro.
- **Roles de moderación**: para que los mods puedan usar palabras bloqueadas si las necesitan (por ejemplo, citar un mensaje ofensivo).
- **Bots de utilidad**: bots que publican mensajes automáticos con URLs o menciones.

## Lo que NO hace

- **No entiende contexto.** Si alguien dice "voy a borrar este servidor mañana" en un canal de planificación, se borrará igual. El filtro no distingue ironías.
- **No procesa imágenes.** Si alguien envía una imagen con texto ofensivo, Kigo no lo detectará. Para eso necesitas un bot de moderación de imágenes.
- **No detecta deepfakes ni voice cloning.** Fuera de su scope.

## Siguiente paso

[Aprende cómo funciona la verificación →](verificacion.md), que es la forma más efectiva de filtrar multicuentas.
