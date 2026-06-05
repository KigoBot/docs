# Configurar el modo lento

Obliga a los usuarios a esperar X segundos entre mensajes en un canal. La mitad de estricto entre "todo normal" y "bloqueado".

## Cuándo usarlo

- Un canal tiene demasiado tráfico y quieres que se calme.
- Quieres evitar que alguien flood de mensajes, sin llegar a bloquear.
- Estás moderando un debate acalorado y quieres que la gente piense antes de responder.
- Tu servidor es muy activo y el spam de短线 es un problema.

## Requisitos

- Tu rol debe tener permiso de **Gestionar canales**.
- Kigo debe tener permiso de **Gestionar canales** en el servidor.

## Cómo usarlo

1. Ve al canal donde quieres aplicar el slowmode.
2. Escribe `/slow-mode`.
3. Escribe los segundos de espera (entre 0 y 21600 = 6 horas).
4. Pulsa Enter.

Kigo aplica el slowmode al canal. Te responde con un mensaje efímero confirmando.

## Valores recomendados

- **0 segundos**: desactiva el slowmode.
- **5-10 segundos**: para canales de debate o generales activos. Apenas se nota en conversación normal, pero frena el spam.
- **30-60 segundos**: para canales donde quieres calidad sobre cantidad.
- **5+ minutos**: para canales de anuncios o de soporte, donde las respuestas no son urgentes.
- **6 horas (máximo)**: para canales de bots o logs.

## Cómo se ve para el usuario

Si el usuario intenta escribir dentro del tiempo de slowmode, Discord le muestra un mensaje como "estás en modo lento, espera X segundos". El contador se ve en la barra de mensaje.

El usuario puede ver el tiempo restante pasando el ratón por el icono de reloj.

## Excepciones

**Mods y admins** no se ven afectados por el slowmode (a menos que les pongas el slowmode explícitamente, que Discord no permite). El slowmode es solo para `@everyone`.

**Bots** también respetan el slowmode por defecto. Si tienes un bot que necesita postear más rápido, dale un rol con permiso de "Gestionar mensajes" o "Administrador" (esto es un workaround, no ideal).

## Diferencia con lock

- **Slowmode** (`/slow-mode`): los usuarios pueden seguir escribiendo, pero con espera entre mensajes.
- **Lock** (`/lock`): los usuarios no pueden escribir nada.

Slowmode es más suave. Si quieres que el canal siga activo pero frenado, usa slowmode. Si quieres silencio total, usa lock.

## Desactivar

Para quitar el slowmode:

1. Escribe `/slow-mode 0` en el canal.
2. Kigo aplica 0 segundos de espera, lo que equivale a desactivarlo.

O ve a `Configuración del canal > Modo lento` y ponlo a 0 manualmente.

## Caso de uso típico: debate en #general

1. El canal #general tiene mucho debate últimamente.
2. Escribes `/slow-mode 30` (30 segundos entre mensajes).
3. Los usuarios siguen pudiendo hablar, pero tienen que pensar antes de responder.
4. Cuando la situación se calme, `/slow-mode 0` para volver a la normalidad.

## Lo que NO hace

- **No afecta a otros canales.** Solo al actual.
- **No se acumula.** Si un usuario escribe 5 mensajes en 30 segundos, no se le "debe" tiempo: simplemente el siguiente mensaje se retrasa otros 30 segundos desde el último.
- **No se aplica a mensajes directos.** Solo al canal.

## Problemas frecuentes

**"Kigo dice que el número no es válido"** — El slowmode máximo es 21600 segundos (6 horas). El mínimo es 0.

**"Los mods también están afectados"** — No debería. Si los mods están afectados, probablemente no tienen "Gestionar canales" o "Administrador" en su rol. Revisa.

**"Un bot está spameando"** — El slowmode se aplica a todos. Si un bot necesita postear más rápido, dale un rol con permisos especiales o desactívalo temporalmente.

## Siguiente paso

Has visto los comandos básicos de moderación. Si quieres más detalle sobre un comando específico, vuelve al [índice de moderación](index.md). Si tienes un problema concreto, [problemas frecuentes](../problemas/index.md) tiene respuestas rápidas.
