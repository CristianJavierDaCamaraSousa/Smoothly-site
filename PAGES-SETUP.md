# Activar GitHub Pages (una vez)

1. Crea el repo en GitHub: **CristianJavierDaCamaraSousa/Smoothly-site** (público, sin README si vas a empujar esta carpeta).

2. Desde tu máquina:

```powershell
cd c:\Smoothly\Smoothly-site
git init
git add .
git commit -m "Initial public landing"
git branch -M main
git remote add origin https://github.com/CristianJavierDaCamaraSousa/Smoothly-site.git
git push -u origin main
```

3. En GitHub: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/docs**
   - Save

4. Espera 1–3 minutos y abre en incógnito:  
   https://cristianjavierdacamarasousa.github.io/Smoothly-site/

5. Sustituye las URLs en `docs/version.json` (ver `docs/LEMON-SQUEEZY.md`) y vuelve a hacer push.
