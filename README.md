# Babylon — babylon.vc

Single-page site for the Babylon fund.

## Deployment (Vercel)

1. Sign up / log in at vercel.com
2. New project → "Add new" → upload this entire folder
3. Vercel auto-detects it as a static site, deploys in ~30 seconds
4. Settings → Domains → add `babylon.vc` and `www.babylon.vc`
5. Vercel shows DNS records to configure at your registrar
6. Add the records (A record for apex, CNAME for www)
7. HTTPS auto-provisions via Let's Encrypt

## Files

- `index.html` — the site (logo embedded as base64, fonts from Google Fonts CDN)
- `og-image.png` / `og-image.jpg` — 1200×630 social preview card
- `favicon-32x32.png` / `favicon-192x192.png` / `apple-touch-icon.png` / `favicon.ico` — browser/device icons
- `babylon-logo.png` — full-resolution transparent logo (for other uses)
- `vercel.json` — caching headers + clean URLs
- `robots.txt` / `sitemap.xml` — basic SEO

## To update copy

Edit `index.html` directly, push to Vercel (drag-drop again, or connect to GitHub).

## To update the OG image

Replace `og-image.png` and `og-image.jpg`. After updating, Twitter/Slack/etc. cache previews — use https://cards-dev.twitter.com/validator and Slack's `/unfurl` to bust their caches.
