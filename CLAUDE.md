# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status

Pre-development. The repository currently contains **no application code, build tooling, or tests** — only design references in `Refeence/` and project scaffolding (git, `.gitignore`). There is no stack chosen yet, so there are no build/lint/test commands to document. Update this file with real commands and architecture once code exists.

## Progress log

Kept current after each step so a future session can pick up where we left off. Newest first.

- **2026-06-21** — Initialized git repository (`main` branch). Added `.gitignore` (Node/Next/Vite-oriented). Created this CLAUDE.md (intent-only). No stack chosen yet; next step is to decide the tech stack and scaffold the site.

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
