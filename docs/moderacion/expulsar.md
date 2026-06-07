# Expulsar a un usuario

Echa a un usuario del servidor. A diferencia del ban, el usuario puede volver si alguien le pasa una nueva invitación.

## Cuándo usarlo

- El usuario incumplió normas pero la falta no es tan grave como para banearlo.
- Quieres dar una "señal de aviso" pública.
- Estás testeando los permisos y quieres asegurarte de que `/kick` funciona.

Para faltas graves o reincidentes, usa `/ban` directamente.

## Requisitos

- Tu rol debe tener permiso de **Expulsar miembros**.
- Kigo debe tener permiso de **Expulsar miembros** en el servidor.
- El usuario a expulsar debe ser miembro actual del servidor.

## Cómo usarlo

1. Escribe `/kick`.
2. Selecciona el usuario de la lista.
3. (Opcional) Escribe una razón.
4. Pulsa Enter.

Kigo ejecuta el kick, te responde con un mensaje efímero confirmando, y registra la acción en el canal de logs.

## Diferencia con ban

| | Kick | Ban |
|---|---|---|
| ¿El usuario puede volver? | Sí, con nueva invitación | No (salvo desban manual) |
| ¿Aparece en auditoría? | Sí | Sí |
| ¿Mensajes anteriores? | Se mantienen | Se mantienen |
| ¿Cuándo usarlo? | Faltas leves o moderadas | Faltas graves o reincidencia |

## DM al expulsado

Igual que con `/ban`, Kigo **no envía DM** automático al expulsado. Si quieres comunicarle el motivo, hazlo manualmente antes o después.

## Limitaciones de jerarquía

Mismas reglas que con ban: no puedes kickear a alguien con un rol más alto que el tuyo, salvo que seas el owner.

## Lo que NO hace

- **No banea al usuario.** Solo lo echa. Si tiene una invitación, puede volver.
- **No borra mensajes** del usuario expulsado.
- **No aplica ningún efecto permanente.**

## Problemas frecuentes

**"El usuario vuelve a entrar después de ser kickeado"** — `/kick` no es permanente. Si el usuario vuelve con malas intenciones, usa `/ban` o el filtro de multicuentas.

**"Kigo dice que no tiene permisos"** — Revisa que el rol de Kigo tenga "Expulsar miembros" activado.

## Siguiente paso

[Aprende a silenciar →](silenciar.md), útil cuando quieres que alguien se calme sin echarlo del servidor.
