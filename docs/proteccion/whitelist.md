# Lista blanca

La lista blanca (o "whitelist") es el mecanismo de excepciones. Usuarios, canales o roles específicos que NO se ven afectados por la protección de Kigo.

!!! warning "No hay comando `/whitelist`"
    No existe un slash command `/whitelist`. La lista blanca se gestiona **exclusivamente** desde `/configuración` → **Lista Blanca** (también accesible como paso 5 del asistente `/setup`).

## Para qué sirve

Imagina que tienes un bot de música en tu servidor. Este bot crea canales cada vez que alguien le pide una canción. Sin whitelist, Kigo interpretaría eso como "creación masiva de canales" y banearía al bot.

Con whitelist, le dices a Kigo: "este bot y sus canales están exentos, no los toques".

Lo mismo con:

- **Tu staff:** para que puedan reorganizar canales sin disparar el anti-raid.
- **Canales de moderación:** donde los mods hablan con jerga que dispararía el automod.
- **Roles de administración:** para que puedan publicar enlaces sin filtros.
- **Categorías de bots:** donde se permite la creación libre de canales.

## Lo que la whitelist afecta

- **Anti-raid:** usuarios, canales y roles exentos no disparan la detección.
- **Automod:** mensajes de usuarios exentos no se filtran.
- **Verificación:** usuarios exentos no necesitan verificar (revisar la lógica exacta en la configuración del servidor).
- **Sanciones automáticas:** sanciones no se aplican a exentos.

## Lo que la whitelist NO afecta

- **Comandos de moderación manuales.** Si un moderador usa `/ban` contra alguien en la whitelist, el ban se ejecuta igualmente. La whitelist no es un escudo contra la moderación humana.
- **Anti-raid contra multicuentas.** La multicuenta es global, no por usuario.
- **Permisos del bot.** Si Kigo no tiene un permiso en un canal, no lo va a tener por estar en la whitelist.

## Cómo añadir elementos

Ve a `/configuración` y entra en la sección **Lista Blanca**. Verás tres select-menus (uno por tipo de elemento) y un botón "Limpiar Lista Blanca":

- **Añadir usuario:** select menu de usuarios del servidor. Puedes añadir hasta 25 a la vez. Se quitan y se ponen desde el mismo menú.
- **Añadir rol:** igual, con roles del servidor.
- **Añadir canal:** select menu de canales (texto o categorías, hasta 25 a la vez).

Kigo también detecta automáticamente "patrones" sospechosos. Si tienes 20 bots que crean canales por separado, considera exentar la categoría entera en vez de cada canal individual.

## Reglas importantes

**No abuses de la whitelist.** Cada exención debilita la protección. Antes de añadir a alguien, pregúntate: "¿de verdad este elemento necesita estar exento?". Si la respuesta es "me da pereza configurar otra cosa", busca la otra solución.

**Revisa la whitelist periódicamente.** Cada 2-3 meses, mira quién está en la whitelist y si sigue mereciendo estarlo. Miembros que ya no son staff, bots que se desinstalaron, canales que ya no existen. El botón "Limpiar Lista Blanca" resetea la lista completa si quieres empezar de cero.

**Un usuario en la whitelist sigue siendo responsable.** Si exentas a un usuario porque es de confianza y luego abusa, la culpa es de quien lo añadió a la whitelist, no de Kigo.

## Whitelist vs roles de Discord

Discord ya tiene su propio sistema de permisos. ¿Por qué no usar esos directamente?

La whitelist de Kigo hace cosas que los permisos de Discord no pueden:

- **Eximir de la detección de spam** (no se puede hacer solo con permisos).
- **Eximir de la verificación** (los permisos de Discord no aplican a un sistema externo como el de Kigo).
- **Eximir de las sanciones automáticas** sin tener que darle permisos especiales al usuario.

Usa los permisos de Discord para "este usuario no puede usar el canal X". Usa la whitelist de Kigo para "este usuario no se ve afectado por mi protección".

## Lo que NO hace

- **No añade permisos al usuario.** Si un usuario en la whitelist no puede leer un canal por sus roles de Discord, Kigo no lo va a cambiar.
- **No oculta al usuario de los logs.** Los logs muestran todo lo que pasa, incluyendo lo que hacen los usuarios en la whitelist.
- **No es infinita.** Si necesitas muchísimas entradas, Kigo no avisa de un límite duro: la lista se guarda en base de datos y su rendimiento escala con el tamaño del servidor.

## Siguiente paso

[Aprende qué hacer si sufres un raid →](limpieza-post-raid.md), incluyendo el comando `/eliminar-raid` que limpia los canales y roles duplicados.
