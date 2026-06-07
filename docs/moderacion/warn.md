# Warn

`/warn` añade una advertencia formal a un usuario. Cada warn queda registrado en el historial del servidor y puede activar el Castigo Progresivo si tienes premium.

## Requisitos

- Permiso **Moderar miembros** en tu rol.
- Que el bot tenga permiso **Moderar miembros**.
- Que el target no sea el owner del servidor.
- Que el target no sea el propio bot.

## Uso

```
/warn usuario:@usuario razón:"texto" severidad:1 contexto:<link>
```

### Opciones

- **usuario** (requerido) — el miembro a advertir. Tiene que estar en el servidor.
- **razón** (requerido) — el motivo. Hasta 500 caracteres.
- **severidad** (opcional) — 1, 2 o 3. Por defecto 1.
- **contexto** (opcional) — URL de evidencia (un mensaje, una captura, etc.). Sirve para que el caso sea trazable.

### Severidades

| Nivel | Cuándo usarlo | Efecto |
|---|---|---|
| **1 - Leve** | Spam, mensajes fuera de tono, incumplimiento leve de normas. | Warn normal. |
| **2 - Media** | Insultos, contenido no permitido, incumplimiento reiterado. | Warn con peso medio para el Castigo Progresivo. |
| **3 - Alta** | Acoso, amenazas, contenido gravemente prohibido. | Warn con peso alto. El Castigo Progresivo puede saltar antes. |

## Qué pasa cuando ejecutas el comando

1. Se crea un caso en el historial con un número incremental (`#1`, `#2`, ...).
2. El bot intenta mandar un DM al usuario con la advertencia (si tiene DMs abiertos y la config `notifyUser` está activa).
3. Si tienes **Castigo Progresivo** configurado y el nuevo warn cruza un umbral (3, 5, 7 warns...), el bot aplica la sanción automáticamente (mute, kick o ban según la regla).
4. Se manda un embed al canal de logs.

![Ejemplo de respuesta de /warn](images/warn-respuesta.png) — *pendiente de captura real*

## Si tienes Castigo Progresivo

El Castigo Progresivo es una función **premium** que se configura en `/configuración` → Premium → Castigo Progresivo. Cuando activas premium en el servidor, se crean 3 reglas por defecto:

- 3 warns → mute 1 hora
- 5 warns → mute 1 día
- 7 warns → kick

Estas reglas se pueden editar (cambiar umbrales, acciones, duraciones) o añadir más.

Si el nuevo warn cruza uno de esos umbrales, el bot ejecuta la sanción automáticamente y crea un caso adicional (`#caso_id: mute`, `#caso_id: kick`, etc.) en el historial.

## Ver los warns de un usuario

- `/warns usuario:@usuario` — lista los warns activos (no expirados) del usuario.
- `/case id:<número>` — muestra el detalle de un caso concreto.
- `/modlogs usuario:@usuario` — historial completo de casos (warns, mutes, kicks, bans).

## Quitar un warn

```
/unwarn id:<número_de_caso>
```

Esto marca el warn como expirado (no se borra, queda en el historial con flag de expirado) y crea un nuevo caso `unwarn` enlazado.

## Expiración automática

Los warns expiran automáticamente. El número de días es configurable en `/configuración` → Premium → Castigo Progresivo → Expiración (por defecto 60 días). Un warn expirado:

- No cuenta para el Castigo Progresivo.
- Sigue visible en `/modlogs` (con flag de expirado).
- No se puede "revivir".

## Siguiente paso

Si quieres ver los warns de un usuario concreto, usa `/warns usuario:@usuario`. Para ver todo el historial, `/modlogs`.
