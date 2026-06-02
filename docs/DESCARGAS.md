# Cómo publicar los .exe para la landing

Los archivos **no** se suben como carpetas dentro de `docs/`. La página lee [`version.json`](version.json) y los botones apuntan a URLs públicas de descarga.

Tienes dos opciones:

---

## Opción A — GitHub Releases en **Smoothly-site** (más simple)

Solo subes los `.exe` a un Release de este repo (sin código fuente). Los usuarios descargan desde GitHub CDN; la landing sigue siendo tu página.

### 1. Generar los .exe (en el repo privado Smoothly)

```powershell
cd c:\Smoothly
.\scripts\build-installer.ps1 -Version 1.1.0
```

Salida:

- `dist\SmoothlySetup-1.1.0.exe` — instalador  
- `publish\Smoothly.exe` → renómbralo o cópialo como `Smoothly-1.1.0-portable.exe`

(Requiere [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) e [Inno Setup 6](https://jrsoftware.org/isinfo.php).)

### 2. Crear un Release en GitHub

1. Abre https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases  
2. **Draft a new release**  
3. Tag: `v1.1.0` (con `v`)  
4. Título: `Smoothly 1.1.0`  
5. Arrastra los dos `.exe` a **Release assets**  
6. **Publish release**

### 3. URLs de descarga

Formato (sustituye versión y nombre exacto del archivo):

```text
https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases/download/v1.1.0/SmoothlySetup-1.1.0.exe
https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/releases/download/v1.1.0/Smoothly-1.1.0-portable.exe
```

En la página del Release, clic derecho en cada asset → **Copiar enlace de descarga**.

### 4. Actualizar `version.json`

Edita `docs/version.json`, pega las URLs en `installer.url` y `portable.url`, luego:

```powershell
cd c:\Smoothly\Smoothly-site
git add docs/version.json
git commit -m "chore: download URLs for v1.1.0"
git push
```

En ~1 minuto la landing mostrará los botones activos.

---

## Opción B — Lemon Squeezy (la del plan comercial)

1. Sube los `.exe` al producto en [Lemon Squeezy](https://www.lemonsqueezy.com).  
2. Copia las URLs de descarga del panel.  
3. Pégalas en `version.json` y haz push (igual que arriba).

Detalle: [LEMON-SQUEEZY.md](LEMON-SQUEEZY.md).

---

## Script rápido (repo Smoothly)

```powershell
.\scripts\update-site-version.ps1 -Version 1.1.0 `
  -InstallerUrl "https://github.com/.../SmoothlySetup-1.1.0.exe" `
  -PortableUrl "https://github.com/.../Smoothly-1.1.0-portable.exe"
```

Luego commit y push en **Smoothly-site**.

---

## Qué no hacer

- No hagas `git add` de `.exe` dentro de `docs/` (pesa, es mala práctica).  
- No uses el ZIP del **tag** en el repo de código privado para usuarios finales.
