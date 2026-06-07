# Ocultar un canal (`/hide`)

Quita el permiso de "Ver canal" al rol `@everyone` en el canal donde se ejecuta el comando. El canal deja de ser visible para los miembros que no tengan un rol con permiso explícito de verlo.

## Cuándo usarlo

- Un evento ha terminado y quieres ocultar el canal asociado.
- Quieres privatizar un canal de uso temporal (sorteos, eventos, etc.) sin tener que crear uno nuevo.
- Estás reorganizando el servidor y necesitas que un canal deje de ser público.

## Requisitos

- Tu rol debe tener permiso de **Gestionar canales**.
- Kigo debe tener permiso de **Gestionar canales** en el servidor.

## Cómo usarlo

1. Ve al canal que quieres ocultar.
2. Escribe `/hide`.
3. (Opcional) Escribe una **razón** (queda en los logs de auditoría de Discord).
4. Pulsa Enter.

Kigo modifica los permisos del canal: `@everyone` ya no puede verlo. Te responde con un mensaje efímero confirmando.

## Quién sigue viendo el canal

- Roles con permiso explícito de "Ver canal" en ese canal (mods, admins, etc.).
- El propio bot (necesario para responder a los mods que escriban dentro).
- Tened en cuenta: si ningún mod tiene "Ver canal" explícito en el canal, tampoco lo verán. Tendrán que añadirse el permiso a mano.

## Revertir la ocultación

Usa [`/show`](show.md) en el mismo canal. Kigo restaura el permiso de "Ver canal" a `@everyone` a su estado por defecto.

## Diferencia con `/lock`

- **`/lock`**: los usuarios pueden ver el canal pero no escribir.
- **`/hide`**: los usuarios no pueden ver el canal (sigue existiendo, pero no aparece en su lista).

## Lo que NO hace

- **No borra mensajes.**
- **No afecta a los permisos de roles específicos** que ya tuvieran "Ver canal" activado. Si quieres, gestiona esos permisos a mano.

## Problemas frecuentes

**"Kigo dice que no tiene permisos"** — Kigo necesita "Gestionar canales" en su rol. Revísalo.

**"El canal sigue siendo visible para algunos"** — Esos usuarios probablemente tienen un rol con permiso explícito de "Ver canal" en ese canal. Kigo no toca permisos de roles específicos.

## Siguiente paso

[Mostrar de nuevo con `/show` →](show.md) o [vuelve al índice de moderación →](index.md).
