# Website Maintenance Guide

## Local development

Run the local Hugo server from the repository root:

```bash
hugo server
```

Useful variations:

```bash
hugo server --buildDrafts
hugo --minify
```

- `hugo server` starts a live preview.
- `hugo server --buildDrafts` is useful if you temporarily mark a page as draft.
- `hugo --minify` is a good pre-push check because it matches the production build more closely.

## Core files and folders

- `config.yml`: global site settings, homepage copy, buttons, metadata, analytics, and social/profile links.
- `content/research/`: one folder per research project.
- `content/cv/somdeepa_das_cv.pdf`: the public CV file.
- `content/teaching/_index.md`, `content/contact.md`, `content/resources/_index.md`: top-level page content.
- `layouts/`: Hugo template overrides.
- `assets/css/`: custom styling layered on top of PaperMod.
- `.github/workflows/`: GitHub Pages build and deploy workflow.

## Homepage maintenance

The homepage is driven from `config.yml` under `params.profileMode`.

Important fields:

- `title`: homepage heading.
- `subtitle`: main professional introduction.
- `researchAgenda`: short paragraph summarizing the active research pipeline.
- `marketNote`: brief timing signal for the Fall 2026 market.
- `buttons`: homepage calls to action.

Keep the homepage focused on research identity rather than materials you do not yet have. Until the job-market packet is ready, avoid adding empty placeholders for a JMP, publications, or references.

## Research page conventions

The research page is organized by `research_status` in each project's front matter.

Use:

- `research_status: working-paper` for projects with a developed abstract, draft, or circulating paper.
- `research_status: project` for projects that are active but not yet ready to share as full drafts.

Suggested front matter pattern:

```yaml
---
title: "Project title"
author: ["Somdeepa Das", "Coauthor Name"]
description: "Search-friendly one-paragraph description."
summary: "Committee-readable summary for the research list page."
research_status: working-paper
weight: 1
is_published: false
show_journal: false
---
```

Guidelines:

- `description` should help search engines understand the project.
- `summary` should work for hiring committees scanning the research page quickly.
- `weight` controls ordering within each section.
- Projects can omit action links entirely until you are ready to share materials.
- `params.researchList.cardsClickable` in `config.yml` controls whether the whole research card is clickable.
- `paperLink` can be added to front matter if you want a working-paper card to point to a PDF or external draft link instead of the project page.
- `slideLink` can be added to front matter if you want a project card to show a `Slides` button on the research page.

## Adding or updating a project

1. Copy an existing folder inside `content/research/`.
2. Rename the folder to the desired URL slug.
3. Update the front matter.
4. Add or remove `paperLink`, `slideLink`, `paper.pdf`, or `slides.pdf` depending on what you want to expose from the research page.
5. Update the on-page abstract so it matches the latest version you want online.

Recommended ordering for the current site:

- `1`: alcohol working paper
- `1`: unions project
- `2`: third project / project in progress

## CV updates

Replace the file at `content/cv/somdeepa_das_cv.pdf` with the newest version. Keep the filename unchanged so existing links continue to work.

## Deployment

Deployment is handled by GitHub Pages Actions.

Current behavior:

- pushes to `main` trigger a production Hugo build
- the action uploads the generated `public/` directory
- GitHub Pages serves the latest successful deployment automatically

There is no manual copy step from `public/` into another deployment folder.

## SEO and indexing checklist

Before Fall 2026 market season, review:

1. `config.yml` site description and keywords.
2. Homepage copy so it includes your name, field, institution, and research areas.
3. `description` fields for each research project.
4. `params.socialIcons` and `params.schema.sameAs`.

Recommended links to add when ready:

- Google Scholar
- LinkedIn
- ORCID

Optional verification:

- put your Google Search Console verification token in `params.analytics.google.SiteVerificationTag`

After deployment:

1. submit `https://somdeepa.github.io/sitemap.xml` in Google Search Console
2. request indexing for the homepage and key research pages if needed
3. search for `Somdeepa Das economics Purdue` and monitor whether the homepage becomes the dominant result

## Notes for upcoming content refreshes

- Replace the current alcohol summary with the newest draft language once that draft is ready.
- Refresh the unions abstract as soon as the revised abstract is finalized.
- Replace the temporary ongoing-project placeholder with the real title and abstract for the third project.
