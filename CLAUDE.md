# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # start dev server at http://localhost:3030 (hot reload)
npm run build    # build static output to dist/ (includes --base /aussie-animals-slidev/ for GitHub Pages)
npm run export   # export to PDF (requires Playwright — run `npx playwright install chromium` first)
```

There are no tests or linters configured.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds and deploys to GitHub Pages automatically. Live URL: https://chenkonturek.github.io/aussie-animals-slidev/

The `--base /aussie-animals-slidev/` flag in the build script is required — removing it breaks asset paths on GitHub Pages. For local builds (`dist/`) served from a root path, this flag causes asset 404s; serve locally with `npx serve dist` or use `npm run dev` instead.

## Architecture

This is a [Slidev](https://sli.dev) presentation — a Vue-powered slide deck defined entirely in `slides.md`.

**Entry point:** `slides.md` — contains all 14 slides separated by `---`. Each slide can have its own YAML frontmatter (layout, transition, class) and an optional `<script setup>` block for reactive data.

**Theme:** `@slidev/theme-shibainu`. Available layouts from this theme: `cover`, `section`, `section-2`, `section-3`, `default`, `default-2` through `default-7`, `center`, `quote`, `right`. Slidev core also provides: `two-cols`, `two-cols-header`, `image`, `image-left`, `image-right`, `iframe`, `fact`, `statement`. The theme does **not** support `colorSchema: light`.

**Global styles:** `style.css` at the project root is auto-loaded by Slidev. It overrides shibainu with child-friendly colours (CSS custom properties prefixed `--color-*`), sets Nunito as the base font, and adds a `slide-up-in` entrance animation on all slide content.

**Components** (`components/` — auto-imported by Slidev, no registration needed):

- `AnimalGrid.vue` — wraps a configurable CSS grid of `AnimalCard` instances. Contains the full `ANIMAL_DATA` record internally (keyed by animal slug). Pass animal slugs via `:animals` prop and optionally `:columns`.
- `AnimalCard.vue` — 3D CSS flip card. Front shows emoji + name + type; back shows fact + habitat. Uses `-webkit-` prefixes for Safari compatibility. Toggle state is `isFlipped = ref(false)`.
- `AnimalQuiz.vue` — self-contained multi-choice quiz. Accepts a `questions` array (each item: `{ question, options[], correct, explanation }`). Tracks `currentIndex`, `score`, and `isComplete` internally. Uses `<Transition name="slide-fade">` between questions and `<Transition name="fade">` for the explanation panel.
- `FunFact.vue` — stateless bounce-in card (pure CSS `@keyframes bounce-in`). Props: `emoji`, `fact`, `color`.
- `AustraliaMap.vue` — pure inline SVG map of Australia (520×450 viewBox). No props. Renders the continent outline, Tasmania, ocean labels, and animal emoji markers (🐊 north, 🦘 outback, 🐨 east coast, 🦈 Pacific). Width-driven sizing (`width: 100%; height: auto`) — size it by constraining the parent container.

**Slide-scoped styles:** Add a `<style>` block at the end of a slide's markdown content for styles that apply only to that slide. Class names must be unique across slides as these styles are **not** automatically scoped (unlike Vue SFC `<style scoped>`). Prefix with a slide-specific namespace (e.g. `.spl-` for the Australia is Special slide) to avoid collisions.

**Full-bleed slides:** Use `layout: none` to bypass all theme padding and layout wrappers. Place content in a `div` with `position: absolute; inset: 0` (or UnoCSS `absolute inset-0`) to fill the full slide area. Used on slide 2 (Australia is Special) for the two-panel design.

**Passing data to components in slides:** Define variables in a per-slide `<script setup>` block placed after the slide content in `slides.md`. Each slide is compiled as its own Vue SFC, so variables do not leak between slides.
