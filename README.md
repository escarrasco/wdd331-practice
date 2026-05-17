# WDD 331R Practice Site

**Student:** Esther Silvia Carrasco Escobar
**Semester:** Spring 2026
**Live Site:** [View Site](https://escarrasco.github.io/wdd331-practice/)

## About

This repository is my Practice Site for WDD 331R: Advanced CSS.
Each week I add new pages and styles as I work through the course
assignments. The site deploys automatically to GitHub Pages on
every push to main.

## Pages

- [Home](index.html)
- [Custom Properties and Nesting](unit-1/custom-properties/index.html)
- [Layered Components](unit-2/layered-components/index.html)

---

## CSS Architecture

Styles are organized into a layered folder structure inside `css/`. The layer order is declared in `main.css` and enforced by the build tool.

```
css/
├── base/
│   ├── elements.css      # Body, headings, links
│   └── reset.css         # Box-sizing, margin/padding reset
├── components/
│   └── card.css          # Assignment card component
├── layout/
│   └── primary.css       # Page wrapper, header, grid, footer
├── tokens/
│   ├── colors.css        # Color custom properties
│   └── variables.css     # Spacing, typography, radius, shadow tokens
├── utilities/
│   └── utilities.css     # Helper classes (sr-only, text-align)
└── main.css              # Layer order declaration and all imports
```

The five-layer stack in order: `tokens → base → layout → components → utilities`

## Build Tool

This project uses **PostCSS** :

| Package | Role |
|---|---|
| `postcss` | Core engine |
| `postcss-cli` | Command-line interface — enables `npm run build` and `npm run watch` |
| `postcss-import` | Bundles all `@import` files into one |
| `autoprefixer` | Adds vendor prefixes automatically for browser compatibility |
| `cssnano` | Minifies the output |

The source entry point is `css/main.css`. The bundled, minified output is written to `dist/styles.css`, which is what the HTML files reference.

## Running the Build

Install dependencies:

```bash
npm install
```

Build once (outputs to `dist/styles.css`):

```bash
npm run build
```

Watch mode — rebuilds automatically on every file save (use this during development):

```bash
npm run watch
```

> **Note:** `dist/` and `node_modules/` are in `.gitignore`. The CI workflow generates `dist/styles.css` automatically on every push to `main`.