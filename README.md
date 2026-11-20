# larochec.github.io

Source of [larochec.github.io](https://larochec.github.io/), the personal website of Clément Laroche: speech and audio ML on the edge.

## What's here

| Path | What it is |
|---|---|
| `index.html` | The whole page: markup, styles and a small script, all inline. No build step, no framework, no third-party requests. |
| `assets/img/` | Portrait, the STM32N6 board photo (WebP with a JPEG fallback), favicon, iOS home-screen icon, and the 1200×630 social preview card (`og-card.png`). |
| `assets/fonts/` | Newsreader (variable, Latin subset), self-hosted under the SIL Open Font License. |
| `assets/audio/` | The before/after demo: a VoiceBank-DEMAND test clip (`demo-noisy.wav`) and LiSenNet's real-time enhancement of it (`demo-enhanced.wav`), 16 kHz mono WAV. Loaded only when a visitor presses play. |
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
- **A publication**: copy an `<li class="pub">` block. Put the year only on the first entry of each year (leave the other `pub-year` spans empty).
- **Colours**: the tokens at the top of the `<style>` block (`--accent`, `--bg`, …), defined once for light and once for dark.
- **Social preview card** (`assets/img/og-card.png`): a static image of the name, tagline, portrait and waveform. Regenerate it if any of those change.
- **Demo audio**: replace the two WAVs in `assets/audio/` with another noisy/enhanced pair of the same length, and update the caption under the strip. The waveform drawn during playback is computed from the files themselves.

The page follows the visitor's light/dark preference and remembers a manual choice (in `localStorage`). The waveform animation pauses when off-screen, freezes or resumes when clicked (or with Enter/Space when focused), and is static for visitors who prefer reduced motion. The **Noisy** and **Enhanced** buttons play the demo clip; pressing the other one mid-clip switches version at the same moment, and while a clip plays the strip draws the real audio passing through the chip. Without JavaScript, the strip, the player and the theme button are simply hidden.

## Deployment

GitHub Pages serves the site from the root of `main`. Changes pushed to `main` are live within a minute or two.

## Credits

- Typeface: [Newsreader](https://github.com/productiontype/Newsreader), Copyright 2020 The Newsreader Project Authors, licensed under the SIL Open Font License 1.1 (see `assets/fonts/Newsreader-OFL.txt`). Packaged by [Fontsource](https://fontsource.org/).
- Demo audio: test utterance `p232_032` from the VoiceBank-DEMAND noisy speech database (C. Valentini-Botinhao et al., University of Edinburgh; [16 kHz mirror](https://huggingface.co/datasets/JacobLinCool/VoiceBank-DEMAND-16k)), licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The enhanced version was produced from it by [LiSenNet](https://huggingface.co/claroche1/LiSenNet)'s `conv-hardened` int8 streaming graph (noisy-phase, real-time path); both files share one gain and have 15 ms fades.
- GitHub icon adapted from [Lucide](https://lucide.dev/), ISC License. Copyright (c) for portions of Lucide are held by Cole Bemis 2013-2022 as part of Feather (MIT); all other copyright (c) for Lucide is held by Lucide Contributors 2022. The remaining icons are drawn for this page.
