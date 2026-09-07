# Holo Multi-Card Site

Interactive holographic collectible cards (Three.js). One repo, multiple cards.

## Live

- Pages: https://ds63.eu.org/holo-card-jingwang/
- Repo: https://github.com/EuDs63/holo-card-jingwang

## Cards

| id | title | path |
|----|-------|------|
| ditto (default) | Bai Bian Guai | ./cards/ditto/ |
| jingwang | Jing Wang | ./cards/jingwang/ |

Switch with header chips, or open `?card=ditto` / `?card=jingwang`.

## Local preview

```bash
python3 -m http.server 8080
```

## Structure

```
index.html  app.js  style.css  cards.json  .nojekyll
cards/ditto/...  cards/jingwang/...
```

Asset paths in each card-config.json are relative to that card folder (`./assets/...`).
