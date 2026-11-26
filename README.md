# KAS KEUANGAN — Open-source weekly cashflow tracker (web app)

An open-source web application built by [@dmonziee](https://github.com/dmonziee): a weekly income & expense tracker (pemasukan & pengeluaran mingguan) that runs entirely as a static web app. Non-commercial, personal software project — the code is public on GitHub and anyone can read, run, or fork it.

- 🌐 Live demo: https://dmonziee.github.io/monzie-keuangan/
- 📱 APK Android: `KAS-Keuangan-1.2.apk` (WebView wrapper, paket `app.monzie.keuangan`)
- 📄 License: MIT — see [LICENSE](LICENSE)
- Applying for the subdomain `monzie.is-a.dev` as this project's permanent address (not live yet).

## Tech stack

- **Frontend:** vanilla HTML/CSS/JS, single-file app (`index.html`), no build step, no framework
- **Sync & auth:** Firebase Firestore (project `rekapan-monzie`, region asia-southeast1, Spark free plan) + Firebase Email/Password Auth
- **Hosting:** GitHub Pages (static)
- **Android:** WebView wrapper built manually with `aapt2` (see `android/`, Gradle is not used)

## Run locally

```bash
# Option 1: open the file directly
open index.html

# Option 2: serve it (recommended, so fetch works the same as in production)
python3 -m http.server 8000
# then open http://localhost:8000
```

Without a Firebase config the app runs in **Mode Lokal** (localStorage, key `monzie-keuangan-v1`) with a clear banner. To enable sync, inject the Firebase web config into `index.html` with `./inject-firebase-config.sh firebase-config.json` (see `V2-README.md`).

## Project structure

```
index.html        # live app (Firebase config injected)
index-v2.html     # source template (placeholder config — edit this, then inject)
inject-firebase-config.sh  # injects firebase-config.json into index-v2.html → index.html
firebase-config.json       # Firebase web config (public client keys, mode 600)
V2-README.md      # Firestore schema, rules, injection steps, test notes
android/          # Android WebView wrapper source + manual build script
LICENSE           # MIT License
```

## Features

- Weekly recap (Monday–Sunday): total pemasukan, pengeluaran, saldo, per-day chart, per-day list
- Week navigation (prev/next, jump to date, "Minggu Ini")
- Filter by type/category + search notes
- **Public (no login):** read-only monitoring — recap, totals, list, chart
- **Admin:** login with Firebase email + password (`kingmusang578@gmail.com`) — add/edit/delete transactions, export/import JSON, export CSV, delete demo data, upload local data to Firebase, change password
- In-app confirm modal + toast (no native `confirm()`/`alert()` — required for the Android WebView)

## Data & sync

Data is stored in **Firebase Firestore** (project `rekapan-monzie`). Anyone can read without login; only a signed-in admin can write (Firestore rules: `read: true`, `write: request.auth != null`). Admin changes appear on all devices within seconds (live sync). If Firebase is unreachable or the config is not filled in, the app falls back to **Mode Lokal** (browser localStorage) with a clear banner, and the last data is kept as an offline cache.

Demo data for the week 23–29 Nov 2026 is included on first open and can be deleted by the admin in Settings. The admin can migrate local data to Firebase via Settings → "Upload data lokal ke Firebase".

## Contributing

Issues and pull requests are welcome — open one on [github.com/dmonziee/monzie-keuangan](https://github.com/dmonziee/monzie-keuangan). Please keep changes small and test the app locally before submitting.
