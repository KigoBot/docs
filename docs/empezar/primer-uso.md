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
| 1. Bienvenida | Pantalla de inicio con advertencias de permisos si las hay |
| 2. Permisos | Revisa que Kigo tenga los permisos correctos y su rol esté arriba de los demás |
| 3. Registros | Elige o crea el canal de logs donde Kigo dejará el historial de acciones |
| 4. Verificación | Configura el rol y el canal de verificación, y publica el mensaje con el botón |
| 5. Lista Blanca | Añade usuarios, roles y canales que NO se verán afectados por la protección |
| 6. Nivel de Protección | Elige Nulo (0%), Simple (25%), Básico (50%) o Extremo (100%) |
| 7. Canales | Activar/desactivar protección contra crear/eliminar/actualizar canales en masa |
| 8. Roles | Activar/desactivar protección contra crear/eliminar/actualizar roles en masa |
| 9. Bots & Multicuentas | Política de bots admitidos (verificados/no verificados/todos) y antigüedad mínima de cuentas |
| 10. Sanciones | Activar protección contra bans, expulsiones y actualizaciones masivas del servidor |
| 11. Auto Moderación | Activar las reglas de automod (Everyone/Here, enlaces Discord, enlaces Web, ghost ping, flood) |
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
