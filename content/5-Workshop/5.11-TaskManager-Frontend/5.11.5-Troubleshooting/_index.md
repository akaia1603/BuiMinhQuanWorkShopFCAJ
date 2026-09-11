---
title: "Troubleshooting"
date: 2026-09-01
weight: 5
chapter: false
pre: " <b>5.11.5.</b> "
---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| The page loads but CSS/JS do not (403) | The `css/` and `js/` folders have mode `dr-x------` (500) — nginx cannot read them. Run `sudo chmod 755 /usr/share/nginx/html/css/ /usr/share/nginx/html/js/`, then `sudo chmod 644 /usr/share/nginx/html/css/* /usr/share/nginx/html/js/*`, followed by `sudo systemctl restart nginx` |
| The UI loses all styling and layout breaks | `style.css` had a syntax error (the `.stat-label` selector was missing a closing `}`) which made the browser skip the following CSS. Fixed the block; verified by counting balanced `{`/`}` |
| API calls return `403` after changing the JWT secret | The old token in the browser is invalid. Open the Console (F12), run `localStorage.clear()`, refresh the page and sign in again |