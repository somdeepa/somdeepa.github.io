# Somdeepa Das Website

This repository contains the Hugo source for `https://somdeepa.github.io/`, a research-first academic website built on a customized `PaperMod` theme and deployed with GitHub Pages Actions.

## Quick start

Install Hugo Extended, then from the repo root run:

```bash
hugo server
```

That starts a local preview server with live reload. The production site is generated automatically by GitHub Actions whenever changes are pushed to `main`.

## Everyday editing

- Homepage configuration lives in `config.yml`.
- Research entries live in `content/research/<project-slug>/index.md`.
- Teaching, resources, and contact pages live in `content/`.
- The current CV should be kept at `content/cv/somdeepa_das_cv.pdf`.
- Custom styling and layout overrides live in `assets/css/` and `layouts/`.

## Deployment

Push to `main` to trigger the GitHub Pages workflow in `.github/workflows/`. The site is built in production mode and deployed from the generated `public/` directory artifact. There is no separate `www` folder to update manually.

## More documentation

See [docs/website-maintenance.md](docs/website-maintenance.md) for content conventions, project-entry structure, deployment notes, and the SEO/indexing checklist.
