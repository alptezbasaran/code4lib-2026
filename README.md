# Code4Lib 2026 — Presentation

A Quarto + Reveal.js presentation template, same structure as [ncam25](https://github.com/alptezbasaran/ncam25).

## Project structure

- `_quarto.yml` — Quarto project config (footer, theme, reveal options)
- `slides/index.qmd` — Main slide deck (add your content here)
- `slides/theme/theme.scss` — Custom theme (colors, typography)
- `assets/` — Shared images/logos for content slides.
- `slides/assets/` — Deck-local assets used by generated `slides/index.html`; includes `lib_logo_whiteBG.svg` / `.png` for title-slide and corner logo.
- `Dockerfile` — Quarto environment for Docker
- `compose.yaml` — Docker Compose for local preview
- `.github/workflows/deploy-page.yml` — Deploy to GitHub Pages on push to `main`

## Running with Docker

1. **Start the container:**
   ```bash
   docker compose up -d
   ```

2. **Render the slides:**
   ```bash
   docker compose exec slides bash -lc "quarto render slides/index.qmd"
   ```

3. **Preview (live reload):**
   - Open http://localhost:4000
   - Or: `docker compose exec slides bash -lc "quarto preview slides/index.qmd"`

## Render locally (no Docker)

From the project root:

```bash
quarto render slides/index.qmd --to revealjs
open slides/index.html
```

Live preview (reloads on save):

```bash
quarto preview slides/index.qmd
```

Requires [Quarto](https://quarto.org/docs/get-started/) installed. If you don’t have it, use Docker (see above).

## Customize

- Edit `slides/index.qmd` front matter (title, subtitle, author, date) and add slides (separate with `---`).
- Put images in `slides/assets/` and reference as `assets/yourfile.png` in slides (most reliable for local HTML + Pages).
- Adjust theme in `slides/theme/theme.scss` (e.g. `$accent`).

## GitHub Pages

Push to `main` (with changes under `slides/`, `_quarto.yml`, or `assets/`) to trigger the workflow. Enable **Pages** in the repo (Settings → Pages → Source: GitHub Actions) and use the `github-pages` environment.
