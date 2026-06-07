# Limpieza tras un raid

A veces el anti-raid detecta el raid demasiado tarde, o Kigo no estaba configurado cuando ocurrió. En esos casos, el servidor queda lleno de canales y roles duplicados. El comando `/eliminar-raid` los limpia de un golpe.

## Cuándo usarlo

- Acabas de sufrir un raid y el servidor tiene 30 canales con nombres como "raid1", "raid2", "raid3"...
- Alguien creó 15 roles con nombres aleatorios para ocultar cuentas maliciosas.
- El raid fue "lento" (duró horas) y el anti-raid no lo detectó por estar bajo el umbral.
- Quieres hacer una limpieza masiva de canales de spam antiguos.

## Cómo funciona

1. Escribe `/eliminar-raid tipo:canales` o `/eliminar-raid tipo:roles`.
2. Kigo escanea el servidor y cuenta cuántas veces se repite cada nombre.
3. Si hay 3 o más canales/roles con el **mismo nombre exacto**, los marca como duplicados.
4. Te muestra un mensaje con cuántos encontró.
5. Te pide confirmación con dos botones: **Eliminar** y **Cancelar**.
6. Si confirmas, Kigo borra los duplicados con un pequeño delay entre cada uno (3 segundos) para no saturar la API de Discord.

## Qué considera "duplicado"

Kigo usa una comparación **exacta** de nombre, no heurística. Dos canales se consideran duplicados si:

- Tienen el **mismo nombre** (sin importar mayúsculas/minúsculas, Discord ya los trata como case-insensitive en nombres).
- Hay **al menos 3** canales con ese mismo nombre en el servidor.

Si solo tienes 2 canales con el mismo nombre, Kigo no los tocará. El umbral mínimo es 3.

## Qué NO considera duplicado

- Canales con nombres **parecidos pero distintos** (por ejemplo, "raid-1" y "raid-2" se tratan como diferentes, no como variantes del mismo nombre).
- Roles gestionados por integraciones o bots (`managed: true`) ni el rol `@everyone` del servidor.
- Hilos (`threads`): Kigo no los tiene en cuenta al escanear canales.

## Confirmación

El comando siempre pide confirmación antes de borrar nada. Los botones son:

- **Eliminar** (rojo): procede con el borrado.
- **Cancelar** (gris): no hace nada.

Tienes **8 minutos** (480 000 ms) para decidir. Si no haces clic en ninguno, el comando expira y no se borra nada.

Esto es para evitar que un clic accidental borre 50 canales de un golpe.

## Quién puede usarlo

Solo el **owner del servidor** (o el owner del bot) puede ejecutar `/eliminar-raid`. No es un comando para moderadores, precisamente porque es destructivo.

## Después de la limpieza

Una vez Kigo termina, te muestra un mensaje efímero con cuántos canales/roles eliminó.

Los canales/roles eliminados quedan en los logs de auditoría de Discord durante 90 días, así que si te arrepientes, un admin puede recuperarlos manualmente.

## Lo que NO hace

- **No recupera el contenido** de los canales borrados. Mensajes, archivos, hilos: todo se va con el canal.
- **No banea a los usuarios** que crearon los duplicados. Para eso, mira los logs de auditoría y banealos manualmente (o configura mejor el anti-raid para la próxima).
- **No borra categorías vacías.** Si después de eliminar los canales queda una categoría sin canales, Kigo no la borra.
- **No detecta canales con contenido activo.** Kigo borrará cualquier duplicado, incluso si tiene mensajes recientes.

## Siguiente paso

[Aprende cómo configurar el canal de logs →](logs.md) para que este tipo de eventos queden registrados y puedas auditarlos después.
