# Canal de logs

Kigo necesita un canal donde dejar constancia de todo lo que hace. Se recomienda crear uno llamado `#kigo-logs` y darle permisos de lectura solo a tu staff.

## Por qué es importante

El canal de logs es tu "caja negra". Si algo sale mal (o si quieres saber qué hizo Kigo en las últimas 24 horas), lo miras ahí.

Sin logs:

- Si Kigo banea a alguien, no sabes por qué.
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
4. Ejecuta `/configuración` y dile a Kigo que use ese canal.

Kigo también puede crearlo automáticamente con un botón en `/configuración` → **Logs** → **Crear canal de logs**.

## Qué se registra

Kigo registra, en orden cronológico:

**Moderación manual**

- `usuario baneado por @staff` con razón
- `usuario expulsado por @staff`
- `usuario silenciado por @staff` con duración
- `mensajes borrados` con cantidad y autor
- `canal bloqueado/desbloqueado` por @staff

**Anti-raid**

- `raid detectado: creación masiva de canales` con detalles
- `multicuentas detectadas` con número de cuentas
- `cambios sospechosos al servidor revertidos`
- `baneos coordinados detectados` (esto es grave, aparece en rojo)

**Automod**

- `mensaje borrado por spam` con autor y canal
- `mensaje borrado por palabra bloqueada` con la palabra detectada
- `usuario silenciado por flood` con duración
- `ghost ping detectado` con autor y mencionado

**Verificación**

- `nuevo miembro: @usuario` cuando entra
- `verificación exitosa` con minutos tardados
- `verificación fallida` con código incorrecto
- `usuario expulsado por no verificar` con minutos transcurridos

**Sistema**

- Kigo entrando/saliendo del servidor
- Shards reiniciándose
- Errores internos (raros, pero pasan)

## Formato de cada entrada

Cada entrada en el log es un embed con:

- **Título** corto describiendo el evento.
- **Color** según severidad:
    - 🟢 Verde: normal, acción de moderación exitosa.
    - 🟡 Amarillo: advertencia, algo detectado pero no urgente.
    - 🔴 Rojo: crítico, raid o sanción fuerte.
- **Campos** con detalles: usuario, canal, razón, IDs, duración.
- **Footer** con timestamp y tipo de evento.

## Privacidad

El canal de logs es privado por defecto. Si lo dejas público por error, cualquiera podría ver qué moderadores banean a quién. Configúralo correctamente:

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

Kigo no borra nada del canal de logs. Lo que Kigo escribe ahí es responsabilidad tuya.

## Lo que NO se registra

- **Mensajes privados** entre usuarios (Kigo no los lee).
- **Comandos de moderación que no ejecutaron acción** (por ejemplo, `/ban` cuando el usuario no estaba en el servidor).
- **Cambios de configuración** (para eso, haz backup con `/configuración` → **Backups**).
- **Cosas que pasaron antes** de activar el canal de logs.

## Siguiente paso

Ahora que conoces los cuatro módulos de protección, vuelve a [la visión general de protección](index.md) o ve a [moderación](../moderacion/index.md) para los comandos del día a día.
