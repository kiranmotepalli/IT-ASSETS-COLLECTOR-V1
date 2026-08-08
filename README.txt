NSPIRA IT ASSETS COLLECTOR — SETUP GUIDE
==================================

WHAT THIS IS
A lightweight offline data-collection app for field staff to log branch IT
assets from their Android phone. It is a "PWA" (installable web app) —
not a Play Store app, but it installs and behaves like one: home screen
icon, full-screen, works with no internet connection.

FILES IN THIS FOLDER
  index.html      the app
  manifest.json   tells Android how to install it (icon, name, colors)
  sw.js           service worker — makes it work offline
  icon-192.png    app icon (small)
  icon-512.png    app icon (large)

-----------------------------------------------------------------
OPTION A — Quickest test (no hosting, just for you to try now)
-----------------------------------------------------------------
Open index.html directly in Chrome on your Android phone. The form and CSV
export work immediately. Full "Install app" / offline behaviour needs
Option B, because Android requires these files served over a real web
address (not opened from a local file) to install a PWA properly.

-----------------------------------------------------------------
OPTION B — Proper install for your team (recommended, free, ~10 min)
-----------------------------------------------------------------
Host these 5 files on any free static host so they get a real https:// URL.
Easiest option — GitHub Pages:

  1. Create a free GitHub account if you don't have one.
  2. Create a new repository, e.g. "assetline-collector".
  3. Upload all 5 files in this folder to the repository (drag and drop
     on github.com works fine, no coding needed).
  4. In the repo, go to Settings > Pages > set Source to
     "Deploy from branch", branch "main", folder "/ (root)". Save.
  5. GitHub gives you a URL like:
       https://yourusername.github.io/assetline-collector/
  6. Open that URL on an Android phone in Chrome. You'll see an
     "Install app" banner inside the app (or use Chrome's menu ⋮ >
     "Add to Home screen" / "Install app").
  7. Share that same URL with staff at other branches — each person
     installs it once on their own phone.

(Netlify or Vercel work the same way if you prefer them — drag-and-drop
the folder onto netlify.com/drop for the fastest option of all.)

-----------------------------------------------------------------
HOW DATA COLLECTION WORKS
-----------------------------------------------------------------
- Each phone stores its own entries locally (nothing is uploaded
  automatically — there's no shared server here).
- Field staff fill in the "Add" tab per asset, review what they've
  logged under "Entries", then hit "Export" to generate a CSV.
- That CSV uses the exact same column layout as the ASSETLINE web app's
  Import/Merge tab (Branch, Floor, Room / Area, Asset Category, Asset
  Name, Make, Model, Serial No, Quantity, Status, Remarks) — so it can
  be shared back (WhatsApp/email/Drive) and pasted straight into
  ASSETLINE to merge into the central database.
- Data survives closing the app and going offline. It only clears if
  someone taps "Clear all entries" or clears the browser's site data.

-----------------------------------------------------------------
IF YOU EVENTUALLY WANT LIVE MULTI-DEVICE SYNCING
-----------------------------------------------------------------
This version is intentionally offline/local-only for reliability at
branches with poor signal. If you'd rather have all branch phones write
straight into one shared live database (instead of exporting/merging
CSVs), that needs a small backend (e.g. Google Sheets API, Firebase, or
a simple hosted database) — a bigger step, happy to help set that up
when you're ready.
