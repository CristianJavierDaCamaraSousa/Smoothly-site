# Smoothly Privacy Policy

**Last updated:** June 2026

Smoothly is designed to run locally on your PC. We do not operate user accounts or analytics servers for the app.

## What the app does on your computer

| Data | Purpose | Leaves your PC? |
|------|---------|-----------------|
| Settings (`%AppData%\Smoothly\settings.json`) | Your preferences and license state | No |
| Trial start date (registry `HKCU\Software\Smoothly`) | Enforce 14 day trial | No |
| Log files (`%AppData%\Smoothly\logs`) | Troubleshooting | No |
| Global mouse hook | Smooth scrolling | No |

## Network access

Smoothly may connect to the internet when:

- **Check for updates** is enabled (reads version manifest from the public website)
- You **activate or validate** a Payhip license key (calls Payhip's license API with your key)
- You **deactivate** a Payhip license on this PC (decreases usage via Payhip API)
- You click **Buy**, **Support**, **EULA**, or **download update** (opens your browser)

We do not run our own license server. Payhip processes license API requests under their privacy policy.

## License keys

- **Payhip keys:** sent to Payhip for verification and usage tracking; a device identifier (hash of PC name + Windows user) is stored locally to enforce one device per license.
- **Legacy `SMOOTH` keys:** validated **offline** on your PC only; we do not receive them unless you contact support.

## Payment

Purchases are processed by Payhip. Their privacy policy applies to checkout.

## Contact

Questions: https://github.com/CristianJavierDaCamaraSousa/Smoothly-site/issues
