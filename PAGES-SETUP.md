# Enable GitHub Pages (one-time)

1. Create the repo on GitHub: **CristianJavierDaCamaraSousa/Smoothly-site** (public; skip adding a README if you will push this folder).

2. From your machine:

```powershell
cd c:\Smoothly\Smoothly-site
git init
git add .
git commit -m "Initial public landing"
git branch -M main
git remote add origin https://github.com/CristianJavierDaCamaraSousa/Smoothly-site.git
git push -u origin main
```

3. On GitHub: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/docs**
   - Save

4. Wait 1–3 minutes, then open in a private/incognito window:  
   https://cristianjavierdacamarasousa.github.io/Smoothly-site/

5. Replace the placeholder URLs in `docs/version.json` (see `docs/LEMON-SQUEEZY.md` or `docs/DOWNLOADS.md`) and push again.
