# Qaza Tracker

Track your qaza prayer debt (including safar qaza), log repayments, and mark missed
prayers on a calendar. Single-page app, no backend, all data stored in your browser via
localStorage.

## Files

Upload all of these to the repo root:

`index.html`, `manifest.json`, `sw.js`, `icon.svg`, `icon-192.png`, `icon-512.png`,
`icon-192-maskable.png`, `icon-512-maskable.png`, `apple-touch-icon.png`

## Deploy to GitHub Pages

1. Create a new GitHub repo (public, or private with Pages enabled on your plan) and upload
   every file above to the repo root.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch", pick your
   default branch (e.g. `main`) and folder `/ (root)`, then **Save**.
4. Wait a minute or two, then open the URL GitHub shows you
   (usually `https://<your-username>.github.io/<repo-name>/`).

The URL is a real HTTPS site, which a PWA needs (service workers only work over HTTPS or
localhost).

## Install it on your phone

**iPhone (Safari)**
1. Open the URL in Safari (must be Safari for the install step).
2. Tap Share → **Add to Home Screen** → **Add**.

**Android (Chrome)**
1. Open the URL in Chrome.
2. Tap ⋮ → **Add to Home screen** / **Install app**.

## Notes

- **Data stays on-device.** Each browser, and the installed home-screen copy, has its own
  separate storage. Use Settings → Import / Export to back up and move data.
- **Importing** only accepts Qaza Tracker data. Files from other apps are rejected.
- **Corrupt data protection.** If saved data can't be read, the app warns you and blocks
  saving until you import a backup or reset, so the damaged copy isn't overwritten.
- **Offline use:** `sw.js` caches the app so it opens with no signal, fetching a fresh copy
  when online.
- **Sharing a github.io domain with other apps:** the service worker only manages caches
  starting with `qaza-tracker-`. Storage keys all start with `salah_`; make sure any other
  app on the same domain uses different key names.
- **Updating:** replace `index.html` (and bump `CACHE` in `sw.js`, e.g. `qaza-tracker-v2`,
  if you change cached files), then push. The phone picks it up next time it opens online;
  it can take one extra reopen to take effect.
