# mkdocs-example

Simple MkDocs site with Material theme, dark mode, multilingual docs (English/Japanese), Mermaid diagrams, and Git-based "Last updated".

## Prerequisites

- Python: `>= 3.11` (see `pyproject.toml`)
- Git: needed for revision date
- uv: fast Python package manager and runner
  - Install instructions: https://docs.astral.sh/uv/getting-started/installation/

## Setup

- Create the virtual environment and install dependencies:
  - `uv sync`

## Run Locally

- Start the dev server:
  - `uv run mkdocs serve`
- Open the site:
  - `http://127.0.0.1:8000/`

## Build For Deployment

- Build the static site into `site/`:
  - `uv run mkdocs build`

## Project Layout

- Source docs live under two language folders:
  - English: `docs/en/`
  - Japanese: `docs/ja/`
- Navigation and plugins are configured in `mkdocs.yml`.

## Features

- Material theme with dark mode toggle
- Multilingual navigation via `mkdocs-static-i18n`
- Mermaid diagrams via `mkdocs-mermaid2-plugin`
- Syntax highlighting via `pymdown-extensions` (`pymdownx.highlight`)
- Git metadata in the footer via:
  - `mkdocs-git-revision-date-localized-plugin` ("Last updated …")

## Notes & Troubleshooting

- Git metadata requires real commit history. In CI, ensure a full clone (e.g., GitHub Actions: set `fetch-depth: 0`). If history is unavailable, build date is used as a fallback.
- If you add pages, mirror them in both `docs/en/...` and `docs/ja/...` so the language switch stays in sync.
- If you change i18n or Git plugins, keep plugin order in `mkdocs.yml` as:
  - `i18n` → `git-revision-date-localized`

## License

This project is licensed under the MIT License. See `LICENSE` for details.
