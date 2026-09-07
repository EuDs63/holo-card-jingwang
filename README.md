# 静望 · Holographic Card (GitHub Pages)

Interactive holographic portrait card — **静望** — built with Three.js. Drag to rotate, scroll to zoom, flip the card, and tune foil / depth live in the browser.

## GitHub Pages

This folder is a static site ready for GitHub Pages:

1. Push the contents of this directory to a repo (or `gh-pages` branch / `/docs`).
2. Enable **GitHub Pages** from the repository settings (source: branch root or `/docs`).
3. `.nojekyll` is included so GitHub Pages does not process the site with Jekyll (needed for files starting with `_` and for plain static assets).

Three.js loads from the jsDelivr CDN (`three@0.180.0`) via an import map in `index.html` — no `node_modules` required on the host.

## Local preview

Serve the folder over HTTP (modules need a server):

```bash
npx serve .
# or: python3 -m http.server 8080
```

Then open the printed URL.

## Contents

| Path | Role |
|------|------|
| `index.html` | Page shell + import map |
| `app.js` | Three.js card scene, shaders, controls |
| `style.css` | Layout and UI |
| `card-config.json` | Card copy / collection metadata |
| `assets/subject.png` | Subject layer |
| `assets/background.png` | Background layer |
| `assets/lineart.png` | Line-art layer |
| `assets/text.png` | Text overlay |
| `assets/card.glb` | Card mesh |
| `.nojekyll` | Disable Jekyll on GitHub Pages |
