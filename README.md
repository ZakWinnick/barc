# Bay Area Rivian Club

The official website for the Bay Area Rivian Club (BARC), the first chapter of [Rivian Clubs of America](https://rivianclubs.org). Built with [Hugo](https://gohugo.io/).

**Live site:** [bayarea.rivianclubs.org](https://bayarea.rivianclubs.org/)

## Getting Started

Requires [Hugo extended](https://gohugo.io/installation/) (v0.140.0+).

```bash
hugo server        # Start local dev server at localhost:1313
hugo --minify      # Build for production (outputs to public/)
```

## Project Structure

The site uses a custom Hugo theme at `themes/barc/` with a single-page homepage layout. Content sections (About, Events, Membership, Newsletter) are defined in the homepage template rather than as separate content pages.

- `themes/barc/layouts/` — Page templates (homepage, list, base)
- `themes/barc/static/css/style.css` — All styles with CSS custom properties and automatic dark mode
- `content/` — Markdown content
- `static/images/` — Logo, hero image, favicon
- `hugo.toml` — Site configuration

## Deployment

Pushes to `main` automatically build and deploy to GitHub Pages via GitHub Actions.

## Links

- [Heylo Community](https://www.heylo.com/groups/bay-area-rivian-club) — Membership & events
- [Newsletter](https://newsletter.bayarearivianclub.com/) — The BARCing Lot
- [@bayarearivians](https://x.com/bayarearivians) on X
- [@bayarearivianclub](https://instagram.com/bayarearivianclub) on Instagram
