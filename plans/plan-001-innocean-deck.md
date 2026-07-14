# Plan 001 — INNOCEAN Deck (Baxter House standard agency-partner presentation)

**Scope:** Local to this project (`jerusalem` workspace, symlinked as `innocean-slide-deck`).
**Destination:** `./plans/plan-001-innocean-deck.md`
**Date:** 2026-07-14

## Goal
Create a new slide deck for **INNOCEAN**, adapted from the existing New Balance deck
(`index.html` at repo root). Built as a self-contained **subdirectory** (`/innocean/`) so it
can later be split into its own Vercel project (eventual home: presentations.baxterhousemusic.com).
This becomes Baxter House's **standard "hello new agency partner" presentation** — Baxter House
only, no Radish anywhere.

## Source materials
- Existing deck: `/index.html` (New Balance × Radish). Reuse structure + design system.
- `Copy of Milk & Honey Silo Deck.pdf` (in `/Users/amitsavyon/ClaudeCode/Clients/Baxter/`).
  Confirmed: real vector text + ~80 individual hi-res image assets (Option 1 viable).
  Every "Milk & Honey Silo" mark must be removed (that was where the work was done; it's
  Baxter's work now).

## Decisions (confirmed by client)
1. **No Radish anywhere** — fully Baxter House–only chrome + copy.
2. **Case Studies = its own section**, each case study a **unique nav link / sub-section**.
3. "How We Work" pillars (M&H page 1): **hold/drop** for now (their copy, not ours).
4. "Brands We Love" logo wall (M&H page 10): **omit** until Baxter's real brand list provided.
5. Optimum Online (M&H pg 7-8): **not in core six**; extract + keep for a possible 7th.

## Cover copy
```
A music & creative screening for
INNOCEAN
Presented by Baxter House
```

## Removals from New Balance deck
- The Partnership (`#partnership`)
- Who Is Radish? (`#who-radish`)
- Radish → Music Supervision Placements (`#radish-music-to-picture`)
- Featuring: Max Levin (`#max-levin`)
- New Balance logo watermark background
- All Radish branding/copy (nav title, closing "two companies… music supervision")

## Keep (rebranded to Baxter-only)
- Who Is Baxter House?
- Baxter → Chart-Topping Hits
- Baxter → Music Customization & Arrangements
- The House
- Closing / Let's Build Something Together

## Case Studies (the six, each its own sub-nav link)
Reusable template per case study: brand title/logo · **ASK** · what we delivered (bullets) ·
asset gallery (click-to-modal, reusing existing track-card/modal pattern).

| Brand | ASK | Assets | Source |
|-------|-----|--------|--------|
| New Balance — We Got Now (2026) | TBD (client) | TBD (client) | bullets only |
| Chick-fil-A — Jalapeño Ranch | TBD (client) | TBD (client) | bullets only |
| Virgin Voyages | ✅ from PDF | ✅ from PDF | M&H pg 3–4 |
| Novartis — Super Bowl Spot | TBD (client) | TBD (client) | bullets only |
| Accenture × James Blake | partial | remix tile (pg 9) | bullets + PDF |
| Smirnoff — Sound of We | ✅ from PDF | ✅ from PDF | M&H pg 5–6 |

Optional later: Remixes grid (M&H pg 9), Optimum Online (7th case study).

## Build phases
1. **Scaffold** — copy New Balance deck into `/innocean/`, self-contained assets, rebrand,
   remove Radish/Partnership/Max, fix cover.
2. **Extract** M&H assets → `/innocean/assets/case-studies/<brand>/`, strip M&H marks.
3. **Case Studies section** — reusable template + sub-nav; populate Virgin, Smirnoff,
   Accenture live; stub New Balance, Chick-fil-A, Novartis for client ASK + assets.
4. **Verify** — visual check, nav/modal wiring, mobile.

## Open items awaiting client
- ASK copy + image assets for New Balance, Chick-fil-A, Novartis.
- Additional Accenture × James Blake assets (only the remix tile exists in PDF).
- Baxter's real brand list (if we want a "Brands We Love" wall).
- Decision on a Baxter version of "How We Work" pillars.

## Revision (client update, same day)
- Case Studies = PDF's three (Virgin Voyages, Smirnoff, **Optimum Online**) + New Balance,
  Novartis, Chick-fil-A. **No standalone Accenture case study.**
- **Accenture × James Blake** moves into a new dedicated **Remixes** slide (PDF pg 9 grid:
  2K24/Mötley Crüe, Gatorade/Vince Staples, Google/Maggie Rogers, Accenture/James Blake,
  Essentia/Yma Sumac, Honda/Panda Bear).
- **"Brands We Love & Who Love Us"** logo wall included (PDF pg 10, cropped free of M&H marks).
- **"How We Work"** included — M&H copy kept for now, rendered as a **2×2 quad**.
- NB/Novartis/Chick-fil-A: client asked to prefer PDF-style language over pasted bullets, but
  those three are not in the PDF — built from pasted bullets as the only source, flagged for
  real ASK + copy + assets.

## Activities
- /Users/amitsavyon/conductor/workspaces/Baxter/jerusalem/activities/activity-001-plan-001-innocean-deck-build.md
