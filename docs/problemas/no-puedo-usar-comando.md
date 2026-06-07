# No puedo usar un comando

Discord te muestra el comando, pero al ejecutarlo te da error o no pasa nada. Esto es lo más común: falta un permiso.

## Diagnóstico rápido

Cuando intentas usar un comando, Discord te muestra uno de estos mensajes:

### "Esta aplicación no tiene permiso para..."

Significa que **Kigo** no tiene el permiso necesario. Solución:

1. Ve a `Configuración del servidor > Roles`.
2. Busca el rol "Kigo".
3. Activa el permiso que falta (cada comando requiere uno específico, ver tabla abajo).
4. Espera 1 minuto a que Discord propague el cambio.

### "Missing Permissions"

Kigo responde con este mensaje cuando intenta hacer algo (banear, borrar) y no puede. La causa suele ser la misma que arriba: un permiso que falta en el rol de Kigo.

### "Solo el owner del servidor puede..."

El comando requiere ser el owner. Solo el owner del servidor (no mods) puede ejecutarlo. Si no eres el owner, pídele a él que lo ejecute.

### "Tu rol no tiene permisos suficientes"

Tu rol no tiene el permiso necesario. Solución:

1. Ve a `Configuración del servidor > Roles`.
2. Busca tu rol.
3. Activa el permiso que falta.

## Permisos por comando

| Comando | Permiso requerido (en tu rol) | Permiso requerido (en Kigo) |
|---|---|---|
| `/ban` | Banear miembros | Banear miembros |
| `/unban` | Banear miembros | Banear miembros |
| `/kick` | Expulsar miembros | Expulsar miembros |
| `/mute` | Moderar miembros | Moderar miembros |
| `/unmute` | Moderar miembros | Moderar miembros |
| `/warn`, `/warns`, `/unwarn` | Moderar miembros | — |
| `/case`, `/modlogs` | — | — |
| `/clear` | Gestionar mensajes | Gestionar mensajes, Leer historial |
| `/lock`, `/unlock` | Gestionar canales | Gestionar canales |
| `/hide`, `/show` | Gestionar canales | Gestionar canales |
| `/nuke` | Gestionar canales | Gestionar canales |
| `/slow-mode` | Gestionar canales | Gestionar canales |
| `/setup` | Owner del servidor | — |
| `/configuración` | Owner del servidor | — |
| `/eliminar-raid` | Owner del servidor | Administrador |
| `/premium usar` | Owner del servidor | — |
| `/premium liberar` | Owner del servidor | — |
| `/premium canjear` | — | — |
| `/premium estado` | — | — |
| `/ayuda`, `/botinfo`, `/clusters`, `/info-user` | — | — |

## Si los permisos están bien pero sigue fallando

Revisa estas cosas raras:

**Jerarquía de roles.** En Discord, los roles tienen un orden. Si tu rol está por debajo del rol del usuario al que quieres banear, no podrás. La solución es subir tu rol en la jerarquía (arrastrándolo hacia arriba en la lista de roles).

**Permisos en canales específicos.** Algunos canales tienen permisos sobrescritos que pueden bloquear comandos. Ve a `Configuración del canal > Permisos` y revisa que tu rol (y el de Kigo) tengan acceso.

**El bot está apagado.** Si Kigo está en estado "inactivo" en la lista de miembros, puede no responder. Pide al owner que lo reinicie o revisa si hay un apagado programado.

**Discord está fallando.** A veces Discord tiene incidencias generales. Revisa [discordstatus.com](https://discordstatus.com/).

**Estás en un DM.** Kigo no funciona en mensajes directos. Solo en servidores.

## Permisos no son retroactivos

Si Kigo tenía un permiso ayer y hoy se lo quitas, las acciones que ya ejecutó (como bans antiguos) se mantienen, pero no podrá ejecutar nuevas acciones hasta que le devuelvas el permiso.

## Siguiente paso

Si tu problema es de jerarquía de roles, pregunta en el [servidor de soporte](https://discord.gg/RRy8t5mfQe) con una captura de la lista de roles de tu servidor.
