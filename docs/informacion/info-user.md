# Comando `/info-user`

Muestra información de un usuario en relación con Kigo: si tiene premium activo y si es staff de Kigo.

## Cómo usarlo

1. Escribe `/info-user`.
2. (Opcional) Selecciona un **usuario**. Si no seleccionas ninguno, Kigo muestra tu propia información.
3. Pulsa Enter.

Kigo te responde con un embed efímero.

## Qué muestra

- **¿Es un usuario premium?** — Sí/No, con la fecha de expiración si tiene premium activo.
- **¿Es un staff de mi soporte?** — Sí/No, con el rango concreto (definido en el `staff.json` interno) si lo es.

## Requisitos

- Cualquier miembro del servidor puede usar `/info-user`. No requiere permisos especiales.

## Lo que NO hace

- **No muestra el historial de moderación.** Para eso, usa `/modlogs` o `/case`.
- **No muestra warns activos.** Para eso, usa `/warns`.
- **No muestra información personal del usuario** (email, IP, etc.) — Kigo no tiene acceso a esos datos.

## Siguiente paso

[Vuelve al índice de información →](index.md) o al [inicio](../index.md).
