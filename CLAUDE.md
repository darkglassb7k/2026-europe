# 2026 Europe Itinerary

A single-page static site for pyw's 2026-09-15 to 2026-09-30 Netherlands · Belgium · Italy trip. Deployed on Vercel, auto-deploys on push to `main`.

## Files

- `index.html` — content
- `style.css` — Scandinavian / Nordic minimalist style
- `todo.csv` — outstanding booking tasks (short, not a master data source)
- Lucide icons via CDN (version pinned)
- No build step, no framework

## Planning source of truth

Master trip planning lives in the user's wife's Google Sheets (not in this repo). This site is a public-facing showcase; the wife's sheet is the working plan. When the user shares updates (screenshots, pasted text), diff against the wife's sheet convention and update `index.html` accordingly. Do NOT reintroduce a master `itinerary.csv` — that workflow was retired.

## How to update the itinerary

User sends new/updated trip details. You diff against `index.html` and apply edits in place. Then commit + push — Vercel handles the deploy.

```bash
git add index.html style.css
git commit -m "..."
git push
```

## Content conventions

- **Language:** English, casual travel-influencer tone (not literal translation, not stiff).
- **Day card structure:**
  - `<article class="day-card">` (米白 default, add `forest` class for moving / pivotal days)
  - Date marker (number + Sep · Day)
  - `stay-bubble` for accommodation (top-right on desktop, bottom of card on mobile)
  - `day-body` with `<h3>` title, `<span class="day-tag">` subtitle, `<ul>` of list items
  - Optional `<div class="note">` for callouts (game plan / heads up)
- **List item labels (`<span class="label">`):**
  - Transit (all transport: flights, trains, buses, cars)
  - Visit (all sights)
  - AM / PM (time-of-day slot) or specific time (08:15, 15:30)
  - Bags / Booking / Sunset (special one-offs only)
- **Icons:** Lucide via `<i data-lucide="..."></i>`. Common: `plane`, `train-front`, `bus`, `car`, `map-pin`, `church`, `image`, `dumbbell`, `wine`, `trees`, `swords`, `landmark`, `bed`, `triangle`.
- **Chapter dividers:** unified star ✦ for all four chapters and footer.
- **Forest-green cards** are reserved for moving days / big pivotal days. Default米白 for normal sightseeing days.

## Style tokens (in `:root`)

- Parchment / cream backgrounds
- Forest green (`--sc-forest`) for accent
- Wood / cream-soft (`--sc-wood-soft`) for secondary
- Deep blue (`--sc-deep`) and accent red (`--sc-accent`) available but currently unused on cards

## Don'ts

- No em / en dashes in prose (titles OK). Substitute with `·`, comma, period, or parens.
- No Chinese in user-facing text (the site is fully English now).
- Don't add a legend / symbols block — it was removed deliberately.
- Don't add country chips back to hero — also removed deliberately.
