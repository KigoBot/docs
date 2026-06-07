# Bloquear un canal

Impide que los miembros normales escriban en un canal. Los roles con permisos especiales (mod, admin) siguen pudiendo escribir.

## Cuándo usarlo

- Un tema caliente se descontroló y quieres que el canal se enfríe.
- Estás haciendo mantenimiento del canal y no quieres que los usuarios escriban mientras.
- Acabas de anunciar algo delicado y quieres evitar respuestas durante un rato.
- Spam masivo en un canal específico.

## Requisitos

- Tu rol debe tener permiso de **Gestionar canales**.
- Kigo debe tener permiso de **Gestionar canales** en el servidor.

## Cómo usarlo

1. Ve al canal que quieres bloquear.
2. Escribe `/lock`.
3. (Opcional) Escribe una razón.
4. Pulsa Enter.

Kigo modifica los permisos del canal para que `@everyone` no pueda enviar mensajes. Te responde con un mensaje efímero confirmando.

## Qué pasa al bloquear

Al bloquear un canal:

- Los usuarios sin roles especiales ven el canal pero no pueden escribir.
- Los mensajes anteriores siguen visibles.
- Los usuarios con roles que tengan permiso de "Enviar mensajes" explícito (típicamente mods y admins) sí pueden escribir.
- Los bots que tenían permiso explícito siguen pudiendo escribir.

## Desbloquear

Para desbloquear:

1. Ve al canal bloqueado.
2. Escribe `/unlock`.
3. Kigo restaura los permisos normales.

También puedes ir a `Configuración del canal > Permisos > @everyone > Enviar mensajes` y activarlo manualmente.

## Diferencia con slowmode, hide y nuke

- **Slowmode** (`/slow-mode`): los usuarios pueden seguir escribiendo, pero tienen que esperar X segundos entre mensajes.
- **Lock** (`/lock`): los usuarios no pueden escribir nada, pero el canal sigue visible.
- **Hide** (`/hide`): el canal deja de ser visible para `@everyone`. Ver [Ocultar canal](hide.md).
- **Show** (`/show`): revierte un `/hide`. Ver [Mostrar canal](show.md).
- **Nuke** (`/nuke`): se borra el canal y se clona (se "reinicia"). Acción drástica. Ver [Nuke](nuke.md).

Usa lock para pausas temporales, slowmode para mantener conversación pero frenada, hide para privatizar el canal, y nuke solo cuando el canal está tan roto que no se puede recuperar.

## Para quién es visible

El canal bloqueado sigue siendo visible para los usuarios (pueden leer mensajes antiguos). Solo se quita el permiso de escribir.

Si quieres ocultarlo completamente, usa [`/hide`](hide.md) en su lugar.

## Lo que NO hace

- **No borra mensajes.** Solo impide nuevos.
- **No notifica a los usuarios** que el canal está bloqueado. Si quieres avisar, manda un mensaje de "este canal está temporalmente bloqueado por [razón]".
- **No afecta a mensajes directos.** Solo al canal específico.
- **No expira solo.** Tienes que desbloquearlo manualmente.

## Caso típico: tema polémico

1. Alguien publica un tema que se caldea rápido.
2. Escribes `/lock [razón: tema polémico]` y un mensaje de "este canal se ha bloqueado temporalmente para evitar escalada".
3. Pasado un rato, `/unlock` cuando la situación se calme.

## Problemas frecuentes

**"Kigo dice que no tiene permisos"** — Kigo necesita "Gestionar canales" en su rol. Revisa.

**"El lock no funciona en un canal privado"** — Si el canal es privado (con permisos restrictivos desde el inicio), el lock podría no tener efecto. Usa permisos manuales.

**"Los mods tampoco pueden escribir"** — Si tu rol de mod no tiene "Enviar mensajes" explícito en ese canal, Kigo no te lo añadirá. Tendrías que hacerlo manualmente.

## Siguiente paso

[Aprende a configurar el modo lento →](slowmode.md), una alternativa más suave al bloqueo.
