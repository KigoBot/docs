# Ver el historial de moderación (`/modlogs`)

Lista los últimos casos de moderación del servidor, o de un usuario concreto. Es el "registro" del servidor.

## Requisitos

- Cualquier miembro del servidor puede usar `/modlogs`. No requiere permisos especiales.

## Cómo usarlo

1. Escribe `/modlogs`.
2. (Opcional) Selecciona un **usuario** si quieres filtrar.
3. Pulsa Enter.

Kigo te responde con un embed efímero con el resumen y los últimos 15 casos.

## Qué muestra

- **Total de casos** del servidor.
- **Conteo por tipo**: Warns, Mutes, Kicks, Bans.
- **Lista** de los últimos 15 casos con formato `TIPO · #ID · @usuario · razón (recortada) · fecha`.

Si filtras por usuario, el título cambia a "Modlogs de {usuario}".

## Diferencia con `/warns` y `/case`

- **`/modlogs`**: vista de los últimos 15 casos, sirve para auditoría rápida. Mezcla todos los tipos.
- **`/warns usuario`**: solo warns activos (no expirados) de un usuario.
- **`/case id`**: detalle completo de un caso concreto.

## Si no hay casos

Kigo responde con un embed indicando "Sin casos registrados".

## Siguiente paso

[Detalle de un caso con `/case` →](case.md) o [vuelve al índice de moderación →](index.md).
