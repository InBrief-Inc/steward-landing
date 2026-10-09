# steward-landing

Static landing page for [Steward](https://steward.inbrief.sh), published with GitHub Pages.

- `index.html`: the whole page, with inline CSS and no build step.
- `icon.svg`: the Steward app icon, copied from the desktop app's Tauri icons.
- `CNAME`: the custom domain GitHub Pages serves.

## Preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

GitHub Pages publishes `main` at the repository root, so a push to `main` rebuilds the site.

Settings → Pages: source "Deploy from a branch", branch `main`, folder `/ (root)`, custom domain `steward.inbrief.sh`. Turn on "Enforce HTTPS" once the certificate is issued.

DNS, in Cloudflare for the `inbrief.sh` zone:

| Type  | Name    | Target                | Proxy status |
| ----- | ------- | --------------------- | ------------ |
| CNAME | steward | inbrief-inc.github.io | DNS only     |

Keep the record on "DNS only" (grey cloud). GitHub has to reach its own servers directly to issue the HTTPS certificate.
