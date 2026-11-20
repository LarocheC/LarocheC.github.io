# LarocheC — personal landing page

Single-file static landing page (`index.html`, no build step) for the GitHub account
[@LarocheC](https://github.com/LarocheC), in the style of personal `*.github.io` sites.
Includes live GitHub stats cards (account stats, most-used languages, contribution streak)
via [github-readme-stats](https://github.com/anuraghazra/github-readme-stats).

## Preview locally

Open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Publish (when ready to go live)

1. Make this repository **public** (GitHub Pages on the free plan requires a public repo).
2. Go to **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   pick `main` and `/ (root)`, then Save.
3. The site goes live at `https://larochec.github.io/` after a minute or two.

Until then, keep the repo private / do not enable Pages: nothing is publicly reachable.

## Customize

- Edit text, links and project cards directly in `index.html`.
- Avatar and stats are pulled live from GitHub (`avatars.githubusercontent.com`,
  `github-readme-stats.vercel.app`, `github-readme-streak-stats.herokuapp.com`).
