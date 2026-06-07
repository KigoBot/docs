# Comando `/botinfo`

Muestra información técnica sobre Kigo: número de servidores, ping, uso de RAM, CPU, versión, etc.

## Cómo usarlo

1. Escribe `/botinfo` en cualquier canal.
2. Pulsa Enter.

Kigo te responde con un embed efímero con la información.

## Qué muestra

- **Servidores:** total de servidores donde Kigo está añadido (de la caché interna con un TTL de 60 s).
- **Actividad:** cuándo se conectó el bot por última vez (en formato Discord relative time).
- **Versión:** la versión actual del bot (con el commit SHA corto si está disponible).
- **Pings:**
    - **Bot:** ping del websocket (`client.ws.ping`).
    - **Base de datos:** tiempo de una consulta a PostgreSQL.
    - **Caché:** tiempo de un `PING` a Redis.
- **RAM:** memoria heap usada por el proceso.
- **CPU:** porcentaje de CPU usado.

## El botón "Ver top 10 servidores"

El embed incluye un botón azul **"Ver top 10 servidores"**. Al pulsarlo, Kigo te responde (efímero) con el top 10 global de servidores por número de miembros. El top se cachea durante 60 segundos.

## Requisitos

- Cualquier miembro del servidor puede usar `/botinfo`. No requiere permisos especiales.

## Siguiente paso

[Información de shards con `/clusters` →](clusters.md) o [información de un usuario con `/info-user` →](info-user.md).
