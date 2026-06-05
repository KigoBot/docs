# Silenciar a un usuario

Impide que un usuario escriba en cualquier canal del servidor durante un tiempo determinado. Discord lo llama "timeout".

## Cuándo usarlo

- El usuario está discutiendo acaloradamente y quieres que se calme.
- El usuario spamea y quieres frenarlo sin echarlo.
- El usuario infringe normas leves y quieres una sanción que no sea permanente.

Para infracciones graves, usa `/ban` directamente.

## Requisitos

- Tu rol debe tener permiso de **Expulsar miembros temporalmente** (también llamado "Moderar miembros").
- Kigo debe tener el mismo permiso.
- El usuario debe ser miembro actual del servidor.

## Cómo usarlo

1. Escribe `/mute`.
2. Selecciona el usuario.
3. (Opcional) Escribe el tiempo. Por defecto 15 minutos. Formatos aceptados: `15m`, `1h`, `7d`, `2w` (semanas), etc.
4. (Opcional) Escribe una razón.
5. Pulsa Enter.

Kigo silencia al usuario, te responde con un mensaje efímero confirmando, y registra en logs.

## Tiempos disponibles

Discord permite silenciar entre 1 minuto y 4 semanas. Kigo acepta todos los formatos legibles:

- `15m` = 15 minutos
- `1h` = 1 hora
- `2h30m` = 2 horas y 30 minutos
- `7d` = 7 días
- `2w` = 2 semanas (máximo)

Si escribes algo no válido, Kigo te avisará con un ejemplo de formato correcto.

## Qué ve el usuario silenciado

Mientras esté silenciado, el usuario:

- **Puede leer** todos los canales (a menos que no tuviera acceso por otros motivos).
- **No puede escribir** en ningún canal.
- **No puede reaccionar** a mensajes.
- **No puede hablar** en canales de voz.
- **No puede usar comandos** de barra.
- **Sí puede** ver mensajes, entrar a canales de voz para escuchar, y usar funciones que no requieren escribir.

## Quitar el silencio

Para desilenciar antes de que expire el tiempo:

1. Usa el comando `/unmute` con el usuario.
2. O ve a `Configuración del servidor > Tiempos de espera` y quítalo manualmente.

El usuario recuperará todos los permisos inmediatamente.

## Lo que NO hace

- **No es un ban.** El usuario sigue siendo miembro del servidor y puede leer todo.
- **No se acumula.** Si silencias a alguien 3 veces en una semana, sigue siendo 3 silencios independientes, no una semana de silencio.
- **No afecta a bots.** Los bots tienen su propio sistema de permisos y los silencios no siempre funcionan con ellos.

## Sanciones progresivas

Un patrón común es escalar:

1. Primera falta leve: `/mute 15m` + razón.
2. Segunda falta: `/mute 1h` + razón.
3. Tercera falta: `/mute 24h` + razón.
4. Cuarta falta: `/kick` + razón.
5. Quinta falta: `/ban` + razón.

Este patrón funciona bien para usuarios que reinciden pero no hacen nada gravísimo.

## Problemas frecuentes

**"El usuario puede seguir escribiendo"** — Puede que tenga un rol con permisos especiales que ignore el silencio. O que sea un bot (los silencios no afectan a algunos bots).

**"Quito el silencio pero sigue silenciado"** — Espera unos segundos. Discord puede tardar en propagar el cambio.

**"El formato de tiempo no funciona"** — Kigo usa la librería `ms`. Formatos válidos: `1s`, `5m`, `2h`, `1d`, `2w`. No acepta `1 día` con espacios, ni `mañana`, ni cosas ambiguas.

## Siguiente paso

[Aprende a borrar mensajes →](borrar-mensajes.md), el comando que más vas a usar en el día a día.
