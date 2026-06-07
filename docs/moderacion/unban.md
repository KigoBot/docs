# Desbanear a un usuario (`/unban`)

Quita la prohibición a un usuario identificado por su **ID de Discord**. La acción crea un caso de tipo `unban` en el historial del servidor.

## Requisitos

- Tu rol debe tener permiso de **Banear miembros**.
- Kigo debe tener permiso de **Banear miembros** en el servidor.
- Necesitas la **ID de Discord** del usuario a desbanear (no vale con el nombre).

## Cómo usarlo

1. Escribe `/unban`.
2. Escribe la **ID del usuario** (p. ej. `123456789012345678`).
3. Pulsa Enter.

Kigo comprueba que ese ID está en la lista de baneados, lo desbannea, y te responde con un mensaje efímero confirmando.

## Cómo conseguir la ID de un usuario baneado

Las IDs de Discord no cambian nunca. Si la apuntaste cuando lo baneaste (o si la tienes de un log anterior), úsala directamente.

Si no la tienes:

1. Ve a `Configuración del servidor > Banidos`.
2. Busca al usuario en la lista (puedes buscar por nombre si Kigo tenía su tag guardado).
3. Click derecho en su entrada → `Copiar ID de usuario`.

Otra opción: revisa los casos de ban en `/modlogs` — la ID del usuario aparece en cada línea.

## Limitaciones

- **No se puede desbanear por nombre.** La ID es obligatoria.
- **No se puede desbanear a un usuario que sigue baneado de Discord** (lo que pasa en cuentas baneadas de plataforma).

## Lo que NO hace

- **No re-envía una invitación** al usuario. Si quieres que vuelva, pásale tú el enlace.
- **No borra los casos de ban anteriores.** Quedan en `/modlogs` para auditoría.
- **No desbannea a un usuario que ya no está baneado.** Kigo avisa y termina.

## Problemas frecuentes

**"Ese usuario no está prohibido"** — La ID no está en la lista de baneados del servidor. Revisa que sea la ID correcta.

**"Kigo dice que no tiene permisos"** — Kigo necesita el permiso "Banear miembros" en su rol.

## Siguiente paso

[Vuelve al índice de moderación →](index.md).
