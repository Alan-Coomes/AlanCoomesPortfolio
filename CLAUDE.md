# CLAUDE.md

## Project Overview

Personal portfolio website for Alan Coomes, hosted on GitHub Pages at **alancoomes.com**. This is a static, single-page site with no build tools, bundlers, or JavaScript frameworks.

## Repository Structure

```
/
├── index.html   # Entire site: HTML markup + inline CSS (no external stylesheets)
├── CNAME        # Custom domain: alancoomes.com
├── README.md    # Repo description
└── CLAUDE.md    # This file
```

## Architecture & Tech Stack

- **Pure static HTML/CSS** — no JavaScript, no build step, no dependencies
- **All CSS is inline** in a single `<style>` block inside `index.html`
- **Google Fonts** loaded via `<link>`: DM Serif Display (headings), DM Mono (monospace accents), Figtree (body text)
- **No package.json, no node_modules, no bundler** — edits to `index.html` are the final output

## Deployment

- **GitHub Pages** serves the `main` branch automatically
- The `CNAME` file maps the site to `alancoomes.com`
- There is no CI/CD pipeline, no build command, no test suite
- Pushing to `main` deploys immediately

## Design System

### CSS Custom Properties (`:root`)

| Variable         | Value         | Usage                     |
|------------------|---------------|---------------------------|
| `--navy`         | `#0a0f1e`     | Page background           |
| `--navy2`        | `#111827`     | Secondary background      |
| `--teal`         | `#0ea5a0`     | Primary accent color      |
| `--teal-dim`     | `#0ea5a020`   | Teal at low opacity       |
| `--teal-border`  | `#0ea5a040`   | Teal border at low opacity|
| `--cream`        | `#f5f2eb`     | (Defined, unused)         |
| `--muted`        | `#8892a4`     | Secondary/muted text      |
| `--text`         | `#e8eaf0`     | Primary text              |
| `--text-dim`     | `#c5cad6`     | Dimmed body text          |
| `--card`         | `#141c2e`     | Card backgrounds          |
| `--border`       | `#1e2a40`     | Border color              |

### Typography

- **Headings / display**: `'DM Serif Display', serif`
- **Monospace accents** (tags, dates, labels): `'DM Mono', monospace`
- **Body text**: `'Figtree', sans-serif`

### Responsive Breakpoint

Single breakpoint at `max-width: 640px`:
- Grids collapse to single column
- Nav padding shrinks
- Timeline dates are hidden on mobile

## Page Sections

The site is a single-page layout with anchor-linked navigation:

1. **Nav** — sticky top bar with logo + links to `#experience`, `#education`, `#skills`, `#contact`
2. **Hero** — full-viewport intro with name, tagline, CTA buttons, and stats row
3. **Experience** (`#experience`) — vertical timeline with two roles at Infosys/T-Mobile
4. **Education** (`#education`) — two-column card grid (Georgia Tech MS, Concordia BA)
5. **Skills** (`#skills`) — two-column grid of skill groups with tag chips
6. **Contact** (`#contact`) — two-column grid with email, phone, location
7. **Footer** — single line with name and year

## Conventions for AI Assistants

### General Rules

- **All changes happen in `index.html`** — there are no other source files
- **Preserve the dark theme** — always use CSS variables, never hardcode colors
- **Keep CSS inline** — do not extract to a separate stylesheet unless explicitly asked
- **No JavaScript** unless the user explicitly requests it
- **No build tools** — do not introduce npm, webpack, vite, etc. unless explicitly asked
- **Maintain responsive design** — test any layout changes against the 640px breakpoint

### Style Guidelines

- Use existing CSS custom properties for all colors
- Follow the established font-family assignments (serif for headings, mono for labels, sans-serif for body)
- New components should match existing patterns: `0.5px` borders, `8px` border-radius on cards, `var(--card)` backgrounds
- Button styles: use `.btn` base class with `.btn-primary` or `.btn-outline` modifiers
- Section headers follow the pattern: `.section-tag` (numbered tag) + `.section-line` (divider)

### Content Updates

- Experience entries use the `.timeline-item` grid structure (date | track | content)
- Education entries use `.edu-card` inside `.edu-grid`
- Skills use `.skill-group` with `.skill-tag` chips inside `.skills-grid`
- Contact items use `.contact-item` inside `.contact-grid`

### Testing

- There is no automated test suite
- Verify changes by opening `index.html` directly in a browser or starting a local HTTP server
- Check both desktop and mobile layouts (640px breakpoint)
