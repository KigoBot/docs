# Mostrar un canal (`/show`)

Revierte la ocultación de un canal: restaura el permiso de "Ver canal" para `@everyone` a su estado por defecto.

## Requisitos

- Tu rol debe tener permiso de **Gestionar canales**.
- Kigo debe tener permiso de **Gestionar canales** en el servidor.

## Cómo usarlo

1. Ve al canal que quieres mostrar.
2. Escribe `/show`.
3. Pulsa Enter.

Kigo restaura el permiso de "Ver canal" para `@everyone`. Te responde con un mensaje efímero confirmando.

## Cuándo usarlo

- Después de [`/hide`](hide.md), cuando quieres volver a hacer público el canal.
- Cuando has ajustado manualmente los permisos y quieres "resetear" el acceso de `@everyone`.

## Lo que hace exactamente

`/show` pone el permiso de "Ver canal" para `@everyone` en `null` (sin override), lo que significa que se aplican los permisos por defecto del rol. Si tu servidor tenía `@everyone` con "Ver canal" activado por defecto, el canal vuelve a ser visible.

## Lo que NO hace

- **No elimina otros permission overwrites** que puedas tener configurados (roles con permisos personalizados, etc.). Solo afecta al override de `@everyone`.
- **No desoculta canales** que no hayas ocultado con `/hide` o manualmente con un override.

## Siguiente paso

[Vuelve al índice de moderación →](index.md).
