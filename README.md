# larochec.github.io

Personal landing page of Clément Laroche: speech and audio ML on the edge.

> **Status: private draft.** This repository is private and GitHub Pages is off, so nothing here is public yet.

## What's here

| Path | What it is |
|---|---|
| `index.html` | The whole page: markup, styles and a small script, all inline. No build step, no framework, no third-party requests. |
| `assets/img/` | Portrait, the STM32N6 board photo (WebP with a JPEG fallback), favicon, iOS home-screen icon, and the 1200×630 social preview card (`og-card.png`). |
| `assets/fonts/` | Newsreader (variable, Latin subset), self-hosted under the SIL Open Font License. |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, without a Jekyll build. |

## Preview locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Opening `index.html` directly in a browser also works.

## Editing

Everything is plain HTML in `index.html`, in page order: hero, About, Selected work, Publications, Contact. Each section starts with a comment banner.

- **Text**: edit it in place.
- **A project**: copy an existing `<li class="project">` block inside the matching theme.
- **A publication**: copy an `<li class="pub">` block. Put the year only on the first entry of each year. The newest year is always visible; entries inside `<details class="pubs-older">` stay folded until a visitor expands them, so update its "N more from …" label when you add or move papers.
- **Colours**: the tokens at the top of the `<style>` block (`--accent`, `--bg`, …), defined once for light and once for dark.
- **Social preview card** (`assets/img/og-card.png`): a static image of the name, tagline, portrait and waveform. Regenerate it if any of those change.

The page follows the visitor's light/dark preference and remembers a manual choice (in `localStorage`). The waveform animation pauses when off-screen, freezes or resumes when clicked (or with Enter/Space when focused), and is static for visitors who prefer reduced motion. Without JavaScript, the animation and theme button are simply hidden.

## Going live

1. Merge the page into `main`.
2. **Settings → General → Danger zone → Change visibility → Public.** GitHub Pages needs a public repository on the free plan. Making the repository public also makes all of its branches and pull requests public.
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch → `main` / `(root)` → Save.**
4. After a minute or two the site is live at <https://larochec.github.io/>.

## Credits

- Typeface: [Newsreader](https://github.com/productiontype/Newsreader), Copyright 2020 The Newsreader Project Authors, licensed under the SIL Open Font License 1.1 (see `assets/fonts/Newsreader-OFL.txt`). Packaged by [Fontsource](https://fontsource.org/).
- GitHub icon adapted from [Lucide](https://lucide.dev/), ISC License. Copyright (c) for portions of Lucide are held by Cole Bemis 2013-2022 as part of Feather (MIT); all other copyright (c) for Lucide is held by Lucide Contributors 2022. The remaining icons are drawn for this page.
