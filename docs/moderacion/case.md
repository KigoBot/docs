# Ver el detalle de un caso (`/case`)

Cada acción de moderación manual (warn, mute, kick, ban, unban, unmute, unwarn) crea un caso con un ID numérico único por servidor. `/case` te muestra el detalle completo.

## Requisitos

- Cualquier miembro del servidor puede usar `/case`. No requiere permisos especiales.

## Cómo usarlo

1. Escribe `/case`.
2. Escribe el **ID del caso** (un número, p. ej. `42`).
3. Pulsa Enter.

Kigo te responde con un embed efímero con el detalle del caso.

## Qué muestra

- **Acción** (Advertencia, Silencio, Expulsión, Ban, etc.).
- **Usuario** sancionado.
- **Moderador** que aplicó la acción.
- **Razón**.
- **Severidad** (si aplica).
- **Contexto** (URL de evidencia, si se proporcionó al aplicar el warn).
- **Fecha de expiración** (si aplica, con marca `expirado` si ya pasó).
- **Fecha** de creación.
- **Notas**: si otros mods han añadido notas al caso.

## De dónde sale el ID

Cada vez que se aplica una acción de moderación manual, Kigo asigna un nuevo ID incremental dentro del servidor. Por ejemplo, el primer caso de tu servidor es el `#1`, el siguiente el `#2`, etc.

## Lo que NO hace

- **No edita casos.** Los casos son inmutables. Si te equivocas, aplica la acción contraria (`/unban` para un ban, `/unwarn` para un warn) y Kigo registrará un nuevo caso.

## Siguiente paso

[Consulta el historial completo con `/modlogs` →](modlogs.md) o [vuelve al índice de moderación →](index.md).
