# Protección

Kigo protege tu servidor en cuatro frentes distintos. Todos son opcionales y se pueden activar por separado.

## Los cuatro módulos

**[Anti-raid](antiraid.md)** — Detecta y revierte acciones masivas sospechosas: creación de canales en masa, creación de roles en masa, baneos coordinados, multicuentas. Si alguien toma el control de tu servidor o entra un grupo organizado a atacarte, Kigo lo detecta y responde en segundos.

**[Automod](automod.md)** — Filtra mensajes individuales: palabras bloqueadas, enlaces a sitios de phishing, spam, "ghost pings" (mensajes que se borran tras mencionar a alguien), flood. Complementa al anti-raid: este se ocupa de los eventos en masa, el automod de los mensajes sueltos.

**[Verificación](verificacion.md)** — Los nuevos miembros deben pulsar un botón en el canal de verificación y seleccionar el código correcto entre 3 opciones. Si no lo hacen en X minutos, son expulsados. Filtra multicuentas y bots de verificación masiva.

**[Lista blanca](whitelist.md)** — Excepciones. Usuarios, canales o roles específicos que NO se ven afectados por la protección. Útil para tu staff, canales de bots, roles de administración.

## Cuándo necesitas cada uno

- **Servidor pequeño (< 50 personas)**: solo verificación. Suficiente.
- **Servidor mediano (50-1000)**: verificación + anti-raid. Lo mínimo razonable.
- **Servidor mediano con mucha actividad pública**: añade automod para evitar spam en canales de chat.
- **Servidor grande (> 1000)**: los cuatro. La whitelist es imprescindible para no romper bots útiles.

## Cómo se relacionan

Los cuatro módulos comparten el mismo canal de logs. Si algo pasa, lo verás ahí. También comparten la misma lista blanca, así que si exentas a un usuario del anti-raid, también lo exentas del automod y de la verificación.

## Lo que pasa si activas todo

Tu servidor será estricto. Los nuevos miembros tardarán un poco más en entrar (tienen que escribir un código), el spam se borrará automáticamente, y cualquier acción masiva será revertida. Para servidores públicos muy activos esto puede ser demasiado. Puedes empezar con todo activado y luego relajar lo que sobre.

## Siguiente paso

[Aprende cómo funciona el anti-raid →](antiraid.md)
