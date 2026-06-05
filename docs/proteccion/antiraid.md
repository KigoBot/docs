# Anti-raid

Detecta acciones masivas sospechosas y las revierte. Es el módulo más importante si tu servidor es público.

## Qué protege exactamente

El anti-raid vigila estos eventos:

**Creación masiva de canales** — Si en pocos segundos alguien crea 3 o más canales, se considera raid. Kigo borra los canales duplicados y banea al autor.

**Creación masiva de roles** — Igual, pero con roles. Si alguien crea 3+ roles con nombres parecidos en poco tiempo, se borran y se banea al autor.

**Baneos coordinados** — Si un admin legítimo empieza a banear a muchos usuarios "sospechosos" sin ton ni son (lo que pasa cuando le roban la cuenta a un admin), Kigo detecta el patrón y avisa a otro admin o revierte la acción.

**Multicuentas** — Si varias cuentas nuevas (mismo rango de fecha de creación) entran y empiezan a hacer lo mismo, se marcan como raid y se expulsan juntas.

**Cambios sospechosos al servidor** — Nombre del servidor, icono, nivel de verificación, filtro de contenido explícito. Si alguien cambia cosas de golpe, se asume compromiso de cuenta.

## Los niveles de protección

El asistente de configuración inicial (`/setup`) ofrece cuatro niveles preconfigurados. Más alto = más estricto. Una vez elegido, puedes ajustar cada protección por separado en `/configuración`.

**Nulo (0%)** — Ninguna protección activada. Útil solo si quieres empezar desde cero y configurar a mano.

**Simple (25%)** — Anti-raid básico: detección de creación masiva de canales, roles, y baneos de bots no verificados.

**Básico (50%)** — Lo anterior + automod (filtros de mensajes, menciones masivas, enlaces peligrosos, spam).

**Extremo (100%)** — Todo lo anterior + filtro de multicuentas, detección de baneos coordinados y detección de cambios sospechosos al servidor (nombre, icono, verificación).

Si tu servidor es nuevo o pequeño, empieza con Simple o Básico. Solo sube a Extremo si tienes un problema recurrente de raids o multicuentas.

## Cuándo se activa

El anti-raid solo reacciona. No hace análisis en segundo plano de "este usuario parece sospechoso". Espera a que ocurra algo y luego decide si fue legítimo o no.

Esto significa que **no hay falsos positivos por sí solo** — un admin que crea 3 canales legítimamente no activará el raid a menos que sean duplicados obvios (mismo nombre).

## Lo que ve el atacante

Si alguien intenta un raid, en cuestión de segundos:

1. Sus canales y roles desaparecen
2. Es baneado
3. En el canal de logs aparece un embed con todos los detalles (quién, cuándo, qué)
4. Si el raid fue coordinado, las cuentas relacionadas también son baneadas

## Cómo configurarlo

Ve a `/configuración` y entra en la sección de **Protección**. Verás un menú con 4 niveles. Elige el que más se ajuste a tu servidor.

Los niveles se aplican de forma acumulativa: activar el nivel 3 incluye todo lo del nivel 2 y del nivel 1.

## Qué NO hace

- **No previene raids antes de que pasen.** Solo reacciona. Si alguien entra y banea a 50 personas en 10 segundos, Kigo no lo va a evitar, pero sí alertará al resto del staff.
- **No detecta "slow raids"** (5 cuentas entrando cada día durante un mes). Para eso necesitas automod y sentido común.
- **No distingue automáticamente** entre un admin legítimo y un admin comprometido. Por eso el nivel 4 es paranoico: asume que cualquier admin puede estar comprometido.

## Combinado con whitelist

Cualquier usuario, rol o canal en la lista blanca está exento del anti-raid. Esto es importante para:

- **Tu staff**: para que no se active la protección cuando un admin reorganiza el servidor.
- **Bots legítimos**: bots de música, de logs, etc. que crean sus propios canales.
- **Categorías específicas**: si tienes un canal donde se experimenta con bots, exénta la categoría entera.

## Siguiente paso

[Aprende cómo configurar el automod →](automod.md), que protege de mensajes sueltos (no de acciones masivas).
