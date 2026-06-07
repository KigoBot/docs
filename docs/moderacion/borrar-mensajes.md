# Borrar mensajes de un canal

Elimina varios mensajes de una sola vez del canal donde se ejecuta el comando. Útil cuando alguien spammea o quieres limpiar un canal.

## Cuándo usarlo

- Alguien hizo flood en un canal y quieres borrar sus mensajes.
- Se filtró información privada por error y quieres borrarla antes de que más gente la vea.
- Estás reorganizando un canal y quieres borrar mensajes antiguos para empezar limpio.

## Requisitos

- Tu rol debe tener permiso de **Gestionar mensajes**.
- Kigo debe tener permiso de **Gestionar mensajes** y **Leer historial de mensajes** en el canal.

## Cómo usarlo

1. Ve al canal donde quieres borrar mensajes.
2. Escribe `/clear`.
3. Escribe la cantidad de mensajes a borrar (entre 1 y 100).
4. Pulsa Enter.

Kigo borra los N mensajes más recientes del canal (incluyendo el propio mensaje de invocación) y te responde con un mensaje efímero confirmando cuántos borró.

## Limitaciones

**Máximo 100 mensajes por comando.** Discord no permite borrar más de 100 mensajes en una sola llamada a la API. Si necesitas borrar más, ejecuta el comando varias veces.

**Mensajes con más de 14 días.** Discord no permite borrar mensajes con más de 2 semanas de antigüedad (limitación de la API). Kigo pasa el parámetro `bulkDelete: true`, que automáticamente excluye los mensajes de más de 14 días. Si todos los mensajes seleccionados son de más de 14 días, Kigo no borrará ninguno.

**Solo en el canal actual.** El comando solo borra del canal donde se ejecuta. Si quieres borrar de varios canales, ejecuta el comando en cada uno.

## Qué ve el resto del servidor

El borrado es público: si un mensaje está visible, desaparece. Los demás usuarios ven los mensajes desaparecer en tiempo real (si tienen Discord abierto).

Discord también muestra un "X mensajes fueron borrados" en el log de auditoría del canal, pero no de forma visible para los usuarios.

## Caso de uso típico: limpiar spam

1. Un usuario envía 30 mensajes de spam.
2. Escribes `/clear 35` (un poco más por si acaso).
3. Los 30 mensajes del usuario + 5 anteriores desaparecen.
4. El canal queda limpio.

Si el usuario sigue escribiendo, primero siléncialo con `/mute` y luego limpia.

## Lo que NO hace

- **No borra mensajes de otros canales.** Solo del actual.
- **No borra mensajes de más de 14 días.**
- **No permite filtrar** por autor. Para eso, ejecuta el comando varias veces o usa un bot externo.
- **No pide confirmación.** El borrado es inmediato. Ten cuidado con la cantidad.

## Cuidado

`/clear` es uno de los comandos más peligrosos de moderación. Una cantidad mal puesta puede borrar 100 mensajes importantes de un canal activo. Revisa siempre el número antes de ejecutar.

Kigo **no muestra botón de confirmación**: el borrado es inmediato al ejecutar el comando. Si quieres "empezar de cero" con un canal entero, considera `/nuke` en su lugar (que también es destructivo, pero respeta mejor la configuración del canal).

## Problemas frecuentes

**"Kigo dice que no tiene permisos"** — El rol de Kigo necesita "Gestionar mensajes" y "Leer historial de mensajes" en el canal específico.

**"Algunos mensajes no se borraron"** — Probablemente son de hace más de 14 días. Discord no lo permite.

**"Borró 0 mensajes"** — El canal estaba vacío o todos los mensajes eran de hace más de 14 días.

## Siguiente paso

[Aprende a bloquear un canal →](bloquear-canal.md), útil cuando necesitas que un canal se calme de golpe.
