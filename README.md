# Matheasy — Marketing Website

Static marketing site for **Matheasy**, the app that scans any math problem and returns
step-by-step solutions, visual explanations, and AI tutoring (Numi).

Live domain: **https://getmatheasy.com**

## Pages

| URL | File | Purpose |
|-----|------|---------|
| `/` | `Matheasy Landing.dc.html` | Landing / home |
| `/support` | `support.dc.html` | Help center + FAQ |
| `/privacy` | `privacy.dc.html` | Privacy policy |
| `/terms` | `terms.dc.html` | Terms & conditions |
| `/delete-account` | `delete-account.dc.html` | Account deletion instructions |

Clean URLs are provided by `vercel.json` rewrites; the `.dc.html` files are the sources.

## Stack

These pages are a **`dc-runtime` design-tool export**, not a bundled framework app.
Each page is static HTML whose `<x-dc>` template is rendered client-side by `support.js`
(the vendored dc-runtime, which loads React from a CDN). There is **no build step**.

> ⚠️ `support.js` is generated/vendored — do not hand-edit it.

## Deploy (Vercel)

1. Import this repo into Vercel.
2. Framework preset: **Other** (no build command, output = repo root).
3. `vercel.json` handles: root → landing rewrite, clean URLs + 301 redirects,
   long-lived asset caching, and security headers.

No environment variables are required.

## Structure

```
.
├── Matheasy Landing.dc.html   # home
├── privacy / terms / support / delete-account .dc.html
├── support.js                 # vendored dc-runtime (do not edit)
├── vercel.json                # rewrites, redirects, headers
├── 404.html                   # custom not-found page
├── robots.txt · sitemap.xml · site.webmanifest
└── assets/                    # images, icons, video, app-store badges
```

## Before public launch

- [ ] Replace the App Store / Google Play badge links (currently `#`) with real store URLs.
- [ ] Add real social profile URLs (or remove the icons).

## SEO / performance notes

- Head metadata (title, description, canonical, Open Graph, Twitter, JSON-LD) is in the
  **static `<head>`** of every page so it is crawlable without JS.
- Product videos are optimized H.264 sized for the phone mockups.
- Images are optimized JPGs; icons are generated from `assets/logo-w.png`.
