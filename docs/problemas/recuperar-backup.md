# Recuperar la configuración

Kigo guarda la configuración de tu servidor en su base de datos. Si por cualquier motivo pierdes la configuración (reinstalación manual, etc.), puedes recuperarla desde un **backup firmado** que hayas exportado previamente.

## Backup manual con `/configuración`

La forma directa. Kigo te genera un archivo JSON firmado que puedes guardar donde quieras.

### Exportar

1. Escribe `/configuración`.
2. Ve a la sección **Backups**.
3. Pulsa **Exportar backup**.
4. Elige qué secciones incluir (anti-raid, automod, verificación, lista blanca, etc.).
5. Kigo te muestra el archivo `.json` en una respuesta efímera (solo tú lo ves) y te lo envía también por mensaje directo como archivo adjunto.

El archivo está firmado criptográficamente. Si alguien lo modifica, Kigo lo detectará al intentar importarlo y rechazará el archivo.

### Importar

1. Escribe `/configuración`.
2. Ve a la sección **Backups**.
3. Pulsa **Importar backup**.
4. Sube el archivo `.json` que tienes.
5. Kigo valida la firma.
6. Si es válida, te muestra qué secciones se pueden restaurar.
7. Elige cuáles quieres importar.
8. Confirma.

La importación sobrescribe la configuración actual. Si quieres mantener una copia, exporta antes de importar.

## No hay backups automáticos

Kigo **no hace backups automáticos** de la configuración de tu servidor. Si pierdes el servidor en la base de datos, la única forma de recuperarlo es con un backup que hayas exportado tú manualmente.

Recomendación: exporta un backup cada vez que cambies algo importante en la configuración. Guárdalo en un sitio seguro (Drive, Dropbox, tu email, etc.).

## Si Kigo se cayó y se reinstaló

Si el bot se cayó y se reinstaló (por ejemplo, un cambio de infraestructura), la configuración debería seguir ahí, porque se guarda en una base de datos persistente. Si por algún motivo la configuración se perdió, puedes:

1. Usar el último backup manual que tengas.
2. Reconfigurar desde cero con `/setup` (toma 5 minutos si sabes lo que quieres).

## Si cambias de owner

La configuración está vinculada al **ID del servidor**, no al owner. Cambiar de owner no afecta a nada. El nuevo owner tendrá acceso automáticamente.

Más detalles: [Cambiar de owner del servidor](migrar-servidor.md).

## Qué incluye el backup

Un backup completo incluye:

- Configuración de anti-raid (niveles, límites, canales excluidos).
- Configuración de automod (reglas activas, límite de spam, allowList de webs).
- Configuración de verificación (rol, canal, estado).
- Lista blanca (usuarios, roles, canales exentos).
- Configuración de canales de logs.
- Reglas de escalación de warns (si tienes premium).
- Plantilla de DM de warns (si la has personalizado).

## Qué NO incluye

- **Mensajes del canal de logs.** Esos están en Discord, no en Kigo.
- **Baneos.** Los baneos se gestionan desde Discord, no desde Kigo.
- **Cuentas premium.** El premium está vinculado al usuario que lo activó, no se transfiere por backup.
- **Historial de moderación.** Las acciones pasadas no se guardan en el backup. (Puedes ver el historial con `/modlogs` o `/case` mientras el bot siga conectado a la base de datos.)

## Seguridad de los backups

Los backups están **firmados criptográficamente**. Esto significa:

- Kigo puede detectar si alguien modificó el archivo.
- Si modificas el archivo a mano, Kigo rechazará la importación.
- El "secreto" de firmado está en el servidor de Kigo, no en el archivo. No puedes crear backups válidos por tu cuenta.

Mantén los backups en un lugar seguro. Si alguien los obtiene, podría restaurar la configuración de tu servidor (pero necesitaría ser owner o admin para ejecutar el comando de importación).

## Siguiente paso

Si tu problema es que perdiste la configuración tras algún evento, contacta con el [servidor de soporte](https://discord.gg/RRy8t5mfQe) con el ID del servidor y la fecha del evento.
