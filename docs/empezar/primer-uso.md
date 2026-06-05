# Primer uso

Kigo viene con un asistente paso a paso que te deja el servidor protegido en unos 5 minutos. No necesitas leer toda la documentación para empezar.

## Elige tu camino

Tienes dos formas de empezar:

**A) Asistente `/setup` (recomendado para la primera vez)**

Te guía por 12 pasos en orden. Cada paso te explica qué estás configurando y por qué. Ideal si nunca has usado Kigo o si quieres una configuración "razonable" sin pensar demasiado.

**B) Panel `/configuración`**

Un menú con todas las opciones a la vista. Útil si ya sabes lo que quieres cambiar o si necesitas ajustar algo específico después de usar `/setup`.

## Opción A: el asistente `/setup`

1. Escribe `/setup` en cualquier canal.
2. Kigo te mostrará un menú con los pasos. Recomiendo seguir el orden propuesto.
3. Cada paso te hace 2-3 preguntas. Las opciones por defecto son conservadoras: activan la protección sin molestar a los miembros legítimos.

### Lo que configura paso a paso

| Paso | Qué hace |
|---|---|
| 1. Bienvenida | Activa el sistema antiraid y automod |
| 2. Permisos | Revisa que Kigo tenga los permisos correctos |
| 3. Logs | Crea (o reutiliza) un canal donde Kigo dejará registro de las acciones |
| 4. Verificación | Configura el sistema de códigos para nuevos miembros |
| 5. Lista blanca | Te permite añadir usuarios/canales/roles que NO se verán afectados |
| 6. Nivel de multicuentas | Define si quieres filtrar cuentas nuevas o muy nuevas |
| 7. Canales de protección | Configura si Kigo debe crear canales especiales |
| 8. Roles de protección | Igual, pero para roles |
| 9. Bots y multicuentas | Decide si los bots pueden entrar y cómo |
| 10. Sanciones | Configura las acciones automáticas (kicks, bans) |
| 11. Automod | Activa el bloqueo de palabras, links, spam, etc. |
| 12. Resumen | Te muestra un resumen de todo lo que se ha configurado |

### Cuándo saltarte el asistente

Si tu servidor es muy pequeño (menos de 20 personas) y solo quieres protección básica, puedes saltarte el asistente e ir directo a `/configuración`. La protección por defecto ya es razonable.

## Opción B: el panel `/configuración`

Úsalo cuando:

- Ya terminaste el `/setup` y quieres ajustar algo concreto
- Solo quieres cambiar una cosa (por ejemplo, el canal de logs)
- Quieres ver de un vistazo qué tienes configurado

## Siguiente paso

Ahora que Kigo está configurado, echa un vistazo a [los permisos que pediste](permisos.md) para entender qué puede y qué no puede hacer.
