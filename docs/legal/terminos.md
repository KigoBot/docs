# Términos de Servicio

**Última actualización:** 5 de junio de 2026
**Versión:** 1.0

Estos Términos de Servicio regulan el uso de Kigo, un bot de moderación y protección para servidores de Discord. Al invitar a Kigo a un servidor, al usar sus comandos o al interactuar con él, aceptas estos términos en tu nombre y en el de los miembros de los servidores que administras.

!!! info "Sobre el alcance de estos términos"
    Estos términos se aplican al **servicio de Kigo** (el bot de moderación y protección que se invita desde el enlace oficial y aparece listado en [Top.gg](https://top.gg/bot/917041621042888776)). Kigo es un **servicio gestionado por su autor**: existe una sola instancia del bot, no es software auto-hospedable ni de código abierto. Al usarlo, aceptas estos términos en tu nombre y en el de los miembros de los servidores que administras.

## 1. Identificación del titular

Kigo es un proyecto mantenido por:

- **Nombre:** JuanQP07
- **Contacto:** [Servidor de soporte de Kigo en Discord](https://discord.gg/wmky5nBRR2)
- **Bot:** listado en [Top.gg](https://top.gg/bot/917041621042888776)

## 2. Descripción del servicio

Kigo es un bot de Discord que ofrece:

- **Protección automática** contra raids (creación masiva de canales, roles, multicuentas, baneos coordinados).
- **Verificación de nuevos miembros** mediante un botón y un menú desplegable con códigos señuelo.
- **Moderación manual** mediante comandos slash (`/ban`, `/kick`, `/mute`, etc.).
- **Whitelist** para exceptuar a usuarios, canales o roles de la protección.
- **Sistema de premium** con funciones ampliadas canjeables por códigos.
- **Backups firmados** de la configuración de cada servidor.

El servicio se proporciona "tal cual" y puede evolucionar, ampliarse o reducirse sin previo aviso.

## 3. Requisitos para usar Kigo

Para usar Kigo necesitas:

- Una cuenta de Discord válida y en regla con los [Términos de Servicio de Discord](https://discord.com/terms).
- Permisos en el servidor para añadir bots (ser owner o tener el permiso "Gestionar servidor").
- Aceptar estos términos.

Si añades Kigo a un servidor en nombre de una organización, declaras que tienes autoridad para aceptarlos en su nombre.

## 4. Uso aceptable

Kigo está pensado para proteger servidores. **No está permitido** usarlo para:

- Spam, flooding o abuso de comandos.
- Intentar eludir las sanciones de otro bot o de Kigo.
- Acosar, amenazar o doxxear a otros usuarios, dentro o fuera de Discord.
- Usar Kigo como infraestructura para actividades ilegales.
- Reemplazar el consentimiento del owner de un servidor (por ejemplo, anuncias en servidores sin que el owner lo haya pedido).
- Recopilar datos de usuarios con Kigo para usos distintos a la protección de un servidor.

El incumplimiento puede provocar la expulsión del bot del servidor, la cancelación de premium y, en casos graves, el reporte a Discord.

## 5. Premium y códigos

- El premium **no se compra con dinero**: se obtiene canjeando códigos distribuidos por el autor en eventos, colaboraciones o promociones puntuales.
- Cada código **solo se puede canjear una vez** y queda vinculado al ID de usuario que lo canjea.
- Los códigos no son transferibles una vez canjeados.
- El premium tiene una **fecha de expiración** (`premiumEnd`) que se muestra al canjearlo. Tras esa fecha, las funciones premium se desactivan automáticamente.
- **No hay reembolsos** porque no hay compra: si tienes un problema con un código, abre un ticket en el servidor de soporte.
- El autor se reserva el derecho a revocar un premium por incumplimiento de estos términos, informando previamente.

## 6. Backups firmados

Kigo permite exportar la configuración de un servidor como un archivo JSON firmado criptográficamente (HMAC-SHA256).

- La firma sirve para que Kigo **detecte modificaciones no autorizadas** al archivo y rechace importarlo.
- **El archivo puede contener información sensible** del servidor (IDs de canales, roles, configuración). Guárdalo en un lugar seguro.
- Si compartes un backup con alguien, le estás dando acceso a esa información. Kigo no se hace responsable del uso que se haga del archivo una vez sale de tu equipo.
- Kigo **no puede recuperar backups perdidos** que no hayas exportado tú. Hazlo periódicamente.

## 7. Limitación de responsabilidad

Kigo se ofrece "tal cual" y "según disponibilidad". El autor:

- **No garantiza** que el servicio esté libre de interrupciones, errores o pérdida de datos.
- **No se hace responsable** de los daños directos, indirectos, incidentales o consecuenciales derivados del uso (o la imposibilidad de usar) Kigo. Esto incluye, sin limitarse a: pérdida de mensajes, sanciones aplicadas por error, fallos de protección durante un raid, o problemas derivados de cambios en la API de Discord.
- **No se hace responsable** de la configuración aplicada por los usuarios en sus servidores. Si configuras Kigo para banear automáticamente, las consecuencias de esos baneos son tuyas.
- **No se hace responsable** del contenido de los mensajes que Kigo lee para moderar (spam, ghost pings). Esos mensajes siguen siendo propiedad de Discord y de sus autores.
- **No se hace responsable** de las acciones de moderación manuales aplicadas por los usuarios a través de Kigo (ban, kick, mute, warn, etc.). Esas acciones las ejecutas tú; Kigo solo es la herramienta.

## 8. Cambios al servicio

El autor puede:

- Añadir, modificar o eliminar funciones en cualquier momento.
- Cambiar los requisitos técnicos (versión de Discord, intents necesarios).
- Interrumpir el servicio temporalmente por mantenimiento, actualizaciones o causas de fuerza mayor.

Se intentará avisar de los cambios importantes en el [servidor de soporte](https://discord.gg/wmky5nBRR2) y, cuando sea posible, en este sitio de documentación.

## 9. Terminación

- **Tú** puedes dejar de usar Kigo en cualquier momento: expulsa al bot del servidor y, si quieres, desactiva antes los módulos en `/configuración` para limpiar la configuración.
- **El autor** puede dejar de dar el servicio. En ese caso, intentará avisar con al menos 30 días de antelación. Tras el aviso, los datos se conservarán durante un plazo razonable para que puedas exportarlos con `/configuración` → **Backups** → **Exportar**, salvo que una causa legal justifique lo contrario.
- **El autor** puede expulsar a Kigo de un servidor concreto o denegar el servicio a un usuario si hay incumplimiento de estos términos o de las [Directivas de la comunidad de Discord](https://discord.com/guidelines).

Tras la terminación, los datos asociados al servidor se eliminan según la política de retención descrita en la [Política de Privacidad](privacidad.md).

## 10. Cambios a estos términos

Estos términos pueden actualizarse. Los cambios importantes se comunicarán en el servidor de soporte con al menos 14 días de antelación. La fecha de la última actualización aparece al principio de esta página. El uso continuado del bot después de la fecha de entrada en vigor de los nuevos términos implica su aceptación.

## 11. Ley aplicable y jurisdicción

- Estos términos se rigen por la **legislación española y de la Unión Europea**, en particular por el Reglamento (UE) 2016/679 (RGPD) y la Ley Orgánica 3/2018 (LOPDGDD).
- Para cualquier controversia derivada de estos términos, las partes se someten a los **juzgados y tribunales de la ciudad de Madrid (España)**, salvo que la normativa procesal o de consumo aplicable fije otro fuero.

## 12. Contacto

Para cualquier duda sobre estos términos, abre un ticket en el [servidor de soporte de Kigo](https://discord.gg/wmky5nBRR2) o contacta a través de Top.gg.

## 13. Disposiciones finales

- Si alguna cláusula de estos términos se considera inválida por una autoridad competente, el resto sigue en vigor.
- La no exigencia de una cláusula en un momento concreto no implica su renuncia.
- Estos términos constituyen el acuerdo completo entre tú y el autor respecto al uso de Kigo, y sustituyen cualquier acuerdo previo verbal o escrito.

---

Ver también: [Política de Privacidad](privacidad.md).
