# Ver warns de un usuario (`/warns`)

Muestra todos los warns activos de un usuario en el servidor. Los warns se cuentan sobre la ventana de 30 días por defecto (configurable en `/configuración` → **Warns**).

## Requisitos

- Tu rol debe tener permiso de **Moderar miembros**.

## Cómo usarlo

1. Escribe `/warns`.
2. Selecciona el **usuario**.
3. Pulsa Enter.

Kigo te responde con un embed efímero con el historial.

## Qué muestra

Para cada warn activo:

- **ID del caso** (`#N`).
- **Severidad** entre corchetes.
- **Razón** (recortada si es muy larga).
- **Fecha de expiración** (formato DD/MM/YYYY).

Al final, un resumen con:

- Total de warns activos.
- Suma de severidades (lo que mira el Castigo Progresivo).

## Diferencia con `/case` y `/modlogs`

- **`/warns usuario`**: solo warns activos (no expirados) de un usuario.
- **`/modlogs [usuario]`**: historial completo de cualquier caso (warn, mute, kick, ban, unwarn, etc.) del servidor o de un usuario.
- **`/case id`**: detalle de un caso concreto.

## Si el usuario no tiene warns activos

Kigo responde con un embed verde indicando que el usuario está "limpio".

## Lo que NO hace

- **No muestra warns expirados** (siguen en `/modlogs` y `/case`).
- **No muestra warns de otros servidores.**

## Siguiente paso

[Revoca un warn con `/unwarn` →](unwarn.md) o [consulta el historial completo con `/modlogs` →](modlogs.md).
