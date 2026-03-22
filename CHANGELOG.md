# Changelog

All notable changes to Nomi Archive will be documented here.

This project follows [Semantic Versioning](https://semver.org/):
- **MAJOR** version — breaking changes (e.g. CSV format change)
- **MINOR** version — new features, backwards compatible
- **PATCH** version — bug fixes, small improvements

---

## [v1.4.1] — 2026-03-22

### Improvements
- `gallery.html`, `gallery-toolkit.html`, `gallery-local.html` — gallery card redesign
  - Removed prompt text and filename from below each card — grid is now a clean image mosaic
  - Prompt appears as a gradient overlay at the bottom of the image on hover (desktop), fading in smoothly with the filename and a compact Copy button
  - Cards are fully square with no wasted whitespace
  - Mobile behaviour unchanged — tapping opens the bottom sheet with full prompt details

- Sort order simplified
  - Renamed "Newest first / Oldest first" to **Last added / First added** to accurately reflect CSV order rather than implying date metadata
  - Removed Nomi A→Z / Z→A sort options — the Nomi filter tabs already serve this purpose

- Related images fix
  - Related strip now appears **inside the lightbox** (desktop) and **inside the bottom sheet** (mobile) as a horizontal scroll row, rather than below the gallery where it was hidden behind the lightbox overlay

---

## [v1.4.0] — 2026-03-22

### New features
- `gallery.html` and `gallery-local.html` — major gallery improvements

  **Sort order**
  - Dropdown in the toolbar: Newest first, Oldest first, Nomi A→Z, Nomi Z→A
  - Sort preference persisted in `localStorage` between sessions

  **Infinite scroll**
  - Gallery loads 15 images at a time, auto-loading the next batch as you scroll toward the bottom
  - Small spinner shown while loading each batch
  - Replaces loading the full image set at once — significantly improves performance on large archives

  **Favourites**
  - Heart button on every card (visible on hover, always visible when active)
  - Also available in the desktop lightbox and mobile bottom sheet
  - Press `F` on desktop to toggle favourite on the currently open image
  - Favourites filter button in the toolbar — click to show only favourited images
  - `gallery.html` (remote mode): writes `favourite` as a new 6th CSV column via the Worker, syncing across devices
  - `gallery-local.html`: stored in `localStorage` per device

  **Related images**
  - When an image is open (lightbox or bottom sheet), a strip appears at the bottom of the gallery showing up to 6 images with shared prompt keywords
  - Click any related image to jump to it
  - Strip hides automatically when the lightbox or sheet is closed

  **Pinch to zoom**
  - Desktop lightbox: scroll wheel to zoom in/out, double-click to reset
  - Mobile lightbox: two-finger pinch to zoom
  - Zoom resets automatically when navigating to the next image

  **Transition animations**
  - Cards fade in with a stagger effect on initial load and when new batches load
  - Gallery grid fades out and back in smoothly when switching Nomi, style, or sort order

### CSV format update
A new optional `favourite` column (6th) has been added. Fully backwards compatible — old CSVs without this column continue to work.

```
filename, nomi_name, prompt, nsfw, style, favourite
aurora_001.png, Aurora, "your prompt here", false, Realistic, true
```

---

## [v1.3.1] — 2026-03-22

### Improvements
- `gallery.html` and `gallery-local.html` — **mobile bottom sheet**
  - Tapping an image on mobile (≤600px) opens a bottom sheet instead of the desktop lightbox
  - Sheet slides up from the bottom with the full image, prev/next navigation, full prompt (scrollable, no truncation), Nomi name, style badge, NSFW badge, filename, and a full-width Copy prompt button
  - Dismiss by tapping the backdrop or swiping down
  - Desktop lightbox behaviour unchanged
  - Bottom sheet only rendered on mobile — hidden entirely on desktop via CSS

---

## [v1.3.0] — 2026-03-22

### New features
- `gallery.html` and `gallery-local.html` — **style filter**
  - Filter row with `Realistic`, `Anime`, and `Mix` tabs appears below the Nomi tabs — only shown when at least one entry in the CSV has a style value; hidden entirely for old CSVs with no style data
  - Style filter stacks with the Nomi filter and search, so all three can be combined simultaneously
  - Active style persisted in `localStorage` between sessions; also reflected in URL params in `gallery.html` (e.g. `?style=Anime`) so filtered views can be bookmarked or shared
  - Style badge displayed on each card thumbnail (bottom-right corner) when a style is set
  - Style shown alongside Nomi name in the lightbox (e.g. `Aurora · Anime`)
  - CSV parser updated in both gallery files to read the `style` column; fully backwards compatible with old 4-column CSVs

---

## [v1.2.0] — 2026-03-22

### New features
- `logger.html` — **inline editing** on existing entries
  - **Edit prompt** — click Edit on any entry card to reveal an inline textarea pre-filled with the existing prompt; save or cancel without leaving the page
  - **Edit style** — the inline edit area also exposes the Style dropdown, so style can be set or changed on any existing entry
  - Both prompt and style are saved together in a single Save action; empty prompts are blocked
  - Importing an old 4-column `prompts.csv` (without `style`) works without any manual changes — entries default to blank style and can be updated via inline edit

---

## [v1.1.0] — 2026-03-22

### New features
- `logger.html` — added **Style** field to the log form
  - Dropdown options: `Realistic`, `Anime`, `Mix` (optional — leave blank if not set)
  - Style tag displayed as a badge on each entry card in the log list
  - Style value stored and reset correctly after each log entry
  - Export includes style as a new 5th CSV column (`style`)
  - Import parser handles both old 4-column CSVs and new 5-column CSVs — fully backwards compatible

- `README.md` — added **Companion tools** section documenting [Nomi Downloader](https://chromewebstore.google.com/detail/nomi-downloader/dglkpknkpjcfdbbmgidognlnanlocfem) browser extension, including recommended bulk-download workflow and note on Create Art prompt limitation

### CSV Format
```
filename, nomi_name, prompt, nsfw, style
aurora_001.png, Aurora, "your prompt here", false, Realistic
```

---

## [v1.0.0] — 2025-03-16

Initial public release.

### Features
- `logger.html` — log Nomi images and prompts locally in the browser
  - Add and delete Nomis from the sidebar
  - Auto-generates clean filenames (e.g. `aurora_001.png`)
  - Rename hint with one-click copy when filename needs updating
  - NSFW toggle per entry (stored in CSV as 4th column)
  - Toggle NSFW flag on existing entries
  - Import existing `prompts.csv` without duplicating entries
  - Export `prompts.csv` for use with gallery
  - All data persists in browser `localStorage` between sessions

- `gallery.html` — web-server / GitHub Pages version
  - Auto-loads `prompts.csv` and `images/` folder via HTTP fetch
  - Filter by Nomi with count badges
  - Full-text prompt search
  - Lightbox with full-size image view
  - Slideshow mode with progress bar (5-second interval)
  - NSFW blur cover with click-to-reveal on thumbnails
  - Copy prompt to clipboard from gallery and lightbox
  - Keyboard navigation (← → Esc Space)
  - Persistent filter and search state via `localStorage` and URL params
  - Dark mode (follows system preference)
  - Mobile-responsive grid layout

- `gallery-local.html` — local desktop version
  - All gallery features above
  - File picker to load images and CSV manually each session
  - Remembers last active Nomi filter and search between sessions

### CSV Format
```
filename, nomi_name, prompt, nsfw
aurora_001.png, Aurora, "your prompt here", false
```

---

## Versioning Guide (for contributors and maintainers)

When making changes, update this file and bump the version in `README.md`:

| Change type | Example | Version bump |
|---|---|---|
| New feature | Add image tagging | `v1.1.0` |
| Bug fix | Fix CSV parser edge case | `v1.0.1` |
| Breaking change | New CSV column required | `v2.0.0` |
| Small improvement | Better mobile layout | `v1.0.1` |
