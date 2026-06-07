# Análisis de Amenazas

El comando `/amenazas` muestra un perfil de riesgo de un usuario basado en su actividad reciente. Es la función más útil de Kigo Premium para detectar cuentas problemáticas antes de que causen daño.

![Ejemplo de /amenazas](images/amenazas-usuario.png) — *pendiente de captura real*

## Requisitos

- Tener premium activo en el servidor donde se ejecuta el comando. Si no, el bot avisa con un mensaje explicando cómo suscribirse en whop.com.

## Cómo usarlo

```
/amenazas usuario:@usuario
```

El bot responde con un panel que muestra:

- **Nivel de amenaza**: un número del 0 al 100.
- **Etiqueta**: Mínimo, Bajo, Medio, Alto o Crítico.
- **Indicador visual**: una barra de progreso con emojis.
- **Señales detectadas**: lista de qué contribuyó al puntaje.

## Las señales

El puntaje se calcula sumando el peso de varias señales. Cuanto mayor el peso, más rápida la escalada.

| Señal | Peso | Qué significa |
|---|---|---|
| Warns activos | alto | Cada warn suma puntos según su severidad (1=leve, 2=media, 3=alta). |
| Suma de severidad | medio | Aunque tengas pocos warns, si son graves suman más. |
| Detecciones de automod | medio | Si el usuario esquivó filtros muchas veces, sube. |
| Multicuenta detectada | alto | Si se detectó que la cuenta es un "alt" de otra, sube mucho. |
| Cuenta nueva | medio | Si la cuenta tiene menos de X días desde su creación. |
| Evasión detectada | alto | Si el Filtro Evasivo marcó al usuario. |

Los pesos exactos están en el código de Kigo, no son ajustables por servidor.

## Rangos de amenaza

| Puntaje | Etiqueta | Color | Qué hacer |
|---|---|---|---|
| 0-19 | Mínimo | Verde | No hay indicios de problema. |
| 20-39 | Bajo | Azul | Vigilar. No hay señales fuertes. |
| 40-59 | Medio | Amarillo | Posible problema. Considerar warn o mute. |
| 60-79 | Alto | Naranja | Problema claro. Warn o mute recomendado. |
| 80-100 | Crítico | Rojo | Acción inmediata: mute, kick o ban. |

## Por qué un solo warn puede subir el score a 30+

Los pesos están calibrados para que un solo warn severo (severidad 3) ya marque al usuario como "a vigilar". Un usuario con 3 warns de severidad 1 está en zona de "Alto", no "Medio".

Esta calibración es deliberada: es mejor sobreestimar y luego bajar el puntaje al expirar los warns, que subestimar y dejar pasar cuentas problemáticas.

## Lo que NO hace

- **No predice el futuro.** Es un resumen de actividad pasada, no un oráculo.
- **No es infalible.** Un usuario con warns por spam puede tener score bajo, y un usuario que casi nunca warns puede tener score alto por multicuenta.
- **No reemplaza al juicio humano.** Úsalo como una señal más, no como decisión automática.

## Privacidad

- El puntaje se calcula localmente en la base de datos de Kigo, no se envía a servicios externos.
- Solo se almacena el último puntaje por (usuario, servidor), no histórico.
- Si quieres borrar el puntaje de un usuario (poco común, normalmente expira solo), contacta al owner del bot.

## Siguiente paso

Si quieres ver el análisis de un usuario concreto y entender por qué su score es alto, combina `/amenazas` con `/modlogs` para ver su historial completo de warns y casos.
