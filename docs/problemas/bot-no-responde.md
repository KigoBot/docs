# El bot no responde

Si Kigo no responde a tus comandos, hay una secuencia de cosas a revisar en orden.

## Comprobación 1: ¿Kigo está en el servidor?

A veces Kigo se ha caído, lo han echado, o está experimentando una incidencia. Verifica:

1. Ve a la lista de miembros del servidor.
2. Busca "Kigo".
3. Si aparece en gris (offline) o no aparece, hay un problema técnico.

**Si no aparece**: Kigo fue expulsado. Vuelve a [invitarlo](../empezar/invitar.md).

**Si aparece offline**: Kigo está experimentando una incidencia. Espera unos minutos. Si pasa de 30 minutos, abre un ticket en el [servidor de soporte](https://discord.gg/RRy8t5mfQe).

## Comprobación 2: ¿Estás en el canal correcto?

Algunos comandos solo funcionan en canales específicos (por ejemplo, `/configuración` y `/setup` solo en canales donde Kigo tiene permisos). Si ejecutas un comando en un canal donde Kigo no tiene permisos de lectura o envío, no responderá.

## Comprobación 3: ¿El comando existe?

Kigo registra los comandos al arrancar. Si un comando se añadió en una actualización reciente, tu Discord puede tardar hasta 1 hora en mostrarlo (es una limitación de Discord, no de Kigo).

Para forzar la actualización: cierra y abre Discord.

## Comprobación 4: ¿Hay un error en la respuesta?

A veces Kigo responde, pero con un mensaje de error. Lee el mensaje con atención. Los más comunes:

- **"No tengo permisos para..."** — Falta un permiso en el rol de Kigo. Revisa [No puedo usar este comando](no-puedo-usar-comando.md).
- **"Este comando solo puede usarlo el owner del servidor"** — Solo el owner del servidor (no mods) puede usar este comando. Pide al owner que lo ejecute.
- **"Algo salió mal"** — Error interno. Intenta de nuevo en unos segundos. Si persiste, abre un ticket.

## Comprobación 5: ¿El servidor está en modo mantenimiento?

Si Kigo está en mantenimiento programado, verás un mensaje al ejecutar cualquier comando. Esto es raro y se avisa con antelación en el [servidor de soporte](https://discord.gg/RRy8t5mfQe).

## Comprobación 6: ¿Tu Discord está actualizado?

Discord actualiza su cliente con frecuencia. Las versiones muy antiguas pueden no mostrar bien los nuevos slash commands. Actualiza Discord (o reinicia la app de escritorio / móvil).

## Si nada funciona

Abre un ticket en el [servidor de soporte](https://discord.gg/RRy8t5mfQe) con:

- ID del servidor
- Hora exacta del problema
- Comando que intentaste usar
- Captura del error (si hay)
- Resultado de las 6 comprobaciones

## Siguiente paso

[Aprende por qué no puedes usar un comando específico →](no-puedo-usar-comando.md) o vuelve al [índice de problemas](index.md).
