# Jaysree B — Portfolio

A dark, scroll-spy driven personal portfolio built from scratch in Angular — standalone components, signal-based state, and a reusable design token system.

**Live site:** https://jaysreeyadav22.github.io/

## Overview

Single-page portfolio for an AI Engineer / UI Developer, covering:

- **Hero** — intro, role, key stats, CTAs
- **About** — professional journey, education & certifications, core competencies, tools & technologies
- **Projects** — flagship and work projects, each with tags and an optional linked repo
- **CV** — experience timeline + downloadable resume PDF
- **Contact** — email and social links (LinkedIn, GitHub, Kaggle)

Navigation uses `IntersectionObserver`-based scroll-spy: the active nav link — and the pill highlight behind it — updates automatically as each section enters the viewport, and clicking a link smooth-scrolls to it.

## Tech stack

- **Angular** (standalone components, no NgModules)
- **Signals** for reactive state (`ScrollSpyService`)
- **SCSS** with a shared design token system (`_tokens.scss`, `_mixins.scss`)
- No external UI framework — fully custom styling

## Project structure

```
src/app/
├── core/
│   ├── services/
│   │   └── scroll-spy.service.ts   # tracks active section via IntersectionObserver
│   └── models/
│       └── project.model.ts        # Project interface
│
├── shared/
│   └── components/
│       ├── nav-bar/                # sticky header, scroll-spy nav, mobile menu
│       └── section-header/         # reusable "// TAG" + title + description block
│
├── features/
│   └── home/
│       └── sections/
│           ├── hero/
│           ├── about/
│           ├── projects/
│           ├── cv/
│           └── contact/
│
├── data/
│   └── portfolio-data.ts           # projects data (edit here to add/update projects)
│
└── styles/
    ├── _tokens.scss                # colors, spacing, radius, fonts
    └── _mixins.scss                # shared layout mixins

public/
├── images/                         # profile photo
└── files/                          # downloadable CV PDF
```

## Getting started

```bash
npm install
ng serve
```

Visit `http://localhost:4200`.

## Editing content

| To change...              | Edit this file                                  |
|----------------------------|-------------------------------------------------|
| Projects                  | `src/app/data/portfolio-data.ts`                 |
| Hero text/stats            | `src/app/features/home/sections/hero/hero.component.html` |
| About / experience / skills| `src/app/features/home/sections/about/about.component.html` |
| CV timeline                | `src/app/features/home/sections/cv/cv.component.html` |
| Resume PDF                 | Replace file in `public/files/`, keep the filename referenced in `cv.component.html` and `hero.component.html` matching |
| Profile photo              | Replace file in `public/images/`                 |
| Contact links               | `src/app/features/home/sections/contact/contact.component.html` |
| Colors / fonts / spacing   | `src/styles/_tokens.scss`                        |

## Deployment

Deployed via [`angular-cli-ghpages`](https://github.com/angular-schule/angular-cli-ghpages) to GitHub Pages.

```bash
ng deploy --base-href=/
```

> **Note:** this repo is a GitHub *user site* (`jaysreeyadav22.github.io`), which is served from the domain root — `--base-href` must be `/`, not the repo name. This differs from a regular project repo, which would use `--base-href=/repo-name/`.

After deploying, confirm in **Settings → Pages** that the source branch is set correctly, and hard-refresh (`Ctrl+Shift+R` / `Cmd+Shift+R`) to bypass cached assets if changes don't appear immediately.

