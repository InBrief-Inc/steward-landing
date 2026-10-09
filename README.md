# steward-landing

Static landing page for [Steward](https://steward.inbrief.sh), published with GitHub Pages.

- `index.html`: the whole page, with inline CSS and no build step. Colors and type tokens are copied from the Steward desktop app (dark theme).
- `assets/*.webp`: full-screen app screens (Code task waiting for approval, changes and delivery, Memory, Settings → Engines), rendered at 2x from the Steward redesign mockup. Refresh them when the app UI changes.
- `assets/fonts/`: self-hosted IBM Plex Sans and IBM Plex Mono (SIL Open Font License, see `LICENSE-IBM-Plex.txt`), the same fonts the app ships.
- `assets/og.png`, `favicon.png`, `apple-touch-icon.png`: social card and icons.
- `CNAME`: the custom domain GitHub Pages serves.

## Preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

GitHub Pages publishes `main` at the repository root, so a push to `main` rebuilds the site.

Settings → Pages: source "Deploy from a branch", branch `main`, folder `/ (root)`, custom domain `steward.inbrief.sh`. Leave "Enforce HTTPS" off, see below.

DNS, in Cloudflare for the `inbrief.sh` zone:

| Type  | Name    | Target                | Proxy status |
| ----- | ------- | --------------------- | ------------ |
| CNAME | steward | inbrief-inc.github.io | Proxied      |

Keep the record on "Proxied" (orange cloud), like `blog.inbrief.sh`. Cloudflare serves the HTTPS certificate (the zone's Universal SSL) and redirects HTTP to HTTPS, so GitHub's own certificate is not needed. On "DNS only", GitHub has to issue the certificate itself, which stayed pending for over an hour.
