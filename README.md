# Kanza PCC 3.0 — iPhone app (PWA)

This folder is a self-contained Progressive Web App of the Portfolio Command Centre. Once hosted, you "Add to Home Screen" on your iPhone and it behaves like a native app — full-screen, own icon, works offline (showing the last snapshot).

**Files (keep them together, all in one folder):**
- `index.html` — the command centre (the app)
- `manifest.webmanifest` — app name, icon, colours
- `sw.js` — service worker (offline + caching)
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` — app icons

---

## Step 1 — Put it on GitHub Pages

1. Go to https://github.com → sign in → **New repository**. Name it e.g. `pcc-app`. Set it **Public** (Pages needs public on the free tier). Click **Create repository**.
2. On the new repo page, click **uploading an existing file** (or **Add file → Upload files**).
3. Drag in **all 5 files + this README** from this folder. Commit.
4. Go to the repo's **Settings → Pages**.
5. Under **Build and deployment → Source**, choose **Deploy from a branch**. Branch: **main**, folder: **/ (root)**. Save.
6. Wait ~1 minute. Pages will show your URL:
   `https://<your-username>.github.io/pcc-app/`

That URL is your app. Open it in Safari on your iPhone.

## Step 2 — Install on your iPhone (iOS 26/27)

1. Open the Pages URL in **Safari** (must be Safari for install to work).
2. Tap the **Share** button (square with the up-arrow).
3. Scroll down → **Add to Home Screen** → **Add**.
4. The **PCC 3.0** icon appears on your home screen. Open it — it launches full-screen, no Safari bars.

## Updating the app later

When the nightly run re-bakes the panels, re-export `index.html` and re-upload it to the repo (replace the file). The service worker version is `pcc3-v1` in `sw.js`; if a refresh doesn't show changes, bump it to `pcc3-v2` and re-upload `sw.js` to force the cache to update.

---

## What works offline vs live

- **Works offline / on the icon:** the whole command centre, the Cycle Engine (its phase/flow/date logic recomputes in the page each open), and the last nightly snapshot of every panel.
- **Not live in this app:** the nightly *schedule* itself (that runs as a Claude/Cowork agent task — it keeps running on its own and re-bakes the panels), and live iTrust **portfolio/balance** (PIN-gated; only refreshes when the nightly agent reads it). This PWA is a fast, installable **viewer** of the latest results — it does not log in or trade.

Read-only throughout · subordinate to KCP-IPS-2026-001 · not personalised investment advice.
