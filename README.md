# Documentación de Kigo

Sitio de documentación de Kigo, construido con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Estructura

```
docs-site/
├── mkdocs.yml          # Configuración del sitio
├── requirements.txt    # Dependencias Python (mkdocs-material, plugins)
├── README.md           # Este archivo
├── docs/               # Contenido en Markdown
│   ├── index.md
│   ├── empezar/
│   ├── proteccion/
│   ├── moderacion/
│   ├── premium/
│   ├── problemas/
│   └── assets/
│       ├── images/     # Capturas de pantalla
│       └── stylesheets/extra.css
└── overrides/          # Overrides del tema (footer custom)
    └── partials/footer.html
```

## Build local

```bash
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/mkdocs serve     # http://localhost:8000
```

Para validar que no hay enlaces rotos:

```bash
.venv/bin/mkdocs build --strict
```

## Mover a otro repositorio

Toda la documentación está en esta carpeta para que sea trivial moverla a un repositorio propio.

### Pasos

1. Crea un repositorio nuevo (público o privado, lo que prefieras).
2. Copia **todo el contenido de esta carpeta** al nuevo repositorio, incluido el `.venv` no, ese no, pero sí el resto.
3. Crea un workflow de CI en el nuevo repositorio en `.github/workflows/docs.yml`. Ejemplo:

    ```yaml
    name: Documentación

    on:
      push:
        branches: [main]
      workflow_dispatch:

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v4
          - uses: actions/setup-python@v5
            with:
              python-version: '3.12'
              cache: pip
          - run: pip install -r requirements.txt
          - run: mkdocs build --strict
    ```

4. Configura el despliegue (GitHub Pages, Netlify, Cloudflare Pages, Vercel, o lo que prefieras).

### Qué cambia al mover

- El workflow ya no necesita `working-directory: docs-site` porque ahora la raíz del repo es esta carpeta.
- Si quieres publicar con GitHub Pages, el repositorio debe ser público o tener Pages activado en el plan de pago.
- Si mantienes la URL `https://kigobot.github.io/...` (o la que uses), no hace falta cambiar nada en los enlaces de la documentación.

### Qué NO cambia

- Todo el contenido de `docs/`.
- La configuración de `mkdocs.yml` (rutas internas son relativas a la raíz de esta carpeta).
- Los assets (CSS, imágenes, footer custom).
- El aspecto visual.
