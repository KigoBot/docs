# Documentación de Kigo

Sitio de documentación de Kigo, construido con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

Publicado en: **https://kigobot.github.io/**

## Estructura

```
.
├── mkdocs.yml              # Configuración del sitio
├── requirements.txt        # Dependencias Python (mkdocs-material, plugins)
├── README.md               # Este archivo
├── .github/workflows/      # CI: build + deploy a GitHub Pages
├── docs/                   # Contenido en Markdown
│   ├── index.md
│   ├── empezar/
│   ├── proteccion/
│   ├── moderacion/
│   ├── premium/
│   ├── problemas/
│   ├── legal/
│   └── assets/
│       ├── images/         # Capturas de pantalla
│       └── stylesheets/extra.css
└── overrides/              # Overrides del tema (footer custom)
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

## Despliegue

El workflow `.github/workflows/docs.yml` se ejecuta en cada push a `main`:
1. Construye el sitio con `mkdocs build --strict` en `site/`.
2. Sube `site/` como artefacto de GitHub Pages.
3. Despliega automáticamente en GitHub Pages.

Configuración requerida en el repositorio:
- **Settings → Pages → Source: GitHub Actions**
- (Sin secretos adicionales; el `GITHUB_TOKEN` ya tiene permisos para Pages.)

## Cambios desde la versión anterior

Antes la documentación vivía en `docs-site/` dentro del repositorio principal del bot. Ahora está en este repositorio separado para que el ciclo de vida de la docs sea independiente del binario. Las URLs publicadas (`https://kigobot.github.io/...`) no cambian.
