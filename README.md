# Qaza Tracker (Salah Tracker v2)

A small offline-capable app that tracks qaza debt, repayments, and the days you missed prayers. Data stays in your browser on your own device.

## Files
- `index.html` – the whole app
- `manifest.json` – install details (name, icon, colours)
- `sw.js` – offline caching (cache name `salah-v5`; bump it if an old version keeps showing)
- `icon.svg` – app icon
- `salah_tracker_qaza_2026-09-30.json` – your data, trimmed for this version

## Screens
- **Qaza** – owed and safar counters per prayer (+/-, or type a number), repayment logger, overall progress.
- **Calendar** – red dots mark days with missed prayers. Tap a day, then tap a prayer to mark or unmark it as missed. Marking adds 1 to that prayer's qaza debt; unmarking removes it.
- **Stats** – qaza-free streak, prayers repaid this month, and a 6-month repayment chart.
  - Streak = consecutive days with no missed prayer marked on the calendar and no qaza added on the Qaza page (+ button or typing a higher number). Current streak counts up to and including today. Longest streak shows its start and end dates. Counting starts from your earliest recorded day.
- **Settings** – import/export, install, reset.

## Moving over from the old version
1. Export a backup from the old app first (Settings, Import / Export, Download File).
2. Replace the old files with these, and open the app in the same browser as before.
3. If it looks empty, use Settings, Import / Export, Import File and pick the JSON in this folder. Your original full export also imports fine.
4. The first time it opens, it keeps a one-time safety copy of whatever was stored (`salah_safety_...` keys).

## Where data lives
Browser storage key `salah_tracker_v1`. Old prayer logs, notes and prayer times in that key are left untouched and simply ignored, so nothing is lost. Clearing site data, private mode, or another browser or device means an empty app until you import a backup. Export regularly.

## Serving it locally
`python -m http.server 4174 --bind 127.0.0.1` from this folder, then open `http://127.0.0.1:4174/index.html` (install and offline mode need a proper URL, not a double-clicked file).
