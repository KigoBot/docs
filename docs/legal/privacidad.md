# Política de Privacidad

**Última actualización:** 5 de junio de 2026
**Versión:** 1.0

Esta Política de Privacidad explica qué datos recoge Kigo, por qué los recoge, cómo los protege y qué derechos tienes como usuario. Está redactada para cumplir con el Reglamento (UE) 2016/679 (RGPD) y la Ley Orgánica 3/2018 (LOPDGDD).

!!! info "Sobre el alcance de esta política"
    Esta política se aplica al **servicio de Kigo** (el bot de moderación y protección que se invita desde el enlace oficial y aparece listado en [Top.gg](https://top.gg/bot/917041621042888776)). El responsable del tratamiento de los datos personales gestionados por Kigo es JuanQP07.

Kigo es un servicio **gestionado por su autor**: no es software de código abierto ni auto-hospedable. Existe una sola instancia del bot, mantenida por el autor, y los datos se procesan en la infraestructura que él controla. Esto significa que **no hay terceros** ejecutando su propio Kigo sobre tus datos: o usas el servicio público, o no lo usas.

## 1. Responsable del tratamiento

- **Identidad:** JuanQP07
- **Actividad:** mantenimiento de Kigo, un bot de Discord de moderación y protección.
- **Contacto:** [Servidor de soporte de Kigo en Discord](https://discord.gg/wmky5nBRR2)
- **Domicilio a efectos de notificación:** el facilitado en el servidor de soporte.

Kigo es un proyecto de una sola persona, por lo que **no hay un Delegado de Protección de Datos (DPO) formal**. Para cualquier asunto relativo a protección de datos, contacta directamente con el responsable por los medios indicados.

## 2. Datos que SÍ recogemos

Los datos que Kigo almacena se pueden dividir en tres categorías.

### 2.1. Configuración de servidores (base de datos persistente)

Por cada servidor donde Kigo está añadido:

- **ID del servidor** (snowflake de Discord).
- **Configuración del anti-raid:** qué protecciones están activas, sus umbrales, y el ID del canal de logs (si está configurado).
- **Configuración del automod:** qué filtros están activos y el límite de spam.
- **Configuración de verificación:** ID del canal de verificación, ID del rol de verificado, si está activa o no.
- **Lista blanca:** IDs de usuarios, canales, categorías y roles exentos de protección.
- **Timestamps:** cuándo se registró el servidor en Kigo y cuándo se actualizó por última vez.

### 2.2. Datos de usuarios individuales (base de datos persistente)

Para usuarios que canjean un código premium:

- **ID de usuario** de Discord (snowflake).
- **Tier de premium** (1, 2 o 3) y **fechas de inicio y fin.**

Para los códigos premium:

- El **código** (cadena única).
- Si está **canjeado**, por quién (ID) y cuándo.

### 2.3. Datos temporales (caché con caducidad automática)

| Dato | Caducidad | Motivo |
|---|---|---|
| Hash del código de verificación de un usuario | 5 minutos | Validar la verificación sin guardar el código en claro |
| Cache del último ejecutor de un evento de audit log | 15 s si hay resultado, 5 s si no | Evitar llamadas repetidas a la API de Discord |
| Contadores de rate limit (spam, cooldowns de comandos) | 30 segundos | Detectar flood y abuso de comandos |
| Cache de configuración de guild | 5 minutos | Reducir consultas a la base de datos principal |

Nada de lo guardado en la caché temporal es identificable más allá de lo estrictamente necesario para la operación.

### 2.4. Datos en memoria (mueren al reiniciar el bot)

- Cache local de configuración por shard.
- Timeouts de verificación pendientes.
- Métricas operativas internas (contadores y duraciones de comandos).

Estos datos **nunca salen del proceso del bot** y se reconstruyen al reiniciar.

## 3. Datos que NO recogemos

Esto es tan importante como lo que sí recogemos. Kigo **NO** almacena:

- **Contenido de mensajes** de los usuarios. Cuando Kigo lee un mensaje para detectar spam, lo hace en memoria y solo a efectos de la decisión inmediata. El contenido no se guarda de forma persistente. Aparece dentro de embeds de log enviados al canal de logs del servidor, pero esos embeds son gestionados por Discord, no por Kigo.
- **Mensajes directos** entre usuarios. Kigo no lee los DMs que recibe; solo envía los suyos (ver sección 4).
- **Audio de canales de voz.** Kigo no se conecta a voz ni procesa audio.
- **Datos de presencia** (online, idle, en qué juego está, etc.).
- **Historial de actividad** de los usuarios fuera de los servidores donde Kigo está instalado.
- **Analítica externa, tracking, cookies** en sitios web. El sitio de documentación de Kigo no usa cookies de seguimiento.
- **Direcciones IP, datos de navegación, geolocalización** de los usuarios.
- **Correos electrónicos, números de teléfono** u otros datos de contacto fuera de Discord.

## 4. Mensajes que Kigo envía por DM

Kigo envía DMs en situaciones muy concretas. Esos mensajes **los entrega Discord**, no Kigo, y quedan en los servidores de Discord según la configuración de privacidad del usuario receptor. Los casos son:

- Al añadir Kigo a un servidor nuevo: DM de bienvenida al **owner del servidor** con consejos de configuración y enlaces a soporte, documentación y Top.gg.
- Al entrar un miembro nuevo a un servidor con verificación activa: DM con instrucciones (si falla, se publica el mismo aviso en el canal de verificación como fallback).
- Al expulsar a una multicuenta detectada: DM indicando la fecha en la que podrá reentrar.
- Al expulsar a un usuario por no verificar a tiempo: DM con un enlace de invitación válido por 5 días.
- Al exportar un backup desde `/configuración`: DM con el archivo `.json` adjunto.

Kigo **no envía DMs de aviso** por sanciones de automod (spam, ghost pings, menciones masivas, enlaces peligrosos): esas sanciones las aplica Discord directamente y el usuario las ve en el canal.

## 5. Finalidad y base jurídica

| Finalidad | Base jurídica |
|---|---|
| Proteger el servidor del owner (anti-raid, automod, verificación) | **Interés legítimo** del owner del servidor, que es a su vez el responsable de los datos de sus miembros. Kigo actúa como encargado del tratamiento. |
| Permitir la verificación de nuevos miembros | **Interés legítimo** del owner. |
| Gestionar el premium y los códigos canjeados | **Ejecución del contrato** (canjear un código es aceptar unas condiciones de uso del premium). |
| Métricas operativas del bot (comandos ejecutados, duraciones, acciones del anti-raid) | **Interés legítimo** del autor para mantener la calidad del servicio. |

Kigo **no usa los datos para marketing, perfilado publicitario, ni para entrenar modelos de inteligencia artificial**.

## 6. Conservación de los datos

- **Configuración de un servidor:** se mantiene mientras el servidor está en la base de datos. Si el servidor se elimina de Kigo, sus datos se borran en 30 días.
- **Datos de premium:** se mantienen hasta que el usuario solicite la baja o hasta 12 meses después de la expiración del premium, lo que ocurra antes.
- **Códigos premium:** los no canjeados se mantienen indefinidamente (no contienen datos personales hasta que se canjeen). Los canjeados se conservan 24 meses para auditoría.
- **Datos en caché temporal:** expiran automáticamente. No requieren acción.
- **Backups firmados exportados por el usuario:** Kigo no los guarda. Son responsabilidad del usuario.

## 7. Decisiones automatizadas

El anti-raid y el automod de Kigo **toman decisiones automatizadas** que pueden afectar a usuarios (baneos, silencios, expulsiones). Concretamente:

- **Multicuentas:** Kigo expulsa automáticamente a cuentas con menos de X días de antigüedad, según la configuración del servidor. Esta decisión es **completamente automática**.
- **Spam y flood:** Kigo silencia automáticamente a usuarios que superan el límite de mensajes en una ventana de tiempo.
- **Baneos por raid:** Kigo banea automáticamente al ejecutor de una acción masiva cuando supera el umbral configurado.

En todos los casos:

- El usuario afectado puede **apelar** contactando con el owner del servidor.
- El owner del servidor puede **deshacer la sanción manualmente** (los bans de Kigo no son "permanentes" en el sentido de que el owner puede revocarlos).
- El owner puede **desactivar** la protección correspondiente en `/configuración`.
- Si el bot aplica una sanción incorrecta, el usuario puede pedir revisión a través del [servidor de soporte](https://discord.gg/wmky5nBRR2).

## 8. Destinatarios y encargados del tratamiento

Los datos se comparten con:

- **Discord, Inc.** como plataforma sobre la que corre Kigo. Discord tiene su propia [Política de Privacidad](https://discord.com/privacy).
- **Proveedores de infraestructura** del autor (alojamiento de la base de datos y de la caché). El autor utiliza proveedores europeos; los datos se almacenan en la UE.
- **GitHub (Microsoft)** únicamente como proveedor del **sitio de documentación** público (alojado en `kigobot.github.io`). El sitio no recoge datos personales de los visitantes.

Kigo **no vende, no cede, no alquila** datos personales a terceros con fines comerciales.

## 9. Transferencias internacionales

Kigo está alojado en proveedores europeos, por lo que la mayoría de los datos no salen del Espacio Económico Europeo. Sin embargo:

- Discord procesa los datos en su infraestructura global, fuera del EEE en algunos casos. Las transferencias de Discord están cubiertas por sus [Cláusulas Contractuales Tipo](https://discord.com/privacy).
- GitHub (Microsoft) puede alojar copias del sitio de documentación en servidores fuera del EEE. Está cubierto por sus propias garantías contractuales.

Si en el futuro Kigo migra a un proveedor con sede fuera del EEE, se firmarán las cláusulas contractuales tipo de la Comisión Europea o se adoptará otra garantía equivalente.

## 10. Tus derechos (RGPD)

Como usuario afectado, tienes los siguientes derechos:

- **Acceso:** saber qué datos tuyos tiene Kigo.
- **Rectificación:** corregir datos inexactos.
- **Supresión ("derecho al olvido"):** pedir que se eliminen tus datos.
- **Limitación:** pedir que se dejen de usar mientras se resuelve una disputa.
- **Portabilidad:** recibir tus datos en un formato estructurado y legible por máquina (aplicable sobre todo a los datos de premium).
- **Oposición:** oponerte al tratamiento basado en interés legítimo, por motivos relacionados con tu situación particular.
- **Revocación del consentimiento:** cuando el tratamiento se base en consentimiento, retirarlo en cualquier momento.
- **Reclamación ante la autoridad de control:** presentar una denuncia ante la Agencia Española de Protección de Datos (AEPD) u otra autoridad competente.

## 11. Cómo ejercer tus derechos

Para ejercer cualquiera de estos derechos:

1. Abre un ticket en el [servidor de soporte de Kigo](https://discord.gg/wmky5nBRR2) indicando claramente qué derecho quieres ejercer y sobre qué datos.
2. El responsable verificará tu identidad (por ejemplo, comprobando que el ID de Discord desde el que escribes coincide con el de los datos solicitados).
3. Se responderá en un plazo máximo de **30 días naturales** desde la recepción de la solicitud, ampliable a 60 días en casos complejos (en cuyo caso se informará del retraso).

Si tu solicitud requiere actuar sobre datos de un servidor que no administras, Kigo **necesitará la confirmación del owner** del servidor para proceder (porque el owner es el responsable de los datos de los miembros de su servidor). Esto es así aunque el RGPD te dé derecho a la supresión: en última instancia, el owner del servidor decide qué datos de sus miembros se conservan, salvo que medie una obligación legal.

## 12. Seguridad

Kigo aplica las siguientes medidas técnicas y organizativas:

- **Hashing** de los códigos de verificación antes de almacenarlos. El código en claro nunca se guarda, ni siquiera temporalmente.
- **Firma criptográfica** de los backups exportados para detectar manipulaciones al importarlos.
- **Caché con caducidad automática** para que ningún dato temporal persista más de lo necesario.
- **Conexiones cifradas** a las bases de datos (los proveedores utilizados soportan TLS).
- **Variables de entorno** para secretos (token del bot, claves de firma). El bot no expone públicamente los endpoints internos de administración.
- **No se imprimen secretos en logs**, ni siquiera en modo debug.

Aun así, ningún sistema es 100% seguro. Si detectas una vulnerabilidad, repórtala responsablemente en el [servidor de soporte](https://discord.gg/wmky5nBRR2).

## 13. Menores de edad

Kigo no está dirigido a menores de 14 años. La plataforma Discord exige una edad mínima de 13 años (en la UE y el Reino Unido, 14 si el país así lo establece), por lo que cualquier uso de Kigo por parte de un menor de esa edad contraviene tanto la política de Discord como la nuestra.

Si detectas que un menor de 14 años está usando Kigo con datos que deberían ser eliminados, contacta con el [servidor de soporte](https://discord.gg/wmky5nBRR2) y procederemos a la supresión.

## 14. Cambios a esta política

Esta política puede actualizarse para reflejar cambios en el servicio, en la legislación o en las prácticas internas. Los cambios importantes se comunicarán en el servidor de soporte con al menos 14 días de antelación. La fecha de la última actualización aparece al principio de esta página.

## 15. Contacto

Para cualquier asunto relacionado con esta política (solicitudes de acceso, supresión, dudas, quejas):

- **Servidor de soporte de Kigo:** [discord.gg/wmky5nBRR2](https://discord.gg/wmky5nBRR2)
- **AEPD** (autoridad de control en España): [www.aepd.es](https://www.aepd.es)

---

Ver también: [Términos de Servicio](terminos.md).
