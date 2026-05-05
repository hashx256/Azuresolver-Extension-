<p align="center">
  <img src="logo.jpg" alt="AzureSolver Logo" width="150"/>
</p>

# 🧩 AzureSolver Extension v2.0

> **Instantly detect & extract CAPTCHA parameters — no more manual digging.**

[![Version](https://img.shields.io/badge/version-2.0.0-blue?style=flat-square)](https://github.com/yourusername/azuresolver-extension)
[![Manifest](https://img.shields.io/badge/Manifest-v3-green?style=flat-square)](https://developer.chrome.com/docs/extensions/mv3/)
[![Platform](https://img.shields.io/badge/Browser-Chromium-orange?style=flat-square)]()
[![AzureSolver](https://img.shields.io/badge/Powered%20by-AzureSolver.com-6C63FF?style=flat-square)](https://azuresolver.com)

---

## 📎 What is this?

The **AzureSolver Extension** is a browser extension that automatically detects and extracts all CAPTCHA parameters from any website — giving you the exact, ready-to-use API payload for [AzureSolver](https://azuresolver.com) in one click.

No more guessing whether it's v2 or v3. No more digging through page source. No more wasted time.

---

## ✅ Supported CAPTCHA Types

| CAPTCHA | Variants Detected |
|---|---|
| 🔵 **reCAPTCHA v2** | Checkbox · Invisible · Explicit |
| 🟣 **reCAPTCHA v3** | Standard · Score-based |
| 🏢 **reCAPTCHA Enterprise** | v2 Enterprise · v3 Enterprise |
| 🟠 **Cloudflare Turnstile** | Standard |

---

## ⚡ How It Works

```
1. Install the extension
2. Visit any site with a CAPTCHA
3. Trigger the target action (login, register, form submit, etc.)
4. Click the extension icon
5. Copy the ready-to-use AzureSolver API params → done
```

The extension uses an **upgrade-wins detection engine** — meaning if multiple signals are detected, it always resolves to the most accurate CAPTCHA type. For example, a page that initially looks like reCAPTCHA v2 Checkbox will be correctly upgraded to reCAPTCHA v3 or Enterprise if stronger signals are found later.

---

## 🔧 Detection Engine Highlights

- 🧠 **Priority-based type resolution** — avoids misidentification when multiple CAPTCHA signals fire
- 📡 **Intercepted network requests** — catches sitekeys from `anchor`, `bframe`, and `/enterprise` endpoints
- 🔍 **Deep DOM scanning** — inspects `.g-recaptcha`, `.h-captcha`, `.cf-turnstile`, `data-sitekey` attributes and more
- 🔄 **Auto-upgrades detections** — e.g. upgrades `v2 Checkbox → Enterprise v3` on reload signals
- 🌐 **Works on all URLs** — including iframes and dynamically loaded CAPTCHA widgets

---

## 🚀 Installation (Manual / Developer Mode)

1. Download or clone this repository
2. Open Chrome → `chrome://extensions/`
3. Enable **Developer Mode** (top right toggle)
4. Click **Load Unpacked**
5. Select the `Azuresolver-extension 2.0/` folder
6. Done — the extension is now active on all sites

> ⚠️ Chrome Web Store release coming soon. Stay tuned!

---

## 🖼️ Extension Popup

When you click the extension icon after visiting a CAPTCHA-protected page, you'll see:

- ✅ Detected CAPTCHA type
- 🔑 Extracted site key
- 🌍 Current page URL
- 📋 One-click copy of the full AzureSolver API request parameters

---

## 📸 Screenshots

<p align="center">
  <img src="extension%20example.jpg" alt="AzureSolver Extension — Popup Overview" width="280"/>
  &nbsp;&nbsp;&nbsp;
  <img src="extension%20example%202.jpg" alt="AzureSolver Extension — Detection Detail" width="280"/>
</p>

<p align="center">
  <em>Left: Full API params view with one-click Copy JSON &nbsp;|&nbsp; Right: Detection detail with site key & explanation</em>
</p>

---

## 📦 File Structure

```
Azuresolver-extension 2.0/
├── manifest.json       # Manifest v3 config
├── background.js       # Service worker — request interception & coordination
├── content.js          # DOM scanner — detects CAPTCHA signals across all pages
├── injected.js         # Page-world script — intercepts grecaptcha/turnstile calls
├── popup.html          # Extension UI
├── popup.js            # Popup logic — renders detected params
└── icons/
    ├── icon16.png
    ├── icon48.png
    └── icon128.png
```

---

## 🔐 Permissions Used

| Permission | Purpose |
|---|---|
| `activeTab` | Read current tab's URL and content |
| `scripting` | Inject detection scripts into pages |
| `storage` | Store detected CAPTCHA data per tab |
| `webRequest` | Intercept CAPTCHA network requests |
| `tabs` | Communicate between popup and active tab |

---

## 🌐 API Integration

Once you have the extracted parameters, plug them directly into the [AzureSolver API](https://azuresolver.com/docs):

```json
{
  "clientKey": "YOUR_API_KEY",
  "task": {
    "type": "ReCaptchaV3TaskProxyless",
    "websiteURL": "https://example.com",
    "websiteKey": "<extracted_by_extension>",
    "pageAction": "login"
  }
}
```

> The extension generates this payload for you automatically.

---

## 🛣️ Roadmap

- [x] reCAPTCHA v2 / v3 / Enterprise detection
- [x] Cloudflare Turnstile detection
- [x] Priority-based upgrade engine
- [x] One-click param copy
- [ ] Chrome Web Store release
- [ ] Firefox support
- [ ] Auto-submit to AzureSolver API directly from popup
- [ ] Support for GeeTest / FunCaptcha

---

## 🤝 Related

- 🌐 [AzureSolver.com](https://azuresolver.com) — CAPTCHA solving API
- 📖 [API Documentation](https://azuresolver.com/docs)
- 💬 Support — available via the platform

---

<p align="center">Built with ❤️ by the AzureSolver Team</p>
