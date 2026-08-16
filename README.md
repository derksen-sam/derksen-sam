# Sam Derksen - Personal Site

[![HTML Validation](https://github.com/derksen-sam/derksen-sam/actions/workflows/html-validate.yml/badge.svg)](https://github.com/derksen-sam/derksen-sam/actions/workflows/html-validate.yml)
[![Lighthouse CI](https://github.com/derksen-sam/derksen-sam/actions/workflows/lighthouse.yml/badge.svg)](https://github.com/derksen-sam/derksen-sam/actions/workflows/lighthouse.yml)
[![Site Health Check](https://github.com/derksen-sam/derksen-sam/actions/workflows/site-health.yml/badge.svg)](https://github.com/derksen-sam/derksen-sam/actions/workflows/site-health.yml)
[![License: MIT](https://img.shields.io/github/license/derksen-sam/derksen-sam)](LICENSE)

A personal site built to learn GitHub's hosting and automation features, with a landing page, a dedicated page about my work at TeamDynamix, and a themed 404 page.

**Live site:** [https://derksen-sam.github.io/derksen-sam/](https://derksen-sam.github.io/derksen-sam/)

## What's on the site
 
- **Landing page** (`index.html`) - a brief intro and a live feed of my most recent public GitHub activity, fetched client-side from the GitHub events API with a fallback if the request fails.
- **Work page** (`work.html`) - details about my current role as a Technical Support Consultant at TeamDynamix, including skills and a few example solutions I've built.
- **Custom 404** (`404.html`) - a themed not-found page.

## Tech stack

- Plain HTML, CSS, and a small amount of JavaScript - no frameworks, no build step
  - Vanilla JavaScript powers the live GitHub activity feed and the dynamic copyright year
- [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts (external dependency, loaded via `<link>`)
- A single shared stylesheet (`styles.css`) is linked from all three pages, so the browser caches it once and reuses it across the site.

## Automation

This repo runs a few GitHub Actions workflows to keep the site in shape:

- **HTML Validation** (`.github/workflows/html-validate.yml`) - currently only running when manually triggered, but able to run on every push and pull request. Checks all `.html` files at the repo root for structural issues (missing `alt` attributes, unclosed tags) via [HTMLHint](https://htmlhint.com/), and checks every link for breakage via [Lychee](https://github.com/lycheeverse/lychee).
- **Lighthouse CI** (`.github/workflows/lighthouse.yml`) - manually triggered via the Actions tab ("Run workflow"). Audits every `.html` file for performance, accessibility, best practices, and SEO. Accessibility scores below 90 fail the check.
- **Site Health Check** (`.github/workflows/site-health.yml`) — runs daily on a schedule (and can also be triggered manually), pinging the live site and failing the check if it doesn't respond with a 200 status.
- **Dependabot** (`.github/dependabot.yml`) - checks weekly for newer versions of the GitHub Actions used in these workflows and opens a pull request when one's available.

## Deploying updates (GitHub Pages)

1. Push changes to the `main` branch.
2. In the repo settings, under **Pages**, confirm the source is set to `main` / root (`/`).
3. GitHub Pages rebuilds automatically within a minute or two of the push - no manual deploy step needed.

## Project structure

```
.
├── index.html                          # landing page — intro + live GitHub activity feed
├── work.html                           # TeamDynamix role, skills, and example solutions
├── 404.html                            # custom not-found page (nf- prefixed styles)
├── styles.css                          # shared stylesheet for all three HTML pages
├── lighthouserc.json                   # Lighthouse CI configuration
├── .github/
│   ├── workflows/
│   │   ├── html-validate.yml           # HTML/link validation
│   │   ├── lighthouse.yml              # Lighthouse CI audits
│   │   └── site-health.yml             # daily uptime check
│   └── dependabot.yml                  # weekly Actions version checks
└── README.md
```

## License

[MIT](LICENSE) — free to use, copy, modify, and reuse, with attribution.
