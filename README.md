# owvie-website

Marketing site for **Owvie** — kids' bedtime audio-stories app.

- `index.html` — the full marketing site (Home · For Parents · Pricing · Support · About, plus Privacy and Terms), a single-page app with a hash router. Design derived from the app's "Magical Night" brand; fonts (Anthelion, Nunito) and key art embedded.
- `404.html` — sends unknown paths back to the home page, keeping the `#/…` route.
- `.well-known/` — Apple `apple-app-site-association` and Android `assetlinks.json` (universal / app links).
- `_headers` — Cloudflare Pages response headers (JSON content type for the extensionless Apple file).
- `internal/` — internal previews, marked `noindex`.

## Hosting

Hosted on **Cloudflare Pages**, project `owvie-website` (`owvie-website.pages.dev`), in the same Cloudflare account that holds the `owvie.com` DNS zone. It is a direct-upload project with no build step.

It moved off GitHub Pages in November 2026: once `owvie.com` was proxied through Cloudflare, GitHub could no longer renew its own certificate for the domain.

A separate Cloudflare Worker (in the `owvie-v1` repo, `cloudflare/skan-report-attribution`) owns `owvie.com/.well-known/skadnetwork/report-attribution*`. It is not part of this site.

## Deploy

Push to `main` → the `Deploy to Cloudflare Pages` workflow publishes the site files. It needs two repository secrets: `CLOUDFLARE_API_TOKEN` (a token with the "Cloudflare Pages: Edit" permission) and `CLOUDFLARE_ACCOUNT_ID`.

To deploy by hand from a machine logged in with `npx wrangler login`:

```sh
mkdir _site && cp -R index.html 404.html robots.txt _headers .well-known internal _site/
npx wrangler pages deploy _site --project-name owvie-website --branch main
rm -rf _site
```

A new top-level file or folder must be added to the copy list in both places, or it will not be published.

`CNAME` and `.nojekyll` are left over from GitHub Pages and can be deleted once GitHub Pages is switched off for this repo.
