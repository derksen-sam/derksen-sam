# Sam Derksen - Personal Site

A single-page personal site covering my work at TeamDynamix.

**Live site:** [https://derksen-sam.github.io/derksen-sam/](https://derksen-sam.github.io/derksen-sam/)

## Tech stack

- Plain HTML, CSS, and a small amount of vanilla JavaScript - no frameworks, no build step
- [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts (external dependency, loaded via `<link>`)
- Self-contained HTML files - all CSS and JS are inline, no build step

## Automation

This repo runs a few GitHub Actions workflows to keep the site in shape:

- **HTML Validation** (`.github/workflows/html-validate.yml`) - runs on every push and pull request. Checks all `.html` files at the repo root for structural issues (missing `alt` attributes, unclosed tags) via [HTMLHint](https://htmlhint.com/), and checks every link for breakage via [Lychee](https://github.com/lycheeverse/lychee).
- **Lighthouse CI** (`.github/workflows/lighthouse.yml`) - manually triggered via the Actions tab ("Run workflow"). Audits every `.html` file for performance, accessibility, best practices, and SEO. Accessibility scores below 90 fail the check.
- **Dependabot** (`.github/dependabot.yml`) - checks weekly for newer versions of the GitHub Actions used in these workflows and opens a pull request when one's available.

## Deploying updates (GitHub Pages)

1. Push changes to the `main` branch.
2. In the repo settings, under **Pages**, confirm the source is set to `main` / root (`/`).
3. GitHub Pages rebuilds automatically within a minute or two of the push - no manual deploy step needed.

## Project structure

```
.
├── index.html                          # main site - markup, styles, and script
├── 404.html                            # custom not-found page
├── .github/
│   ├── workflows/
│   │   ├── html-validate.yml           # HTML/link validation
│   │   └── lighthouse.yml              # Lighthouse CI audits
│   └── dependabot.yml                  # weekly Actions version checks
└── README.md
```

## License

No license specified - all rights reserved. This is a personal site, not intended for reuse. If you'd like to make it reusable under an open license (e.g. MIT), add a `LICENSE` file and update this section.
