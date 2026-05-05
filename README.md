# Amazing Australian Animals! 🦘

A child-friendly interactive slide deck built with [Slidev](https://sli.dev), featuring clickable animal cards, fun fact banners, and a multiple-choice quiz.

**Live:** https://chenkonturek.github.io/aussie-animals-slidev/

## Getting Started

```bash
npm install
npm run dev      # opens http://localhost:3030
```

## Slides

14 slides covering:

- Kangaroo, Koala, Platypus, Wombat, Echidna, Kookaburra
- Marsupials vs Monotremes explainer
- Interactive quiz with 6 questions and score tracking

## Interactive Components

| Component | What it does |
|-----------|-------------|
| **AnimalCard** | 3D flip card — click to reveal a fun fact |
| **AnimalQuiz** | Step-through quiz with instant right/wrong feedback |
| **FunFact** | Bounce-in fact banner |
| **AustraliaMap** | Inline SVG map with animal emoji markers and ocean labels |

## Build & Export

```bash
npm run build    # static site → dist/ (includes --base flag for GitHub Pages)
npm run export   # PDF export (requires: npx playwright install chromium)
```

## Deployment

Pushing to `main` automatically builds and deploys to GitHub Pages via `.github/workflows/deploy.yml`. The build uses `--base /aussie-animals-slidev/` so assets resolve correctly under the repo sub-path.

## Tech

- [Slidev](https://sli.dev) v52 + [@slidev/theme-shibainu](https://github.com/slidevjs/themes/tree/main/packages/theme-shibainu)
- Vue 3 components with `<script setup>`
- UnoCSS (Tailwind-compatible utility classes)
- Nunito font via Google Fonts
