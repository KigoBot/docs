# Permisos que pide Kigo

Cuando añades Kigo a tu servidor, Discord te muestra una pantalla con un montón de palancas verdes activadas. Esta página explica qué hace cada una y por qué.

## Lectura rápida

- **Todos los permisos son necesarios** para las funciones que Kigo ofrece. Si desactivas uno, esa función no funcionará.
- **Kigo solo usa los permisos para lo que dice hacer.** No hay acciones ocultas.
- **Kigo es mantenido por su autor original.** Si quieres saber qué hace con cada permiso, la mejor forma es preguntar en el [servidor de soporte](https://discord.gg/RRy8t5mfQe) o revisar el comportamiento observable.

## Permisos uno por uno

### Administrador (Administrator)

El más fuerte. Le da a Kigo **todos** los permisos en todos los canales.

Kigo no lo necesita estrictamente, pero pedir permisos individuales en Discord requiere pedir también todos los que dependan de ellos, y la lista se vuelve absurda. Pedir Administrador es la forma estándar de evitar esto.

**¿Es arriesgado?** Sí, en el sentido de que si Kigo se volviera malicioso, podría hacer cualquier cosa. Kigo es mantenido por su autor: si detectas un comportamiento extraño, repórtalo en el [servidor de soporte](https://discord.gg/RRy8t5mfQe). La mayoría de bots medianos y grandes piden este permiso por la misma razón.

### Expulsar miembros y Banear miembros

Kigo los usa para:

- Banear cuentas sospechosas detectadas por el anti-raid
- Banear multicuentas (si lo configuras así)
- Ejecutar manualmente los comandos `/ban` y `/kick`
- Banear bots no verificados que intenten entrar

### Gestionar canales y Gestionar roles

Kigo los usa para:

- Detectar canales y roles creados en masa durante un raid
- Revertir la creación de canales/roles sospechosos
- Borrar canales duplicados con `/eliminar-raid`

### Gestionar mensajes y Leer historial de mensajes

Kigo los usa para:

- Borrar mensajes con spam, links acortados o palabras bloqueadas
- Borrar mensajes en masa con `/clear`
- Detectar "ghost pings" (cuando alguien menciona y borra el mensaje)

### Expulsar temporalmente (Moderar miembros)

Kigo lo usa para:

- Silenciar usuarios con `/mute` y `/unmute`
- Aplicar sanciones automáticas por spam
- Aplicar sanciones por "ghost pings"

### Gestionar apodos

Kigo lo usa para:

- Cambiar el apodo de usuarios baneados para dejar constancia pública (opcional)

### Ver los registros de auditoría

Kigo los usa para:

- Saber **quién** creó un canal/rol/baneo sospechoso (para detectar al atacante)
- Diferenciar entre un admin legítimo y alguien que acaba de tomar el control

### Enviar mensajes, Insertar enlaces, Leer mensajes, Historial de mensajes

Básicos. Sin ellos, Kigo no podría responder a tus comandos, mandarte el aviso de bienvenida por DM, ni leer los mensajes que tiene que moderar.

### Usar comandos de barra (slash)

Necesario para que los comandos como `/setup`, `/configuración`, `/ban` aparezcan en la interfaz de Discord.

### Mencionar @everyone, @here y todos los roles

Kigo lo usa para:

- Mencionarte en alertas críticas si un shard (subproceso del bot) se cae
- Mostrar menciones en los logs de moderación si lo configuras

## Lo que Kigo NO hace con estos permisos

- **No lee mensajes privados** entre usuarios. Solo lee mensajes en los servidores donde está añadido.
- **No escucha audio** en canales de voz.
- **No accede a tu cuenta** de Discord. Es un bot, no un OAuth de usuario.
- **No vende datos.** No hay analítica, no hay tracking. Kigo ni siquiera sabe quién eres.

## Cómo reducir permisos (avanzado)

Si aun así quieres quitar el permiso de Administrador y conceder solo los individuales, Discord lo permite. Al añadir el bot, desmarca "Administrador" en la pantalla de permisos y marca solo los que quieras. **Advertencia**: muchas funciones no funcionarán.

Por ejemplo, si quitas "Gestionar canales", `/eliminar-raid` y la protección contra raids que clonan canales no funcionarán.

## Siguiente paso

Ya tienes Kigo en tu servidor y entiendes qué permisos tiene. Ahora aprende qué hace cada función de protección en [la página siguiente](../proteccion/index.md).
