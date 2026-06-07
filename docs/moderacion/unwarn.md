# Revocar warns (`/unwarn`)

Quita un warn específico (por ID de caso) o todos los warns activos de un usuario. La acción también queda registrada como un caso de tipo `unwarn` para auditoría.

## Requisitos

- Tu rol debe tener permiso de **Moderar miembros**.

## Cómo usarlo

Tienes dos modos:

### Quitar un warn concreto

1. Escribe `/unwarn`.
2. Escribe el **ID del caso** (número, lo ves con `/warns` o `/case`).
3. (Opcional) Razón de la eliminación.
4. Pulsa Enter.

### Quitar todos los warns de un usuario

1. Escribe `/unwarn`.
2. Deja el campo `caso` vacío.
3. Selecciona el **usuario** (campo obligatorio en este modo).
4. (Opcional) Razón de la eliminación.
5. Pulsa Enter.

Kigo te responde con un embed efímero confirmando cuántos warns se eliminaron.

## Qué pasa al revocar

- El warn se marca como revocado y deja de contar para el Castigo Progresivo.
- **No se borra** de la base de datos: la revocación queda como un caso de tipo `unwarn` visible con `/case`.
- Si el usuario ya había sido sancionado automáticamente por Castigo Progresivo, esa sanción **no se revierte** automáticamente. Tienes que hacerlo a mano (`/unban`, `/unmute`).

## Lo que NO hace

- **No elimina el historial.** El caso `unwarn` se queda en `/modlogs` y `/case` para auditoría.
- **No revierte sanciones automáticas** (Castigo Progresivo). Si quieres revertirlas, hazlo manualmente.

## Problemas frecuentes

**"Caso no encontrado"** — El ID no corresponde a un warn de este servidor, o nunca existió. Comprueba con `/case <id>`.

**"Faltan datos"** — Si no indicas `caso`, tienes que indicar `usuario`, y viceversa.

## Siguiente paso

[Vuelve al índice de moderación →](index.md) o [consulta el historial completo con `/modlogs` →](modlogs.md).
