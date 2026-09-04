# CLAUDE.md — gnosisai-web

## Project Overview

Static landing site for the KnowItOwl! iOS/watchOS voice Q&A app. Hosted on GitHub Pages with a custom domain (`knowitowl.sandybrook.io`). Three pages: home (app marketing), privacy policy (legal/compliance), and support (contact form + FAQ).

- **Domain:** knowitowl.sandybrook.io (CNAME)
- **Hosting:** GitHub Pages (static HTML/CSS/JS)
- **Repo:** `cloudreyes/gnosisai-web` — local path: `~/Repos/gnosisai-web`
- **Company:** Sandy Brook DevWorks LLC (Texas)
- **Contact:** hello@sandybrook.io

## Related Repos

- **iOS/watchOS app:** `cloudreyes/gnosisai-iosapp` — local path: `~/Repos/gnosisai-iosapp`
- **Backend:** `cloudreyes/gnosisai-backend` — local path: `~/Repos/gnosisai-backend`

## Tech Stack

- **HTML/CSS/JS** — No build step, no framework, no bundler
- **Hosting:** GitHub Pages (static, served from `main` branch root)
- **Domain:** Custom domain via `CNAME` file (`knowitowl.sandybrook.io`)
- **SEO:** `sitemap.xml`, `robots.txt`, Open Graph + Twitter Card meta tags, JSON-LD structured data
- **Fonts:** Google Fonts (Inter)
- **Icons:** Favicon set in `favicon/` directory (multiple sizes + `site.webmanifest`)
- **Analytics:** None (privacy-first)

## Pages

| File | URL | Purpose |
|------|-----|---------|
| `index.html` | `knowitowl.sandybrook.io/` | Marketing landing page — app features, screenshots, App Store link |
| `privacy.html` | `knowitowl.sandybrook.io/privacy.html` | Privacy policy — 14 sections, CCPA/CPRA compliant |
| `support.html` | `knowitowl.sandybrook.io/support.html` | Contact form (Formspree) + FAQ sidebar |

## Project Structure

```
gnosisai-web/
  CLAUDE.md               # This file
  README.md                # Public-facing documentation
  CNAME                    # Custom domain: knowitowl.sandybrook.io
  robots.txt               # Allow all crawlers, sitemap reference
  sitemap.xml              # 3 URLs (index, privacy, support)
  index.html               # Landing page
  privacy.html             # Privacy policy (14 sections)
  support.html             # Support/contact page with FAQ
  favicon/
    apple-touch-icon.png   # 180x180
    favicon-96x96.png      # 96x96
    favicon-32x32.png      # 32x32
    favicon-16x16.png      # 16x16
    favicon.ico            # Multi-size ICO (16, 32, 48)
    favicon.svg            # SVG favicon
    site.webmanifest        # PWA manifest (name, icons, theme)
    safari-pinned-tab.svg  # Safari pinned tab icon
    web-app-manifest-*.png # PWA manifest icons (192, 512)
    android-chrome-*.png   # Android home screen icons
```

## Key Content Details

### Credit System (must stay in sync with iOS app)

- **Welcome credits:** 20 credits for new users (one-time)
- **Monthly free credits:** 5 credits per month
- **Credit packs (consumable, never expire):**
  - Standard: 30 credits
  - Popular: 60 credits
  - Power: 120 credits
  - App Store Connect supplies the localized storefront prices

### Privacy Commitments (reflected in privacy.html)

- The app does not request a name, email address, phone number, contacts, advertising identifier, or location
- Automatic identity uses Apple's signed App Transaction to derive a one-way hashed, app-scoped user ID; there is no login screen
- User data is **never** sold, rented, or shared with data brokers or aggregators
- User data is **never** used for AI model training
- **Client-side encryption for saved content** — AES-256-GCM via Apple CryptoKit; Firestore/Storage only store ciphertext. Real-time AI processing data is sent over HTTPS in readable form
- **User-scoped encryption keys** — stored in iCloud Keychain, never leave user's devices
- Data stored in Firebase (Firestore + Storage) in `nam5` (multi-region US, 99.999% SLA)
- Firebase Auth sessions are minted by the authenticated backend for the app-scoped App Store identity
- Credit operations and signed StoreKit transaction validation run through the .NET v4 backend
- Delete Personal Data removes messages, audio, the encryption key, pending interaction records, and the Firebase user; credit balances, ledgers, and redeemed transaction claims remain to prevent duplicate grants
- Apple App Store/Xcode provides native crash and hang reports; privacy-filtered nonfatal events go to the v4 backend
- No behavioral analytics, no tracking, no ads

### Third-Party Services (disclosed in privacy policy)

- **Google Cloud** — Cloud Speech-to-Text, Vertex AI Gemini, Google Search grounding, and Cloud Text-to-Speech process questions through the authenticated v4 backend
- **Firebase** — Auth, Firestore, Storage, and App Check
- **Apple** — App Transaction identity, In-App Purchases, iCloud Key-Value Store, iCloud Keychain, and native diagnostics
- **Formspree** — optional website support form delivery

## Conventions

- All pages are self-contained HTML files using Tailwind CSS CDN with minimal inline CSS (no external stylesheets or scripts beyond Tailwind and Google Fonts)
- Responsive design with mobile-first approach
- Dark/light mode support via Tailwind `dark:` classes (toggled by class, persisted in localStorage)
- Sage green accent color matching the app (`#6B8E7E` primary)
- Scroll-triggered fade-in animations via IntersectionObserver
- Contact form uses Formspree (`https://formspree.io/f/...`)
- FAQ uses native `<details>/<summary>` elements (no JS needed)

## Deployment

Push to `main` branch. GitHub Pages auto-deploys. No build step required.

```bash
git add -A && git commit -m "message" && git push
```

Changes appear at `https://knowitowl.sandybrook.io` within minutes.

## Known Issues

- **No build step** — All pages use Tailwind CSS CDN with shared config inline in each file. Changes to shared styles (nav, footer, colors, Tailwind config) must be manually replicated across all three files.
- **Formspree contact form** — Requires a Formspree account. The form action URL is hardcoded in `support.html`.
- **Sitemap `lastmod` dates** — Must be manually updated in `sitemap.xml` when pages are modified.

## Changelog

- **2026-03-18:** Updated `privacy.html` section 4 (Google Gemini / AI Processing) to explicitly enumerate data types sent to Google's servers (voice audio recordings, text messages, conversation history up to 10 messages), reference Google Cloud Data Processing Addendum for equivalent protection, and note that the app obtains explicit in-app consent before sending data — addressing App Store rejection Guidelines 5.1.1(i) & 5.1.2(i).
- **2026-09-04:** Updated release metadata for automatic App Transaction identity, the authenticated v4 backend, current credit packs, personal-data deletion with retained commerce records, Apple-native diagnostics, and the current Google Cloud processing path.
