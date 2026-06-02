# Publishing .exe files for the landing page

Build artifacts are **not** committed inside `docs/`. The site reads [`version.json`](version.json) and download buttons point to public URLs.

You have two options:

---

## Option A — GitHub Releases on **Smoothly-site** (simplest)

Upload the `.exe` files to a Release in this repo (no source code). Users download from GitHub’s CDN; the landing page remains your marketing site.

### 1. Build the .exe files (private Smoothly repo)

```powershell
cd c:\Smoothly
.\scripts\build-installer.ps1 -Version 1.1.0
```

Output:

- `dist\SmoothlySetup-1.1.0.exe` — installer  
- `publish\Smoothly.exe` — rename or copy as `Smoothly-1.1.0-portable.exe`

Requires [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) and [Inno Setup 6](https://jrsoftware.org/isinfo.php).

### 2. Create a GitHub Release

1. Open https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases  
2. **Draft a new release**  
3. Tag: `v1.1.0` (with the `v` prefix)  
4. Title: `Smoothly 1.1.0`  
5. Drag both `.exe` files into **Release assets**  
6. **Publish release**

### 3. Download URLs

Format (replace version and exact file names):

```text
https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases/download/v1.1.0/SmoothlySetup-1.1.0.exe
https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases/download/v1.1.0/Smoothly-1.1.0-portable.exe
```

On the Release page, right-click each asset → **Copy link address**.

### 4. Update `version.json`

Edit `docs/version.json`, paste the URLs into `installer.url` and `portable.url`, then:

```powershell
cd c:\Smoothly\Smoothly-site
git add docs/version.json
git commit -m "chore: download URLs for v1.1.0"
git push
```

Within about a minute the landing page will enable the download buttons.

---

## Option B — Lemon Squeezy (commercial plan)

1. Upload the `.exe` files to your product on [Lemon Squeezy](https://www.lemonsqueezy.com).  
2. Copy the download URLs from the dashboard.  
3. Paste them into `version.json` and push (same as above).

Details: [LEMON-SQUEEZY.md](LEMON-SQUEEZY.md).

---

## Quick script (Smoothly repo)

```powershell
.\scripts\update-site-version.ps1 -Version 1.1.0 `
  -InstallerUrl "https://github.com/.../SmoothlySetup-1.1.0.exe" `
  -PortableUrl "https://github.com/.../Smoothly-1.1.0-portable.exe"
```

Then commit and push in **Smoothly-site**.

---

## What not to do

- Do not `git add` `.exe` files under `docs/` (large files, poor practice).  
- Do not point end users at ZIP assets from the private code repo’s release tag.
