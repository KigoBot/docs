# Limpieza tras un raid

A veces el anti-raid detecta el raid demasiado tarde, o Kigo no estaba configurado cuando ocurrió. En esos casos, el servidor queda lleno de canales y roles duplicados. El comando `/eliminar-raid` los limpia de un golpe.

## Cuándo usarlo

- Acabas de sufrir un raid y el servidor tiene 30 canales con nombres como "raid1", "raid2", "raid3"...
- Alguien creó 15 roles con nombres aleatorios para ocultar cuentas maliciosas.
- El raid fue "lento" (duró horas) y el anti-raid no lo detectó por estar bajo el umbral.
- Quieres hacer una limpieza masiva de canales de spam antiguos.

## Cómo funciona

1. Escribe `/eliminar-raid`.
2. Kigo te preguntará: ¿limpiar canales o roles?
3. Kigo escanea el servidor y agrupa los elementos por nombre.
4. Si hay 3 o más canales/roles con el mismo nombre (o nombres muy parecidos), los marca como duplicados.
5. Te muestra una lista con cuántos encontró.
6. Te pide confirmación con dos botones: **Eliminar** y **Cancelar**.
7. Si confirmas, Kigo borra los duplicados con un pequeño delay entre cada uno (3 segundos) para no saturar la API de Discord.

## Qué considera "duplicado"

Kigo usa una heurística, no una comparación exacta. Dos canales se consideran duplicados si:

- Tienen el **mismo nombre** (ignorando mayúsculas y espacios), o
- Sus nombres son **muy similares** (por ejemplo, "raid-1" y "raid-2" se consideran parte del mismo grupo).
- Hay al menos 3 en el mismo grupo.

Si solo tienes 2 canales con el mismo nombre, Kigo no los tocará. El umbral mínimo es 3.

## Qué NO considera duplicado

- Canales con el mismo nombre en **categorías distintas** (por ejemplo, un "general" en info y otro en moderación). Discord los trata como canales diferentes.
- Roles con el mismo nombre si tienen **distintos permisos** o están asignados a distintos usuarios.
- Canales con **contenido activo** (mensajes en los últimos 7 días). Kigo no borrará canales que estén en uso.

## Confirmación

El comando siempre pide confirmación antes de borrar nada. Los botones son:

- **Eliminar** (rojo): procede con el borrado.
- **Cancelar** (gris): no hace nada.

Tienes 8 minutos para decidir. Si no haces clic en ninguno, el comando expira y no se borra nada.

Esto es para evitar que un clic accidental borre 50 canales de un golpe.

## Quién puede usarlo

Solo el **owner del servidor** (o el owner del bot) puede ejecutar `/eliminar-raid`. No es un comando para moderadores, precisamente porque es destructivo.

## Después de la limpieza

Una vez Kigo termina, te muestra un resumen con:

- Cuántos canales/roles eliminó.
- Cuántos quedaron sin tocar (por no ser duplicados).
- Si quedó alguno en el limbo (por ejemplo, sin categoría padre).

Los canales/roles eliminados quedan en los logs de auditoría de Discord durante 90 días, así que si te arrepientes, un admin puede recuperarlos manualmente.

## Lo que NO hace

- **No recupera el contenido** de los canales borrados. Mensajes, archivos, hilos: todo se va con el canal.
- **No banea a los usuarios** que crearon los duplicados. Para eso, mira los logs de auditoría y banealos manualmente (o configura mejor el anti-raid para la próxima).
- **No borra categorías vacías.** Si después de eliminar los canales queda una categoría sin canales, Kigo no la borra.

## Siguiente paso

[Aprende cómo configurar el canal de logs →](logs.md) para que este tipo de eventos queden registrados y puedas auditarlos después.
