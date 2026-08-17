# owvie-website

Marketing site for **Owvie** — kids' bedtime audio-stories app.

- `index.html` — the full marketing site (Home · For Parents · Pricing · Support · About), a single-page app with a hash router. Design derived from the app's "Magical Night" brand; fonts (Anthelion, Nunito) and key art embedded.
- Hosted on **GitHub Pages** (this repo). DNS for `owvie.com` is managed at GoDaddy and points at GitHub Pages.
- `.nojekyll` keeps Pages from running Jekyll, so a future `/.well-known/` (Apple `apple-app-site-association`, Android `assetlinks.json`) and `/privacy`, `/terms` are served verbatim.

## Deploy
Push to `main` → GitHub Pages publishes automatically.

## TODO before pointing owvie.com here
- Add real `/privacy` and `/terms` pages.
- Add `/.well-known/apple-app-site-association` (Apple Team ID + `com.zznius.owvie`) and `/.well-known/assetlinks.json` (Play app-signing SHA-256) to restore universal / app links.
- Replace placeholder testimonials on the home page with real reviews.
- Add `CNAME` file (`owvie.com`) at the flip step.
