# Moderación

Comandos del día a día para mantener el orden. Todos están disponibles en cualquier canal donde tengas permiso.

## Quién puede usar cada comando

Discord usa su propio sistema de permisos. Para usar los comandos de moderación necesitas:

- **Tu rol** debe tener el permiso correspondiente (por ejemplo, "Banear miembros" para usar `/ban`).
- **Kigo** debe tener el mismo permiso en el canal donde se ejecuta.

Si no puedes usar un comando, Discord te mostrará un mensaje como "esta aplicación no tiene permiso para usar este comando en este servidor". Más detalles en [problemas frecuentes](../problemas/no-puedo-usar-comando.md).

## Los comandos

<div class="grid cards" markdown>

-   :material-gavel: **[Banear](banear.md)**

    ---

    Prohíbe a un usuario del servidor. Acción severa, queda registro en auditoría.

-   :material-account-remove: **[Expulsar](expulsar.md)**

    ---

    Echa a un usuario, pero puede volver con una nueva invitación.

-   :material-volume-off: **[Silenciar](silenciar.md)**

    ---

    Impide que un usuario escriba en todos los canales durante un tiempo.

-   :material-broom: **[Borrar mensajes](borrar-mensajes.md)**

    ---

    Elimina varios mensajes de un canal de una sola vez.

-   :material-lock: **[Bloquear canal](bloquear-canal.md)**

    ---

    Impide que los miembros normales escriban en un canal.

-   :material-timer-sand: **[Modo lento](slowmode.md)**

    ---

    Obliga a esperar X segundos entre mensajes en un canal.

</div>

## Lo que comparten todos

- **Respuesta efímera**: Kigo responde solo a ti (los demás no ven el mensaje de "baneado con éxito").
- **Registro en logs**: cada acción se anota en el canal de logs configurado.
- **Verificación de jerarquía**: no puedes banear a alguien con un rol más alto que el tuyo, ni a alguien con permisos de Administrador (a menos que seas el owner del servidor).
- **Razón opcional**: la mayoría admite una razón que se guarda en los logs de auditoría de Discord.

## Siguiente paso

[Aprende a banear →](banear.md), el más común de los comandos de moderación.
