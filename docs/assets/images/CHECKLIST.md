# Checklist de capturas para la documentación

Capturas pendientes para mejorar la documentación. Esta lista se va rellenando a medida que se generan.

> **Estado**: vacío. La documentación actual funciona sin capturas. Las imágenes son opcionales y se añadirán en una segunda iteración.

## Formato de archivo

- **PNG** para capturas estáticas (mensajes, menús, embeds).
- **GIF** o **WebP animado** para flujos interactivos.
- Nombres en kebab-case, descriptivos.
- Subir a `docs/assets/images/` y referenciar con `![alt](../assets/images/nombre.png)`.

## Capturas pendientes

### 1. `invitar-bot.gif`

- **Tamaño objetivo**: 720×405 px, ≤ 2 MB
- **Contenido**: animación del usuario abriendo el enlace de invitación, viendo los permisos, y aterrizando en el servidor con el bot visible.
- **Para usar en**: `empezar/invitar.md` — sección "Lo que verás los primeros segundos".
- **Cómo capturarlo**: grabar pantalla con OBS o ffmpeg durante el proceso de invitación. Recortar a los primeros 6-10 segundos.

### 2. `configuracion-menu.png`

- **Tamaño objetivo**: 720×480 px
- **Contenido**: el menú principal de `/configuración` con los submenús visibles.
- **Para usar en**: `empezar/primer-uso.md` y `proteccion/index.md`.
- **Cómo capturarlo**: ejecutar el comando en un servidor de prueba, hacer captura de pantalla, anotar las opciones con flechas si es necesario.

### 3. `verificacion-ejemplo.png`

- **Tamaño objetivo**: 720×360 px
- **Contenido**: el botón "Verificate" fijado en el canal de verificación, y la vista del menú desplegable con 3 opciones de código que aparece al pulsarlo.
- **Para usar en**: `proteccion/verificacion.md`.
- **Cómo capturarlo**: configurar verificación con el botón Verificate fijado en el canal, pulsar el botón y capturar el menú desplegable con las 3 opciones de código.

### 4. `antiraid-accion.png`

- **Tamaño objetivo**: 720×320 px
- **Contenido**: un log de moderación mostrando una acción del anti-raid (baneo automático, por ejemplo).
- **Para usar en**: `proteccion/antiraid.md` y `proteccion/logs.md`.
- **Cómo capturarlo**: ejecutar `/logs` después de simular un raid en un servidor de pruebas.

### 5. `top-servers.png`

- **Tamaño objetivo**: 720×600 px
- **Contenido**: la respuesta de `/top-servers` con la lista de servidores ordenada por miembros.
- **Para usar en**: `empezar/index.md` o `proteccion/index.md` (sección de servidores grandes).
- **Cómo capturarlo**: ejecutar el comando en cualquier servidor donde esté el bot.

### 6. `anuncio-preview.png`

- **Tamaño objetivo**: 720×480 px
- **Contenido**: el embed de previsualización de `/anuncio` con los botones Confirmar/Cancelar visibles.
- **Para usar en**: `premium/canjear.md` (sección sobre anuncios a múltiples servidores).
- **Cómo capturarlo**: ejecutar `/anuncio` con un mensaje de prueba, capturar antes de confirmar.

## Capturas que se descartaron

Las dos capturas siguientes estaban pensadas para una sección de arquitectura interna que se eliminó por no ser contenido público. Si en el futuro se vuelve a incluir esa sección, se pueden recuperar:

- `health-endpoint.png` — `curl http://localhost:9180/health` con la respuesta JSON.
- `metricas-prometheus.png` — `curl http://localhost:9180/metrics` con varias métricas.

## Cómo añadir las capturas al sitio

1. Genera la imagen y guárdala en `docs/assets/images/` con el nombre exacto de esta lista.
2. Abre el archivo `.md` correspondiente y añade la referencia Markdown:

   ```markdown
   ![Texto alternativo descriptivo](../assets/images/nombre.png)
   ```

3. Ejecuta `mkdocs build --strict` para validar que el enlace no está roto.
4. Sube los cambios en un commit con mensaje tipo `docs: añadir captura de <descripción>`.

## Prioridad

Orden sugerido de captura:

1. **`configuracion-menu.png`** — la captura más referenciada.
2. **`verificacion-ejemplo.png`** — el flujo de verificación es confuso sin imagen.
3. **`invitar-bot.gif`** — primera impresión del usuario.
4. El resto cuando haga falta.
