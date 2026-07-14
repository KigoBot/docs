# Cambiar de owner del servidor

Discord permite transferir la propiedad de un servidor a otro miembro. Kigo no se ve afectado por esto, pero hay algunas cosas que saber.

## Lo que sigue funcionando

- **Toda la configuración de Kigo** (anti-raid, automod, verificación, whitelist).
- **El premium activo**, si lo tienes.
- **Los logs** y todo el historial.
- **Los bans, mutes, etc.** que Kigo haya aplicado.

## Lo que cambia

- **Comandos que requieren ser owner.** El nuevo owner podrá usar `/configuración`, `/setup`, `/eliminar-raid`, etc.
- **El anterior owner pierde esos permisos.** Ya no podrá usar los comandos restringidos a owner.

## Cómo transferir la propiedad

Esto se hace desde Discord, no desde Kigo:

1. **Como owner actual**: ve a `Configuración del servidor > Miembros`.
2. Busca al miembro al que quieres transferir.
3. Click en los tres puntos al lado de su nombre.
4. Selecciona `Transferir propiedad del servidor`.
5. Confirma con tu token de autenticación 2FA (es obligatorio).

Discord transfiere el servidor. El nuevo owner recibe una notificación y el rol de owner.

## Riesgos

- **No hay vuelta atrás simple.** Una vez transferido, el nuevo owner debe transferirlo de vuelta si quiere.
- **El antiguo owner ya no puede deshacer cambios.** Si el nuevo owner hace algo mal, el antiguo owner no puede revertirlo directamente.
- **Si el nuevo owner es malicioso**, puede expulsar al antiguo, banear a todos, etc. Ten mucho cuidado con quién recibe tu servidor.

## Recomendaciones antes de transferir

- **Comunica claramente al nuevo owner** qué hace Kigo y dónde está la configuración.
- **Exporta un backup** de Kigo y guárdalo en un lugar al que ambos tengan acceso.
- **Pide al nuevo owner que verifique la configuración** después de la transferencia.

## Si el nuevo owner necesita ayuda

Que abra un ticket en el [servidor de soporte](https://discord.gg/wmky5nBRR2) indicando que es nuevo owner. El autor puede guiarle en la configuración inicial.

## Casos especiales

**Transferir a un bot.** No se puede. Discord no permite transferir la propiedad a un bot (los bots no pueden ser owners).

**Servidores de comunidad / verificados.** Si tu servidor está verificado por Discord (tiene el badge de partner o de comunidad), el proceso de transferencia puede requerir pasos adicionales. Revisa la [documentación oficial de Discord](https://discord.com/blog/your-server-your-rules).

## Siguiente paso

Volver al [índice de problemas](index.md) o al [inicio de la documentación](../index.md).
