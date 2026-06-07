# Reiniciar un canal (`/nuke`)

Clona el canal actual y borra el original. El canal clonado queda con el mismo nombre, posición, permisos y tema, pero **sin ningún mensaje anterior**. Es la forma más rápida de "empezar de cero" sin perder la configuración del canal.

## Cuándo usarlo

- Un canal tiene un tema polémico enquistado y quieres "barrer" la historia sin perder el canal.
- Se filtró información sensible (links, claves, datos privados) y necesitas borrar todos los mensajes de golpe.
- Tras un raid que dejó el canal inutilizable.

## Requisitos

- Tu rol debe tener permiso de **Gestionar canales**.
- Kigo debe tener permiso de **Gestionar canales** en el servidor.

## Cómo usarlo

1. Ve al canal que quieres reiniciar.
2. Escribe `/nuke`.
3. Pulsa Enter.

Kigo clona el canal, borra el original y envía un mensaje de confirmación en el canal nuevo: "Canal reiniciado por {usuario}".

## Cómo funciona internamente

1. Discord clona el canal con todos sus permisos, tema, posición, etc.
2. Discord borra el canal original (lo que también borra todos los mensajes).
3. Kigo envía un mensaje breve en el canal nuevo.

El resultado: el canal sigue existiendo, con el mismo nombre, pero está vacío.

## Diferencia con `/clear`

- **`/clear`**: borra hasta 100 mensajes del canal, los más recientes. El canal y los permisos siguen iguales.
- **`/nuke`**: borra **todos** los mensajes del canal (sin límite de antigüedad), pero conserva el nombre, posición y permisos. Implica un cambio de ID del canal: los enlaces antiguos al canal dejarán de funcionar.

## Lo que NO hace

- **No borra los permisos personalizados.** El canal nuevo los hereda todos.
- **No conserva webhooks.** Tendrás que recrearlos.
- **No conserva hilos.** Los hilos del canal original no se migran al clon.
- **No conserva anclados.** Los mensajes anclados del original no aparecen en el clon.

## Problemas frecuentes

**"Los enlaces al canal antiguo ya no funcionan"** — Es normal. El canal nuevo tiene un ID nuevo. Actualiza los enlaces en pins, documentación, etc.

**"Los hilos se han perdido"** — Correcto, `/nuke` no migra hilos. Si los necesitas, pídele a los usuarios que abran hilos nuevos en el canal clonado.

**"Kigo dice que no tiene permisos"** — Kigo necesita "Gestionar canales" en su rol. Revísalo.

## Siguiente paso

[Vuelve al índice de moderación →](index.md).
