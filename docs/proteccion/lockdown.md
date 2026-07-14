# Lockdown (bloqueo de emergencia)

El lockdown es un mecanismo de bloqueo total del servidor que se activa automáticamente cuando el anti-raid detecta un ataque en curso, o manualmente desde la configuración.

## Qué hace

Cuando el lockdown está activo:

- **@everyone** pierde permiso de enviar mensajes en todos los canales de texto.
- Los roles con permiso de `Gestionar canales` (staff, admin) siguen pudiendo escribir.
- El canal de logs registra la activación y desactivación con un embed.
- Los canales existentes no se modifican permanentemente: al desactivar el lockdown, los permisos vuelven a su estado anterior.

## Cuándo se activa

### Automático (recomendado)

El lockdown se activa automáticamente cuando el anti-raid banea a un atacante. Esto evita que otros miembros del raid sigan escribiendo mientras el bot procesa las sanciones.

### Manual

Desde el panel de configuración (`/configuración` → **Protección** → **Lockdown**) puedes:

- **Activar lockdown**: bloquea el servidor al instante.
- **Desactivar lockdown**: restaura los permisos normales.
- **Activar/desactivar lockdown automático**: decide si el anti-raid activa el lockdown al banear.

## Qué ve el servidor

Cuando se activa el lockdown:

1. Todos los miembros no-staff ven que ya no pueden enviar mensajes en ningún canal.
2. En el canal de logs aparece un embed: `🔒 Lockdown activado` con la hora y quién lo activó.
3. Al desactivar, aparece otro embed: `🔓 Lockdown desactivado`.

El lockdown no es silencioso: el canal de logs deja constancia de cada activación y desactivación.

## Consideraciones

- El lockdown no afecta canales de voz, solo canales de texto.
- Los mensajes en curso no se pierden: los miembros dejan de poder escribir, pero los mensajes ya enviados permanecen.
- Si tienes canales que deben permanecer accesibles durante un lockdown (ej. canal de anuncios), añade los roles de staff a la whitelist.
- El lockdown se desactiva automáticamente al reiniciar el bot (el estado se guarda en Redis y se restaura al reconectar).

## Siguiente paso

Vuelve a [la visión general de anti-raid](antiraid.md) para ver cómo se complementa con las demás protecciones.
