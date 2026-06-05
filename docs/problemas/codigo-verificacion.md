# No encuentro el botón de verificación

La verificación con código es una de las funciones más útiles de Kigo, pero también una de las que más confusión genera porque el usuario no siempre entiende dónde tiene que pulsar.

## El problema más común: el usuario busca en el DM

Kigo envía un DM de bienvenida al usuario con instrucciones ("ve al canal X, pulsa Verificate"). Pero ese DM **no contiene el botón**: solo contiene el texto con la ruta a seguir. El botón está físicamente en el canal de verificación del servidor.

**Solución paso a paso (para el usuario que tiene el problema, no para el admin):**

1. Abrir Discord y entrar al servidor (no al DM con Kigo, sino al servidor).
2. Buscar el canal llamado `#verificación` o `#verify` o el que el admin haya configurado.
3. Dentro de ese canal hay un mensaje fijado con un botón azul que dice **Verificate**.
4. Pulsar el botón. Aparecerá un menú con 3 opciones de código de 6 dígitos, solo para ti (es efímero, nadie más lo ve).
5. Seleccionar el código que creas correcto. Kigo te da el rol al instante.

## Si el DM de bienvenida no llegó

Discord permite a los usuarios configurar quién les puede enviar mensajes directos. Si esa configuración es restrictiva, Kigo no puede mandar el DM. Pero eso no es un problema real:

- Kigo publica automáticamente el mismo aviso directamente en el canal de verificación.
- El botón está en ese canal aunque el DM nunca haya llegado.
- El usuario puede seguir los pasos de la sección anterior sin necesidad del DM.

Si quieres verificarlo: el canal de verificación tiene un mensaje de Kigo diciendo algo como "Bienvenido! Presiona el botón Verificate arriba para verificarte. Tienes 5 minutos."

## Si el usuario no encuentra el canal de verificación

A veces el problema es que el canal no es visible para él. Esto pasa si:

- El rol "no verificado" no tiene acceso al canal de verificación.
- El canal está oculto tras un canal de "espera" al que el usuario no llega.

**Lo que puedes hacer como admin:**

1. Escribe `/configuración` → **Verificación**.
2. Revisa que el campo "Canal de verificación" apunte a un canal real y accesible.
3. Verifica que ese canal sea visible para el rol por defecto del servidor (los nuevos miembros deben poder leerlo).

## Si el código caduca antes de seleccionarlo

Por defecto el menú caduca a los 5 minutos (es el mismo tiempo que el timeout de expulsión). Pasado ese tiempo:

- El usuario es expulsado del servidor.
- Kigo le envía un DM con un enlace de invitación válido por 5 días para que pueda reentrar.
- Al reentrar, vuelve a tener 5 minutos para verificar.

Si quieres dar más tiempo, ve a `/configuración` → **Verificación** → **Tiempo límite**.

## Si el menú no aparece al pulsar el botón

Esto puede pasar si:

- El usuario ya está verificado (Kigo le dice "Ya estás verificado").
- Hay un cooldown de 30 segundos (para evitar floods de pulsaciones). Espera medio minuto y vuelve a intentarlo.
- Kigo no está conectado (raro, pero pasa). Mira [El bot no responde](bot-no-responde.md).

## Si el problema es persistente

Si después de todo esto el usuario sigue sin poder verificar, abre un ticket en el [servidor de soporte](https://discord.gg/RRy8t5mfQe) con:

- El ID del usuario (click derecho → "Copiar ID de usuario", requiere modo developer).
- El ID del servidor.
- Captura del canal de verificación mostrando el botón.
- Hora exacta en que el usuario entró al servidor (para revisar los logs).

## Siguiente paso

[Aprende a configurar el sistema de verificación →](../proteccion/verificacion.md) o vuelve al [índice de problemas](index.md).
