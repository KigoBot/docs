# Canal de logs

Kigo necesita un canal donde dejar constancia de todo lo que hace. Se recomienda crear uno llamado `#kigo-logs` y darle permisos de lectura solo a tu staff.

## Por qué es importante

El canal de logs es tu "caja negra". Si algo sale mal (o si quieres saber qué hizo Kigo en las últimas 24 horas), lo miras ahí.

Sin logs:

- Si Kigo banea a alguien automáticamente, no sabes por qué.
- Si el anti-raid se activa, no sabes qué detectó exactamente.
- Si hay un falso positivo, no puedes demostrarlo.

Con logs:

- Sabes exactamente qué pasó, cuándo y por qué.
- Puedes auditar la actividad de Kigo.
- Puedes revertir acciones manualmente si Kigo se equivocó.

## Cómo crear el canal

1. Ve a la categoría de tu servidor donde quieras el canal.
2. Crea un canal de texto llamado `kigo-logs` (o el nombre que prefieras).
3. Configura los permisos: que `@everyone` NO pueda verlo, que tu rol de staff SÍ.
4. Ejecuta `/configuración` y entra en la sección **Registros** para decirle a Kigo que use ese canal.

Kigo también puede crear el canal automáticamente con un botón en `/configuración` → **Registros** → **Crear canal**.

## Qué se registra

Kigo registra, en orden cronológico, los **eventos automáticos** del bot. Cada evento es un embed con un título corto y una descripción en formato de cita.

### Anti-raid

- `Canal(es) Creado(s)` (con log de auditoría y reversión si aplica).
- `Canal(es) Eliminado(s)`.
- `Canal(es) Actualizado(s)`.
- `Rol(es) Creado(s)`.
- `Rol(es) Eliminado(s)`.
- `Rol(es) Actualizado(s)`.
- `Webhook Creado` — detección de creación masiva de webhooks.
- `Prevenir Bots` — baneo automático de bots no permitidos al entrar al servidor.
- `Multicuentas` — expulsión automática de cuentas con menos días de los configurados.
- `Ban Masivo` — detección de baneos masivos por parte de un usuario.
- `Expulsión Masiva` — detección de expulsiones masivas.
- `Actualizar Servidor` — cambios sospechosos al servidor (nombre, icono, verificación, etc.).
- `Antievasión` — detección de usuarios que vuelven tras ser baneados/expulsados.
- `Lockdown Activado/Desactivado` — bloqueo de emergencia del servidor.

### Auto Moderación

- `Prevenir Flood` — sanción por spam/flood. El embed incluye el mensaje que disparó el filtro (recortado).
- `Menciones Fantasma` — sanción por ghost ping (mensaje que menciona y luego se borra).
- `Filtro Evasivo` (premium T2+) — detección de homoglyphs, base64 ofuscado, etc. Emite un auto-warn.

### Comandos de moderación manuales

Cada vez que un moderador ejecuta uno de estos comandos, Kigo lo refleja en el canal de logs. El embed incluye siempre el moderador, el usuario afectado, la razón y, cuando aplica, el número de caso.

- `Warn aplicado` (y `Castigo Progresivo activado` si el warn escala una sanción automática).
- `Unwarn` (individual) y `Unwarn (masivo)` (eliminar todos los warns de un usuario).
- `Ban aplicado` y `Unban`.
- `Kick aplicado`.
- `Mute aplicado` y `Unmute` (con duración y vencimiento en el mute).

### Invitaciones

- `Invitación creada` — código, canal, autor (sacado del audit log), caducidad formateada y usos máximos.
- `Invitación eliminada` — código y canal.

### Hilos

- `Hilo creado` — nombre, id, canal padre y autor (si está disponible).
- `Hilo actualizado` — cambios en nombre, archivado, bloqueado o auto-archivo.
- `Hilo eliminado` — nombre, id y canal padre.

### Bans

- `Ban removido` — quién fue desbaneado y quién lo hizo (audit log).

### Premium

- `Amenaza detectada` (premium T2+) — cuando un usuario alcanza un score de **40 o más** (Medio o superior) tras ejecutar `/amenazas @usuario`. El embed incluye el score, la etiqueta, las señales detectadas y quién ejecutó el comando.

### Verificación

- `Verificación exitosa` — cuando un usuario completa la verificación.
- `Verificación fallida` — código incorrecto o expirado.
- `Verificación expulsada` — expulsión automática por no verificar a tiempo.

### Configuración (auditoría)

- `Cambio de configuración` — cada vez que un administrador modifica un ajuste de Kigo, se registra en una tabla de auditoría interna accesible por el staff de Kigo. Incluye: qué cambió, quién lo hizo, valor anterior y valor nuevo.

### Sistema

- Kigo entrando/saliendo del servidor.
- Lockdown activado/desactivado (manual o automático).
- Errores internos (raros, pero pasan).

No hay un comando público para ver el historial de auditoría de configuración. Si necesitas consultarlo, abre un ticket en el [servidor de soporte](https://discord.gg/wmky5nBRR2).

## Formato de cada entrada

Cada entrada en el log es un embed con:

- **Título** corto describiendo el evento (ej. `:bust_in_silhouette: Multicuenta:`).
- **Descripción** en formato de cita (`> Campo: valor`) con el detalle: nombre e ID del usuario, sanción aplicada, ID del canal, etc.
- **Color** según el tipo de evento.

## Privacidad

El canal de logs es privado por defecto. Si lo dejas público por error, cualquiera podría ver qué cuentas han sido sancionadas. Configúralo correctamente:

1. Click derecho en el canal → `Editar canal`
2. Pestaña `Permisos`
3. Rol `@everyone` → `Ver canal` desactivado
4. Tu rol de staff → `Ver canal` activado
5. (Opcional) Rol `@admin` → `Ver canal` + `Historial de mensajes`

## Retención

Discord no tiene un sistema de "borrar logs antiguos". Si tu servidor tiene mucho tráfico, el canal de logs puede llenarse en meses. Recomendaciones:

- **Usa un bot de archivado** (como ArchiveBot) que mueva logs antiguos a otro canal.
- **Exporta los logs periódicamente** con un bot de backup.
- **Borra manualmente** entradas antiguas irrelevantes cada cierto tiempo.

Kigo no borra nada del canal de logs. Lo que Kigo escribe ahí es responsabilidad tuya. No hay una política automática de retención.

## Siguiente paso

Ahora que conoces los cuatro módulos de protección, vuelve a [la visión general de protección](index.md) o ve a [moderación](../moderacion/index.md) para los comandos del día a día.
