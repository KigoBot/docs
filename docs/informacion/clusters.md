# Comando `/clusters`

Muestra el estado de cada uno de los **shards** (subprocesos del bot) que ejecuta Kigo. Es una vista técnica pensada para diagnosticar problemas.

!!! info "Solo relevante si Kigo usa sharding"
    Si Kigo se ejecuta como un único proceso (sin sharding), el comando responde "El bot no está usando sharding." Kigo, en producción, se ejecuta con múltiples shards; cada shard es responsable de un subconjunto de servidores.

## Cómo usarlo

1. Escribe `/clusters` en cualquier canal.
2. Pulsa Enter.

Kigo te responde con dos embeds: uno por shard y otro con los totales.

## Qué muestra

Para cada shard:

- **Servidores** en caché.
- **Usuarios en caché.**
- **Estado** (`Conectado`, `Conectando`, `Reconectando`, `Inactivo`, `Casi`, `Desconectado`).
- **Ping** del websocket.
- **Uso de RAM.**
- **Uso de CPU.**

El embed final agrega los totales: suma de servidores, usuarios, ping promedio, suma de RAM y suma de CPU.

## Cuándo usarlo

- Estás experimentando lentitud o respuestas extrañas en tu servidor y quieres saber si tu shard está sobrecargado.
- Sospechas que un shard está caído o reiniciándose.
- Quieres tener una visión general del estado de Kigo antes de abrir un ticket en el servidor de soporte.

## Requisitos

- Cualquier miembro del servidor puede usar `/clusters`. No requiere permisos especiales.

## Lo que NO hace

- **No reinicia shards caídos.** Solo informa.
- **No muestra logs.** Para ver logs, abre un ticket en el [servidor de soporte](https://discord.gg/wmky5nBRR2).

## Siguiente paso

[Información general del bot con `/botinfo` →](botinfo.md) o [información de un usuario con `/info-user` →](info-user.md).
