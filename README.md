# Batch Masikhay 2026 — Graduation Seat Finder

An interactive, searchable seat map for the UP-PGH Post-Graduate Interns
(Batch Masikhay 2026) graduation at the Fleur-de-Lis Theater, St. Paul
University Manila. Type a graduate's surname to see their Center Block seat,
their two official guests' paired seats, and their place in the processional
order — all highlighted on a mirrored floor plan.

## What it does

- **Search by name** — accent-insensitive (`Cendana` matches `Cendaña`), with
  keyboard navigation (↑ ↓ Enter Esc).
- **Mirrored seating** — the processional enters through the right-center
  aisle, so seats fill from the far left. Assignments are the inverse of the
  original printed chart; physical seat numbers are unchanged.
- **Graduate + guest model** — each graduate has one Center Block seat; their
  Guests 1 & 2 sit as a labeled pair in the Left/Right block on the same side,
  overflowing to the back of the Center Block (rows M–Q) once the side rows
  fill.
- **Balcony reference** — Guests 3 & 4 sections shown for orientation.

## Stack

Zero build. One static file (`public/index.html`) — vanilla HTML, CSS, and JS,
with fonts from Google Fonts. Nothing to compile, no dependencies to install.

## Run locally

```bash
npx serve public
# or just open public/index.html in a browser
```

## Deploy to Vercel

**Option A — dashboard**
1. Push this repo to GitHub.
2. In Vercel, *Add New… → Project* and import the repo.
3. Framework preset: **Other**. Leave build & output settings empty
   (`vercel.json` already points the site at `public/`).
4. Deploy.

**Option B — CLI**
```bash
npm i -g vercel
vercel        # preview
vercel --prod # production
```

## Updating the roster or seating rule

Everything lives in the `<script>` block of `public/index.html`:

- **`ROSTER`** — the 156-name alphabetical list. Order here *is* the seating
  order, so keep it alphabetical (it matches the definitive PGI-2026 list).
- **Geometry constants** — `INTERN_ROWS`, `CENTER_COLS`, `LEFT_PAIRS`,
  `RIGHT_PAIRS`, and the overflow logic control how names map to seats. The
  16-per-row, two-side-rows-per-graduate-row rule is set here.

After editing, re-verify a few known anchors (e.g. Abesta-Tuban → C10,
Zulueta → L21) before distributing.

## Note

Seat assignments are generated from the roster order and the geometry rule, not
hand-placed. Spot-check against the final printed layout before the ceremony.
