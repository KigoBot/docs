# Verificación

Cuando un nuevo miembro entra al servidor, Kigo le avisa para que se verifique. La verificación es **siempre en un canal del servidor**: el usuario pulsa un botón, ve un menú con 3 opciones de código y selecciona la correcta. Si no lo hace en 5 minutos, es expulsado.

## Por qué existe

La verificación con código es la forma más efectiva de filtrar multicuentas y bots de verificación masiva. Una persona real puede pulsar un botón y leer un menú en 10 segundos. Un bot de spam típico no sabe cuál de las 3 opciones es la correcta: solo acertará un 33% de las veces, y si falla, queda registrado y expulsado.

## Cómo funciona el flujo

1. **El nuevo miembro entra al servidor.** Discord le muestra el servidor con los canales visibles para él.
2. **Kigo le envía un DM de bienvenida** con instrucciones: "ve al canal de verificación, pulsa el botón Verificate, selecciona el código correcto". Si el DM falla (DMs cerrados), Kigo publica el mismo aviso en el canal de verificación como fallback.
3. **El usuario pulsa el botón "Verificate"** que está fijado en el canal de verificación. Kigo le muestra (solo a él, mensaje efímero) un menú desplegable con 3 opciones de código de 6 dígitos. Solo UNA de las tres es la correcta; las otras son señuelos.
4. **El usuario selecciona** la opción que cree correcta en el menú. Kigo valida al instante.
5. **Si acierta**, Kigo le asigna el rol de "verificado" y ahora puede ver el resto de canales.
6. **Si falla** (o no contesta), se le expulsa automáticamente tras 5 minutos. Se le manda un DM con un enlace de invitación válido por 5 días por si quiere volver a intentarlo.
7. **Todo esto queda registrado** en el canal de logs.

## Por qué 3 códigos y no 1

Si Kigo mostrara un único código, cualquier bot de spam que entre al servidor podría leer ese código y enviarlo. Con 3 opciones donde solo 1 es correcta, el bot tendría que adivinar cuál de las tres es la buena. La probabilidad de acertar es del 33%, y si falla, queda registrado y expulsado.

Esto se llama "verificación con códigos señuelo" y es más efectiva que mostrar un único código.

## Qué ven los miembros verificados

Nada especial. Una vez verificado, el miembro tiene el rol de "verificado" y puede usar el servidor normalmente.

Los miembros NO verificados solo ven el canal de verificación y un canal de "espera". No pueden escribir en otros canales.

## Configuración

Ve a `/configuración` y entra en la sección **Verificación**. Verás:

- **Activar verificación** (on/off)
- **Tiempo límite** (1 minuto, 5 minutos, 15 minutos, etc.)
- **Rol de verificado** (el rol que se asigna al pasar la verificación)
- **Canal de verificación** (el canal donde está el botón Verificate)

## Multicuentas

La verificación se complementa con el filtro de multicuentas. Si una cuenta tiene menos de X días de antigüedad (por defecto 15), no se le permite ni verificar: se le expulsa directamente.

Para configurar este umbral: `/configuración` → **Protección** → **Multicuentas**.

## Bots en el servidor

Kigo puede estar configurado para que los bots NO necesiten verificar (porque muchos bots legítimos no pueden pulsar botones en un canal). Hay tres modos:

- **`Permitir todos`**: cualquier bot puede entrar sin verificar.
- **`Solo bots verificados`**: solo los bots marcados como "verificados" por Discord (que requieren owner real) pueden entrar.
- **`Bloquear todos`**: ningún bot puede entrar. Útil para servidores 100% humanos.

Por defecto está en `Solo bots verificados`.

## Lo que NO hace

- **No verifica la identidad del usuario.** Solo verifica que hay una persona real detrás de la cuenta. Alguien con malas intenciones puede verificar y luego empezar a hacer cosas malas.
- **No previene multicuentas con cuentas viejas.** Si alguien crea 3 cuentas y las usa durante 6 meses antes de atacarte, todas pasarán la verificación.
- **No funciona si el usuario no encuentra el canal de verificación.** El botón solo aparece en el canal configurado para ello. Si el DM de bienvenida falla y el usuario no localiza el canal, se le expulsa a los 5 minutos. Hay una página específica para esto: [No encuentro el botón de verificación](../problemas/codigo-verificacion.md).

## Problemas frecuentes

**"No me llega el DM de bienvenida"** — El usuario probablemente tiene los DMs cerrados. Pero no pasa nada: Kigo publica el mismo aviso directamente en el canal de verificación. Más detalles en [No encuentro el botón de verificación](../problemas/codigo-verificacion.md).

**"El código se queda colgado"** — Probablemente es un timeout de la API de Discord. El usuario puede pulsar el botón otra vez; Kigo generará códigos nuevos.

**"Falla siempre"** — Verifica que el usuario no tenga el botón en una pestaña diferente o que no haya caducado el menú (5 minutos por defecto).

## Siguiente paso

[Aprende cómo funciona la lista blanca →](whitelist.md), que te permite hacer excepciones a toda esta protección.
