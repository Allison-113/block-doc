# Block Doc

A field canvassing day log — single-page web app, no backend. All data lives on your own device (IndexedDB); nothing is sent anywhere.

Installable as a PWA: open the page, then **Add to Home Screen**. Works offline.

## Files
- `index.html` — the whole app
- `manifest.webmanifest` — PWA manifest
- `sw.js` — service worker (offline shell)
- `icon-*.png`, `icon.svg` — app icons
- `.github/workflows/pages.yml` — deploys to GitHub Pages on every push to `main`

## Deploying (edit-from-anywhere workflow)

The site is hosted on **GitHub Pages** and redeploys automatically whenever
`main` changes. So the field loop is:

1. Make a change (e.g. from a Claude Code session on your phone).
2. Commit and push to `main`.
3. The **Deploy to GitHub Pages** workflow runs, stamps the service worker's
   cache name with the commit SHA, and publishes the site.
4. Reload the page — the new cache name forces installed PWAs to pick up the
   change, so you see edits without manually clearing anything.

### One-time setup

For the cache-busting deploy to take over, set the Pages **source** to GitHub
Actions: repo **Settings → Pages → Build and deployment → Source → GitHub Actions**.
(Until then, Pages keeps deploying from the `main` branch directly, which still
works but does not auto-bump the cache.)
