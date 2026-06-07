# Banear a un usuario

Prohíbe a un usuario del servidor. La sanción más severa. Una vez baneado, no puede volver a entrar salvo que se le desbanée manualmente.

## Cuándo usarlo

- El usuario cometió una falta grave (acoso, spam masivo, contenido ilegal).
- El usuario es claramente un bot malicioso o multicuenta.
- El usuario es un raid conocido y quieres asegurarte de que no vuelva.

Para faltas menores, considera primero `/kick` (expulsar) o `/mute` (silenciar).

## Requisitos

- Tu rol debe tener permiso de **Banear miembros**.
- Kigo debe tener permiso de **Banear miembros** en el servidor.
- El usuario a banear debe ser miembro actual del servidor.

## Cómo usarlo

1. Escribe `/ban`.
2. Selecciona el usuario de la lista.
3. (Opcional) Escribe una razón.
4. Pulsa Enter.

Kigo ejecuta el ban, te responde con un mensaje efímero confirmando, y registra la acción en el canal de logs.

## La razón

La razón es opcional pero recomendada. Se guarda en los logs de auditoría de Discord (visibles para admins) y en el canal de logs de Kigo. Útil para:

- Que el resto del staff sepa por qué se baneó.
- Si el usuario apela el ban, tener un motivo escrito.
- Llevar un registro histórico de por qué cada usuario está baneado.

Si no escribes razón, Kigo usa "No se especificó" automáticamente.

## Limitaciones de jerarquía

No puedes banear a alguien con un rol **más alto** que el tuyo en la jerarquía de Discord. Por ejemplo, si tienes el rol "Moderador" (posición 3) y el usuario tiene el rol "Admin" (posición 5), no puedes banearlo.

Excepción: si eres el **owner del servidor**, sí puedes banear a cualquiera.

## DM al baneado

Kigo **no envía DM** automático al usuario baneado. Si quieres comunicarle el motivo, escríbele por DM manualmente antes de ejecutar el comando.

## Desbanear

Para desbanear a alguien:

1. Ve a `Configuración del servidor > Banidos`
2. Busca al usuario
3. Click en "Quitar ban"

O usa el comando `/unban` con la ID del usuario (si la tienes apuntada).

## Apelación de bans

Kigo no tiene un sistema de apelación integrado. Si un usuario quiere apelar su ban, debe contactar con el staff del servidor por fuera de Discord (por ejemplo, en una página web o un correo de contacto).

## Lo que NO hace

- **No pide confirmación.** El ban es inmediato al ejecutar el comando. Revisa bien el usuario y la razón antes de pulsar Enter.
- **No borra los mensajes** que el usuario envió antes del ban. Para eso, ejecuta `/clear` después.
- **No notifica al usuario.** Si quieres que sepa por qué, escríbele por DM.
- **No afecta a otras cuentas** del mismo usuario. Si tiene multicuentas, tienes que baneear cada una por separado.
- **No es permanente si desactivas Kigo.** Si quitas a Kigo del servidor, los bans se mantienen. Pero si quieres revertir todos los bans, tendrías que hacerlo manualmente.

## Problemas frecuentes

**"No puedo banear a [usuario con rol alto]"** — Discord no te deja por jerarquía. Solo el owner del servidor puede saltarse esa limitación. Más detalles: [No puedo usar este comando](../problemas/no-puedo-usar-comando.md).

**"El usuario no aparece en la lista"** — Solo puedes banear a miembros actuales del servidor. Si el usuario ya se fue, no aparecerá.

**"Kigo dice que no tiene permisos"** — Kigo necesita el permiso "Banear miembros" en su rol. Revisa `Configuración del servidor > Roles > Kigo > Permisos`.

## Siguiente paso

[Aprende a expulsar →](expulsar.md), una opción menos severa que el ban.
