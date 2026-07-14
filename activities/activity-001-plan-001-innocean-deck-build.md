# Activity 001 — INNOCEAN deck build (Plan 001)

**Date:** 2026-07-14
**Plan:** ./plans/plan-001-innocean-deck.md

## What was completed

Built the first version of the INNOCEAN deck as a self-contained subdirectory at
`/innocean/`, adapted from the New Balance deck and populated from the Milk & Honey Silo PDF.

### Scaffold + rebrand (Baxter House only, no Radish)
- Cover: "A music & creative screening for / INNOCEAN / Presented by Baxter House".
- Removed: The Partnership, Who Is Radish?, Radish placements, Featuring Max Levin,
  New Balance logo watermark.
- Rebranded nav title → "Baxter House", eyebrow → "FOR INNOCEAN", `<title>`, closing copy.
- Kept: Who Is Baxter House?, Chart-Topping Hits, Music Customization & Arrangements,
  The House, Closing.

### New content from the PDF (extraction = Option 1, real text + individual hi-res assets)
- Extracted ~40 individual image assets at native resolution, converted PNG→JPEG
  (26MB → ~6MB). Stored under `/innocean/assets/case-studies/<brand>/`,
  `/innocean/assets/remixes/`, `/innocean/assets/brands/`.
- **How We Work** — 4 pillars (Customs, Artist/Brand Partnerships, Creative Licensing,
  Remixes), M&H copy verbatim, laid out as a 2×2 quad.
- **Case Studies** (own section, each a unique nav link): New Balance, Chick-fil-A,
  Virgin Voyages, Novartis, Smirnoff, Optimum Online. Reusable template = ASK + What We
  Delivered + click-to-modal gallery. Virgin / Smirnoff / Optimum fully built with PDF
  assets + ASK; New Balance / Chick-fil-A / Novartis stubbed (ASK "to be added", pending
  asset tiles).
- **Remixes** — dedicated slide, 6 remixes incl. Accenture × James Blake "Thrown Around".
- **Brands We Love & Who Love Us** — logo wall cropped from PDF pg 10, all M&H text removed;
  own HTML heading added.

### Verification
- All local asset paths resolve; data-item indices consistent with ITEMS array.
- Visually verified via headless browser at 1440×900: cover, How We Work quad, Virgin,
  Optimum, New Balance stub, Remixes, Brands wall — all render correctly.

## Open items (awaiting client)
- Real ASK + copy + image assets for New Balance, Chick-fil-A, Novartis.
- Confirm Accenture × James Blake ASK (draft used) — now lives only in Remixes.
- Confirm "Brands We Love" list is accurate for Baxter (currently the M&H wall image).
- Baxter-specific rewrite of "How We Work" copy (M&H copy is placeholder).
- Case-study order is easily adjustable.

## Revision 2 (client feedback: grouping + inline display)
- Re-verified per-case-study asset grouping (per-page PDF extraction guarantees no cross-brand
  mixing). Completed the **Smirnoff** set — it was under-extracted; added Isaac Zale portrait,
  See You (Isaac), Day One (Leila), and two social process screenshots. Smirnoff now 13 assets;
  Virgin 8; Optimum 9 — all correct and complete.
- Changed case-study galleries from click-to-modal cropped tiles to **inline masonry**
  (`.cs-media`, CSS columns): images shown in place, full/uncropped, **not clickable, not
  fullscreen**, each with a small caption. Modal/lightbox removed for case studies only
  (track record, remixes, brands still use it).

## Revision 3 (client feedback: hero-first case study layout)
- Each populated case study now opens with a **full-viewport hero image** (the PDF's full-bleed
  slide), bled to the content-area edges, above the nav-safe content. Below the hero: the case
  study **name + The Ask + What We Delivered** (text), then the **image grid**.
- Hero images (removed from their grids to avoid duplication):
  - Virgin → Karma Chameleon (The Voyage Edition) art
  - Smirnoff → "We Do We" key art
  - Optimum → "optimum." wordmark on navy (only full-bleed slide on pg8; flagged as minimal —
    offered Away We Go cover / music-video still as richer alternatives, awaiting client call)
- Rule applied: when >1 hero candidate, use the one appearing first in the PDF.

## Files
- `/innocean/index.html` — the deck
- `/innocean/assets/**` — self-contained assets (splittable to its own Vercel project later)
