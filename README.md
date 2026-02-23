# My Slides

Multi-topic [Reveal.js](https://revealjs.com/) presentations authored in Markdown, powered by [reveal-md](https://github.com/webpro/reveal-md).

## Quick Start

```bash
npm install        # install dependencies
npm run dev        # start dev server with live reload
npm run build      # export static HTML to _site/
```

The dev server opens a directory listing of all topics. Click any topic to view its slides.

## Adding a New Topic

1. Copy the `slides/example-topic/` directory:
   ```bash
   cp -r slides/example-topic slides/my-new-topic
   ```
2. Edit `slides/my-new-topic/slides.md` with your content.
3. Place any images in `slides/my-new-topic/images/`.
4. Run `npm run dev` — the new topic appears in the listing automatically.

## Project Structure

```
my-slides/
├── package.json          # npm scripts (dev, build)
├── reveal-md.json        # reveal-md options (separators, custom CSS)
├── reveal.json           # Reveal.js options (controls, transitions)
├── theme/
│   └── custom.css        # shared CSS overrides for all decks
├── slides/
│   ├── example-topic/
│   │   ├── slides.md     # slide content in Markdown
│   │   └── images/       # topic-specific images
│   └── another-topic/
│       ├── slides.md
│       └── images/
└── _site/                # static build output (gitignored)
```

## Markdown Conventions

### Slide Separators

| Separator | Purpose |
|-----------|---------|
| `---`     | Horizontal slide break (new section) |
| `--`      | Vertical slide break (drill-down within section) |
| `Note:`   | Speaker notes (press **S** to view) |

### Front Matter

Each `slides.md` can include YAML front matter for per-deck settings:

```yaml
---
title: My Topic Title
theme: black
revealOptions:
  transition: fade
---
```

### Per-Slide Attributes

Use HTML comments to set slide-level attributes:

```markdown
<!-- .slide: data-background="#2d2d2d" -->
## Slide with dark background
```

### Fragment Animations

```markdown
- First <!-- .element: class="fragment" -->
- Second <!-- .element: class="fragment" -->
```

## Available Themes

`black` (default) · `white` · `league` · `beige` · `night` · `serif` · `simple` · `solarized` · `moon` · `dracula` · `sky` · `blood`

Set per-deck in front matter or globally in `reveal.json`.

## Deployment

Run `npm run build` to generate a static site in `_site/`. Deploy that directory to any static host (GitHub Pages, Netlify, Vercel, etc.).
