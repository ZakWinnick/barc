# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Bay Area Rivian Club (BARC) website - a Hugo static site for the community club chapter. Live at https://bayarea.rivianclubs.org/

## Development Commands

```bash
# Local development server
hugo server

# Build for production
hugo --minify

# Build outputs to public/
hugo
```

## Project Structure

```
content/           # Markdown content
  _index.md        # Homepage
  events/          # Event posts
  about/           # About page
  contact/         # Contact page
static/images/     # Static assets (logo, hero, favicon)
themes/barc/       # Custom theme
  layouts/
    index.html     # Homepage template
    _default/      # Default templates (baseof.html, list.html)
    partials/      # Header, footer components
  static/css/      # Theme CSS
hugo.toml          # Site configuration
```

## Content Types

| Type | URL Pattern | Location |
|------|-------------|----------|
| Posts | `/:year/:month/:slug/` | `content/posts/` |
| Events | `/events/:slug/` | `content/events/` |
| Pages | `/:slug/` | `content/*.md` |

## Configuration

Key settings in `hugo.toml`:
- Primary color: `#1e3708`
- Pagination: 10 items per page
- Social: @bayarearivians (Twitter), @bayarearivianclub (Instagram)
- Minification enabled for production builds

## Deployment

GitHub Actions workflow (`.github/workflows/hugo.yml`) builds and deploys to GitHub Pages on push.
