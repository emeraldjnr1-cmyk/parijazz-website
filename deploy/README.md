# Pari Jazz Commerce — Netlify deploy

This folder is the production website, ready to deploy.

## Deploy

### Option A — Drag & drop
Open https://app.netlify.com/drop and drag this entire folder onto the page.

### Option B — GitHub + Netlify
1. Push this folder as a repo's root.
2. In Netlify, create a new site from that repo.
3. Build settings: no build command, publish directory = ".".

### Option C — Netlify CLI
```
netlify deploy --dir=. --prod
```

## Pages

- `index.html` — Startseite (homepage)
- `e-commerce.html` — E-Commerce
- `sourcing.html` — Sourcing
- `eu-market-entry.html` — EU-Markteintritt
- `contact.html` — Kontakt
- `support.js` — runtime (MUST sit alongside the html files)
- `assets/` — images
