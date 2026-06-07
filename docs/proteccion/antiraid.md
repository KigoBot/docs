# Anti-raid

Detecta acciones masivas sospechosas y las revierte. Es el módulo más importante si tu servidor es público.

## Qué protege exactamente

El anti-raid vigila estos eventos. Cada uno tiene un interruptor independiente en `/configuración` → **Protección**:

**Protección de Canales (crear, eliminar, actualizar)** — Detecta cuando alguien crea, borra o actualiza muchos canales en poco tiempo. El umbral por defecto es de 3 acciones en la ventana configurada (entre 1 y 10).

**Protección de Roles (crear, eliminar, actualizar)** — Igual, pero con roles. Mismo umbral configurable.

**Prevenir Bots** — Decide qué bots pueden entrar al servidor. Tres modos: Solo Verificados (los marcados por Discord), Solo No Verificados, o Todos.

**Multicuentas** — Si una cuenta tiene menos de X días de antigüedad (por defecto 15, configurable entre 1 y 25), se le expulsa directamente al unirse.

**Ban / Expulsión (sanciones masivas)** — Detecta si un miembro está ejecutando muchos bans o expulsiones en poco tiempo (umbral configurable, por defecto 3).

**Actualizar Servidor** — Detecta cambios sospechosos al servidor (nombre, icono, verificación, etc.).

## Los niveles de protección

El asistente de configuración inicial (`/setup`, paso 6) ofrece cuatro niveles preconfigurados. Más alto = más estricto. Una vez elegido, puedes ajustar cada protección por separado en `/configuración`.

![Niveles de anti-raid](images/antiraid-niveles.png) — _pendiente de captura real_

**Nulo (0%)** — Ninguna protección activada. Útil solo si quieres empezar desde cero y configurar a mano.

**Simple (25%)** — Anti-raid básico: protección de canales, roles y filtro de bots no verificados.

**Básico (50%)** — Lo anterior + Auto Moderación (las 5 reglas de automod: `everyone`, `discord_links`, `webs_links`, `ghostping`, `spam`).

**Extremo (100%)** — Todo lo anterior + filtro de multicuentas, sanciones masivas (ban/kick) y actualización del servidor.

Si tu servidor es nuevo o pequeño, empieza con Simple o Básico. Solo sube a Extremo si tienes un problema recurrente de raids o multicuentas.

## Cuándo se activa

El anti-raid solo reacciona. No hace análisis en segundo plano de "este usuario parece sospechoso". Espera a que ocurra algo y luego decide si fue legítimo o no.

Esto significa que **no hay falsos positivos por sí solo** — un admin que crea 3 canales legítimamente no activará el raid a menos que sean duplicados obvios (mismo nombre).

## Lo que ve el atacante

Si alguien intenta un raid, en cuestión de segundos:

1. Sus canales y roles desaparecen (si aplica)
2. Es baneado o expulsado (según la sanción configurada)
3. En el canal de logs aparece un embed con todos los detalles (quién, cuándo, qué)

## Cómo configurarlo

Ve a `/configuración` y entra en la sección de **Protección**. Verás un menú con el nivel preconfigurado. Puedes cambiar de nivel con un select-menu o ajustar cada protección por separado:

- **Canales:** Crear / Eliminar / Actualizar + límite global (1-10)
- **Roles:** Crear / Eliminar / Actualizar + límite global (1-10)
- **Bots & Multicuentas:** política de bots admitidos + días mínimos de cuenta
- **Sanciones:** Ban / Expulsión / Actualizar Servidor + límite global (1-10)

Los niveles se aplican de forma acumulativa: activar el nivel 3 incluye todo lo del nivel 2 y del nivel 1.

## Qué NO hace

- **No previene raids antes de que pasen.** Solo reacciona. Si alguien entra y banea a 50 personas en 10 segundos, Kigo no lo va a evitar, pero sí alertará al resto del staff.
- **No detecta "slow raids"** (5 cuentas entrando cada día durante un mes). Para eso necesitas automod y sentido común.
- **No distingue automáticamente** entre un admin legítimo y un admin comprometido. Por eso el nivel Extremo es paranoico: asume que cualquier admin puede estar comprometido.

## Combinado con whitelist

Cualquier usuario, rol o canal en la lista blanca está exento del anti-raid. Esto es importante para:

- **Tu staff**: para que no se active la protección cuando un admin reorganiza el servidor.
- **Bots legítimos**: bots de música, de logs, etc. que crean sus propios canales.
- **Categorías específicas**: si tienes un canal donde se experimenta con bots, exénta la categoría entera.

## Siguiente paso

[Aprende cómo configurar el automod →](automod.md), que protege de mensajes sueltos (no de acciones masivas).
