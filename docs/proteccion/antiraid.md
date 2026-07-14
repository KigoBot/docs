# Anti-raid

Detecta acciones masivas sospechosas y las revierte automáticamente. Es el módulo más importante si tu servidor es público.

## Qué protege exactamente

El anti-raid vigila estos eventos. Cada uno tiene su propio interruptor y límite configurable en `/configuración` → **Protección**:

**Canales (crear, eliminar, actualizar)** — Detecta cuando alguien crea, borra o modifica muchos canales en poco tiempo. Cada tipo (crear/eliminar/actualizar) tiene su propio límite.

**Roles (crear, eliminar, actualizar)** — Lo mismo, pero con roles. Límite independiente por tipo de acción.

**Webhooks (crear)** — Detecta creación masiva de webhooks, una técnica usada para inyectar mensajes maliciosos.

**Prevenir Bots** — Decide qué bots pueden entrar al servidor. Tres modos: Solo Verificados (los marcados por Discord), Solo No Verificados, o Todos.

**Multicuentas** — Si una cuenta tiene menos de X días de antigüedad (por defecto 15, configurable entre 1 y 25), se le expulsa directamente al unirse.

**Ban / Expulsión (sanciones masivas)** — Detecta si un miembro está ejecutando muchos bans o expulsiones en poco tiempo. Límite configurable.

**Actualizar Servidor** — Detecta cambios sospechosos a la configuración del servidor (nombre, icono, nivel de verificación, etc.).

**Antievasión** — Detecta cuando un usuario baneado o expulsado vuelve con otra cuenta y sigue causando problemas.

## Lockdown (bloqueo de emergencia)

Cuando el anti-raid detecta un ataque en curso, puede activar automáticamente el **Lockdown**: un bloqueo total del servidor que impide escribir a todos los miembros no staff.

Durante un lockdown:

- **@everyone** pierde permiso de enviar mensajes en todos los canales de texto.
- Solo los roles con permisos de gestión de canales pueden seguir escribiendo.
- El canal de logs registra la activación y desactivación.

El lockdown se activa automáticamente al banear a un atacante por anti-raid. También se puede activar y desactivar manualmente desde el panel de configuración.

## Los niveles de protección

El asistente de configuración inicial (`/setup`, paso 6) ofrece cuatro niveles preconfigurados. Más alto = más estricto. Una vez elegido, puedes ajustar cada protección por separado en `/configuración`.

**Nulo (0%)** — Ninguna protección activada. Útil solo si quieres empezar desde cero y configurar a mano.

**Simple (25%)** — Anti-raid básico: protección de canales, roles y filtro de bots no verificados.

**Básico (50%)** — Lo anterior + Auto Moderación (las 5 reglas de automod: `everyone`, `discord_links`, `webs_links`, `ghostping`, `spam`).

**Extremo (100%)** — Todo lo anterior + filtro de multicuentas, sanciones masivas (ban/kick), webhooks, antievasión, actualización del servidor y lockdown automático.

Si tu servidor es nuevo o pequeño, empieza con Simple o Básico. Solo sube a Extremo si tienes un problema recurrente de raids o multicuentas.

## Cuándo se activa

El anti-raid solo reacciona. No hace análisis en segundo plano. Espera a que ocurra algo y luego decide si fue legítimo o no basándose en los límites que configuraste.

Cada acción tiene su propio **límite por ventana de tiempo** (por defecto 3 acciones en 10 segundos). Si un usuario supera ese límite, el anti-raid considera que es un ataque.

## Lo que ve el atacante

Si alguien intenta un raid, en cuestión de segundos:

1. Sus canales y roles desaparecen (si aplica)
2. El servidor entra en lockdown — nadie más puede escribir
3. Es baneado o expulsado (según la sanción configurada)
4. En el canal de logs aparece un embed con todos los detalles (quién, cuándo, qué)

## Cómo configurarlo

Ve a `/configuración` y entra en la sección de **Protección**. Verás un menú con el nivel preconfigurado. Puedes cambiar de nivel con un select-menu o ajustar cada protección por separado:

- **Canales:** Crear / Eliminar / Actualizar + límite por acción (1-10)
- **Roles:** Crear / Eliminar / Actualizar + límite por acción (1-10)
- **Webhooks:** límite de creación (1-10)
- **Bots & Multicuentas:** política de bots admitidos + días mínimos de cuenta
- **Sanciones:** Ban / Expulsión + límite (1-10)
- **Servidor:** Actualizar servidor (on/off)
- **Antievasión:** detectar reincidentes (on/off)
- **Lockdown automático:** activar bloqueo al detectar raid (on/off)

Cada protección tiene su propio límite. No hay un solo "límite global" para todo.

## Qué NO hace

- **No previene raids antes de que pasen.** Solo reacciona. Si alguien entra y banea a 50 personas en 10 segundos, Kigo no lo va a evitar, pero activará el lockdown y alertará al staff.
- **No detecta "slow raids"** (5 cuentas entrando cada día durante un mes). Para eso necesitas automod y sentido común.
- **No distingue automáticamente** entre un admin legítimo y un admin comprometido. Por eso el nivel Extremo es paranoico: asume que cualquier admin puede estar comprometido.

## Combinado con whitelist

Cualquier usuario, rol o canal en la lista blanca está exento del anti-raid y del lockdown. Esto es importante para:

- **Tu staff**: para que no se active la protección cuando un admin reorganiza el servidor.
- **Bots legítimos**: bots de música, de logs, etc. que crean sus propios canales.
- **Categorías específicas**: si tienes un canal donde se experimenta con bots, exénta la categoría entera.

## Siguiente paso

[Aprende cómo configurar el automod →](automod.md), que protege de mensajes sueltos (no de acciones masivas).
