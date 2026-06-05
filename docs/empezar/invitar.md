# Invita a Kigo a tu servidor

Añadir Kigo a tu servidor Discord toma menos de un minuto. Solo necesitas ser **owner del servidor** o tener permiso para **Gestionar el servidor**.

## Antes de empezar

Asegúrate de tener:

- Una cuenta de Discord
- Un servidor donde seas owner o admin
- 30 segundos

## Paso a paso

1. **Abre el enlace de invitación.** Puedes encontrarlo en la página principal de Kigo, en el canal `#enlaces` del Discord de soporte, o en [Top.gg](https://top.gg/bot/917041621042888776).

2. **Selecciona el servidor.** Discord te mostrará un menú desplegable con todos los servidores donde puedas añadir bots. Elige el que quieras proteger.

3. **Revisa los permisos.** Discord te mostrará una lista de los permisos que Kigo solicita. La pantalla tiene un montón de palancas verdes. Es normal. [Te explicamos por qué](permisos.md) en la siguiente página.

4. **Confirma con "Autorizar".** Si tu servidor tiene verificación de dos pasos, te pedirá el código.

5. **Listo.** Kigo ya está en tu servidor. Verás que aparece en la lista de miembros (offline, porque no es un usuario activo).

## Comprobar que funciona

Una vez Kigo esté en el servidor:

1. Escribe `/ayuda` en cualquier canal.
2. Kigo debería responderte con un menú de botones.

Si no responde, mira [El bot no responde](../problemas/bot-no-responde.md).

## Lo que verás los primeros segundos

Nada inmediato en el servidor. Kigo espera a que ejecutes `/configuración` o `/setup` para empezar a trabajar.

El único mensaje automático que Kigo envía al añadirlo a un servidor es un **mensaje directo al owner** (no a todos los miembros) con:

- 3 consejos rápidos: cómo configurar la protección, dónde colocar el rol del bot, y cómo usar la whitelist.
- 5 botones de enlace: Invitación, Soporte, Documentación Oficial, Discord Bot List y Top.gg.

Si no te llega el DM (por DMs cerrados o por un join-storm detectado), Kigo simplemente no lo manda. No hay sanción por esto.

## Invitar a varios servidores a la vez

Puedes añadir Kigo a tantos servidores como quieras con el mismo enlace. Si gestionas varios, no hace falta repetir el proceso: simplemente vuelve a abrir el enlace, elige otro servidor y autoriza.

## Quitar a Kigo

Si en algún momento quieres dejar de usar Kigo:

1. Ve a `Configuración del servidor > Integraciones`
2. Busca "Kigo" en la lista
3. Pulsa "Quitar"

Kigo **no borra automáticamente** la configuración de tu servidor al salir. Si Kigo vuelve a entrar, la recuperará. Si quieres que la borre, ejecuta `/configuración` y desactiva los módulos uno a uno antes de expulsar al bot.

## Siguiente paso

[Configura el bot por primera vez →](primer-uso.md)
