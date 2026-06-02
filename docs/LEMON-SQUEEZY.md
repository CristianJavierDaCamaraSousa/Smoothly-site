# Lemon Squeezy — trial download URLs

Host the Windows builds on Lemon Squeezy and paste the public download URLs into `version.json`.

## Setup (one time)

1. [Lemon Squeezy](https://www.lemonsqueezy.com) → **Products** → your Smoothly product (or a **$0 trial** product).
2. Attach **`SmoothlySetup-x.x.x.exe`** (installer) and **`Smoothly-x.x.x-portable.exe`** (portable) as digital files.
3. Copy each file’s **direct download URL** from the product / variant file settings.

## After each release

1. Upload the new `.exe` files from the private repo’s Release workflow (or local `scripts/build-installer.ps1`).
2. Edit [`version.json`](version.json):
   - `version` — semver without `v` (e.g. `1.2.0`)
   - `publishedAt` — ISO date
   - `installer.name` / `portable.name` — file names shown on the landing page
   - `installer.url` / `portable.url` — Lemon Squeezy CDN URLs
3. Commit and push to `main`; GitHub Pages updates in about a minute.

Optional: set GitHub Actions secrets on the **private** Smoothly repo (`SITE_REPO_TOKEN`, `LS_INSTALLER_URL`, `LS_PORTABLE_URL`) so the Release workflow updates this file automatically.
