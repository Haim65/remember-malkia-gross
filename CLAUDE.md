# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status

Pre-development. The repository currently contains **no application code, build tooling, or tests** — only design references in `Refeence/` and project scaffolding (git, `.gitignore`). There is no stack chosen yet, so there are no build/lint/test commands to document. Update this file with real commands and architecture once code exists.

## Deliverable & decisions

- **Deliverable:** a single self-contained `index.html` (HTML + CSS + JS inline), Hebrew RTL, responsive, accessible contrast. Serves as a hub for Malkia's memorial projects.
- **Tone:** dignified, warm, restrained. All Hebrew prose humanized per `anti-ai.md` (no em dashes, no AI clichés, varied sentence length, specific).
- **Deploy target:** GitHub Pages (git already initialized; needs a GitHub account + push).
- **Remembrance content:** user provides a base; Claude supplements from public sources. Every bio/story draft must be approved by the user before it goes into the page (memorial for a real person — do not invent facts).
- **Backoffice (DEFERRED):** v1 ships the remembrance section with **placeholders** for bio/stories/photos, structured so content can be slotted in later. No CMS/admin/database in v1. A real backoffice (options considered: Supabase DB+admin, static local editor, or Decap CMS) is a later version once the family decides how they want to edit. Keep the remembrance markup data-driven/clearly delimited so a backoffice can plug in without a rewrite.
- **QR:** generated inside the file from the donation URL so the file stays self-contained and the QR always matches the link. Must actually scan to the donation page.

### Required page sections (all six must be present)
1. Hero — in memory of רס"ל מלכיה גרוס הי"ד.
2. **Remembrance area** (added requirement) — photos, biography, stories.
3. Donation link + working QR code beside it.
4. Project 1 — WhatsApp shidduch groups, organized by age group.
5. Project 2 — link to existing "מלקיטוב" site.
6. Project 3 — Instagram: https://www.instagram.com/remember_malkia_gross?igsh=MWRoeTFvczQxeWhrdQ==
7. Two contacts (POC) — each with phone + email, for direct donations.

### Inputs (received 2026-06-21)
- **Design references:** files in `Refeence/` (infographic, photos, campaign PDF) — that's the full reference set.
- **Donation page (also the QR target):** https://links.payboxapp.com/lfuS4UIPR0b
- **WhatsApp shidduch groups** (`Refeence/Shiduch groups Whatsapp`), by age: 18-25 (×3), 25-30 (×4), 30-35 (×3), 35-40 (×2), 40-60 (×2), 60+ (×1).
- **Malkitov (מלכי-טוב):** https://share.google/Bl4gZRizckTWUYvxu (resolve to canonical URL during build).
- **Instagram:** https://www.instagram.com/remember_malkia_gross?igsh=MWRoeTFvczQxeWhrdQ==
- **Contacts (POC):** אורי וולף — Oriwolf0@gmail.com, 058-400-0492 · אלידע הכהן דויטש — elyada10@gmail.com, 058-760-5879
- **Remembrance bio/stories:** placeholders for v1 (see Backoffice note).

## Live site

- **URL:** https://haim65.github.io/remember-malkia-gross/
- **Repo:** https://github.com/Haim65/remember-malkia-gross (public, owner `Haim65`)
- **Hosting:** GitHub Pages, source = `main` branch, `/` root. Deploys automatically on push to `main`.

## Progress log

Kept current after each step so a future session can pick up where we left off. Newest first.

- **2026-06-21** — Added a site QR + favicon. `assets/qr-site.png` = QR to the live site URL with `logo.png` (Malkia cutout) embedded in a white rounded badge in the center; generated with `segno` (error level H) + Pillow composite. **Verified scannable**: decoded the final image with OpenCV → returns the exact site URL. Favicon `assets/favicon.png` (+ `apple-touch-icon.png`) built from `logo.png` as a circular cream/gold medallion; wired into `<head>`. `logo.png` lives at repo root (source). QR is for print/stickers; not embedded in the page (the on-page QR remains the PayBox donation one).
- **2026-06-21** — Replaced the single hero portrait with two authentic photos of Malkia, side by side (circular, gold-framed). Sources added by user to `Refeence/` (the 2026-06-21 images); cropped with Pillow to `assets/img/hero-smile.jpeg` (event/smiling) and `assets/img/hero-desert.jpeg` (army/desert, bucket hat). Full-size copies kept as `assets/img/photo-smile.jpeg` / `photo-desert.jpeg`. Old `hero-face.jpeg` removed. Verified desktop + mobile (two circles fit side by side, 150px desktop / 128px mobile). Pushed → auto-redeploys.
- **2026-06-21** — Deployed to GitHub Pages. Created public repo `Haim65/remember-malkia-gross`, pushed `main`, enabled Pages (main/root). Verified live at https://haim65.github.io/remember-malkia-gross/ (HTTP 200, build `built`) and confirmed the deployed page renders correctly over HTTPS (fonts, images, QR). To update the site in future: commit to `main` and push — Pages rebuilds automatically.
- **2026-06-21** — Built `index.html` (the full site) and verified it. Approved design direction "אור מאופק" (navy + gold + cream; Frank Ruhl Libre headings + Heebo body). All 6 sections present + remembrance area with placeholders. QR baked in as inline SVG (generated with `segno` from the PayBox URL; scannable, offline-safe). Hero portrait cropped from `poster.jpeg` via Pillow → `assets/img/hero-face.jpeg`. WhatsApp groups are data-driven (JS array in the page) for easy updates. Verified rendering at desktop (900px) and mobile (390px) with headless Chrome — layout, QR, and chips look correct. Malkitov link resolved to https://malkitov.com/. Next: deploy to GitHub Pages.
  - **Assets used by the page:** `assets/img/hero-face.jpeg` (hero), `assets/img/badge.jpeg` + `assets/img/poster.jpeg` (gallery), inline QR. `assets/qr-donation.svg` kept as the QR source artifact.
  - **Build helpers:** Python `segno` (QR) and `pillow` (crop) are installed in the local Python 3.11; not part of the deployed site.
- **2026-06-21** — Planning phase. Defined deliverable, sections, tone, and the ask_me_first input list. Decisions confirmed with user: deploy = GitHub Pages; remembrance content = user-provided base + Claude supplement (drafts approved before use).
- **2026-06-21** — Initialized git repository (`main` branch). Added `.gitignore` (Node/Next/Vite-oriented). Created this CLAUDE.md (intent-only).

## Project

A Hebrew-language memorial website: **"ממשיכים את האור של מלכיה" / "משמחים עם מלכיה"** — in memory of **רס"ל מלכיה גרוס הי"ד**, a soldier fallen in the *חרבות ברזל* (Iron Swords) war.

The site is part memorial, part active charitable initiative. Its centerpiece is a **גמ"ח** (free-loan fund) lending musical instruments and cleaning equipment, reflecting Malkia's love of music and *chesed*. Donations are collected via **PayBox** (`https://links.payboxapp.com/...`).

### Intended content (from the mockups)

- Five themed sections: **המורשת** (heritage/story), **האור של מלכיה** (his light), **התנדבויות** (volunteering), **מפגשי זיכרון** (memory gatherings), **פרויקט המידות** (the *midot* project).
- Navigation: אודות · פרויקטים · צור קשר · תרומה (About · Projects · Contact · Donate).
- Impact stats: 6 projects · 230 volunteers · 12 locations.
- A QR-code badge/sticker linking to the donation/initiative.

## Hard requirements

- **RTL, Hebrew-first.** All layout, text alignment, and typography must default to right-to-left. This is the primary UI constraint — verify it in any component work.
- **Reference assets** live in `Refeence/` (note: spelled without the second "r"): an infographic of the section layout, hero/portrait photos, the circular QR badge, and a PDF of the WhatsApp campaign copy. Use these for content, branding, and the color palette (teal, rust, navy, slate, olive on a cream background).
