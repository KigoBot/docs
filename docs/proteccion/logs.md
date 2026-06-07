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
- `Prevenir Bots` — baneo automático de bots no permitidos al entrar al servidor.
- `Multicuentas` — expulsión automática de cuentas con menos días de los configurados.
- `Ban Masivo` — detección de baneos masivos por parte de un usuario.
- `Expulsión Masiva` — detección de expulsiones masivas.
- `Actualizar Servidor` — cambios sospechosos al servidor (nombre, icono, verificación, etc.).

### Auto Moderación

- `Prevenir Flood` — sanción por spam/flood. El embed incluye el mensaje que disparó el filtro (recortado).
- `Menciones Fantasma` — sanción por ghost ping (mensaje que menciona y luego se borra).
- `Filtro Evasivo` (premium T2+) — detección de homoglyphs, base64 ofuscado, etc. Emite un auto-warn.

### Sistema

- Kigo entrando/saliendo del servidor.
- Errores internos (raros, pero pasan).

![Acción del anti-raid en logs](images/antiraid-accion.png) — _pendiente de captura real_

## Lo que NO se registra en este canal

- **Comandos de moderación manuales** (`/ban`, `/kick`, `/mute`, `/warn`, etc.): estas acciones crean un **caso** (registro numerado por servidor) accesible con `/case` y `/modlogs`, pero no se publican automáticamente en el canal de logs.
- **Verificación exitosa**: solo se registra en logs si el usuario falla o expulsa. Los aciertos no aparecen.
- **Cambios de configuración** (para eso, usa los backups firmados).

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
