# Canjear un código de premium

Si tienes un código de Kigo Premium (los publica el autor en eventos, sorteos o colaboraciones), esta es la forma de activarlo.

!!! info "Si pagaste con Whop, no necesitas esto"
    Cuando pagas en whop.com y completas el checkout con tu ID de Discord, el premium se activa automáticamente. No necesitas canjear ningún código. El bot te manda un DM de bienvenida en cuanto se confirma el pago.

## Requisitos

- Tener un código válido (formato `FREE-XXXX...`).
- Estar en un servidor donde Kigo esté añadido.
- No tener ya premium activo (si ya tienes premium, el bot te avisa y no te deja canjear otro código).

## Paso a paso

### 1. Consigue tu código

Los códigos los distribuye el autor de Kigo en su [servidor de soporte](https://discord.gg/wmky5nBRR2) durante eventos, o se entregan manualmente a usuarios que apoyan el proyecto.

Si no tienes un código, no necesitas este comando. En su lugar, suscríbete en [whop.com](https://whop.com) y el premium se activa solo.

### 2. Canjea el código

En cualquier servidor con Kigo, ejecuta:

```
/premium canjear código:tu-código-aquí
```

El bot verifica que el código exista, no haya sido canjeado antes, y que tú no tengas ya premium.

Si todo va bien, te mostrará un panel con:

- **Plan activado:** Plan 1 (3 servidores)
- **Vence:** la fecha en que expira
- **Slots disponibles:** 3 servidores

### 3. Activa el premium en tus servidores

Ahora ve a cada servidor donde quieras premium y ejecuta:

```
/premium usar
```

Tienes que ser **owner del servidor** para hacerlo. Si hay varios owners en tu servidor, cualquiera de ellos puede activarlo.

### 4. Gestiona tus slots

Para ver en qué servidores tienes premium activo y cuántos slots te quedan:

```
/premium estado
```

Para liberar un slot (y usarlo en otro servidor):

```
/premium liberar
```

## Si algo falla

- **"Código no válido"**: el código no existe, ya fue canjeado, o el formato es incorrecto. Verifica que lo copiaste completo, sin espacios.
- **"Ya tienes premium activo"**: no puedes canjear un segundo código si ya tienes premium. Si quieres reemplazarlo, primero libera todos tus slots con `/premium liberar` en cada servidor donde lo tengas activo.
- **No me deja canjear aunque no tengo premium**: a veces hay un delay de hasta 1 minuto. Espera y reintenta.

## Siguiente paso

Tras canjear, recuerda usar `/premium usar` en cada servidor donde quieras las funciones premium. Si tienes dudas, mira [qué incluye premium](que-es.md) o abre un ticket en el [servidor de soporte](https://discord.gg/wmky5nBRR2).
