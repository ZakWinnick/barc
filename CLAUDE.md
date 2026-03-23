# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Bay Area Rivian Club (BARC) website — a Hugo static site for the community club chapter.

- **GitHub Pages site:** https://barc.winnick.cloud
- **Production site:** https://bayarea.rivianclubs.org/

## Development Commands

```bash
hugo server          # Local dev server with live reload
hugo --minify        # Production build (outputs to public/)
```

## Deployment

GitHub Actions (`.github/workflows/hugo.yml`) builds with Hugo extended v0.140.0 and deploys to GitHub Pages on push to `main`. The workflow uses `--gc --minify` with `TZ: America/Los_Angeles`.

## Architecture

**Single-page homepage:** The site is primarily a single-page design. `themes/barc/layouts/index.html` defines the entire homepage as sequential sections (Hero → About → Events → Membership → Newsletter) without using partials for each section. The header partial exists but has an empty nav placeholder.

**Theme structure:** Everything lives in `themes/barc/`. There is one CSS file (`static/css/style.css`), one base layout (`layouts/_default/baseof.html`), and the homepage template overrides the `"main"` block.

**No header partial in baseof:** The base template does NOT include the header partial — it goes straight to `<main>` then footer. The header partial exists but is unused (navigation placeholder for future use).

## Design System

All styling uses CSS custom properties defined in `:root` in `themes/barc/static/css/style.css`:

- **Brand color:** `--color-primary: #1e3708` (forest green) with `-light` and `-dark` variants
- **Accent:** `--color-accent: #c9a227` (gold)
- **Typography:** Montserrat (headings via Google Fonts import), system font stack (body)
- **Dark mode:** Automatic via `prefers-color-scheme: dark` media query, overrides background/text/border variables only — primary and accent colors stay the same

## Third-Party Embeds

The homepage integrates three external services directly via script tags:

1. **Heylo** — Event feed embed (`embedded-events.min.js`) with hardcoded API key and community ID in `index.html`
2. **Ghost** — Newsletter signup form (`signup-form@~0.3`) configured inline with data attributes, points to `newsletter.bayarearivianclub.com`
3. **Tinylytics** — Analytics script loaded in `baseof.html` head

## Content

- **Archetypes:** `archetypes/default.md` uses TOML frontmatter (`+++`) with date, draft, and title fields
- **Permalinks:** Posts use `/:year/:month/:slug/`, events use `/events/:slug/`
- **Content is minimal:** Currently only `content/_index.md` exists; the homepage content is hardcoded in the template, not pulled from markdown
- **Taxonomies:** Tags and categories are configured but not yet in use

## Configuration

`hugo.toml` key settings:
- `enableGitInfo = true` — commit dates used for page metadata
- `markup.goldmark.renderer.unsafe = false` — raw HTML in markdown is disabled
- Social handles configured under `[params.social]`: twitter `bayarearivians`, instagram `bayarearivianclub`
- Inline SVG icons throughout (no icon library) — social icons in footer, benefit icons on homepage
