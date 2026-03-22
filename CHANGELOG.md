# Changelog

All notable changes to Nomi Archive will be documented here.

This project follows [Semantic Versioning](https://semver.org/):
- **MAJOR** version — breaking changes (e.g. CSV format change)
- **MINOR** version — new features, backwards compatible
- **PATCH** version — bug fixes, small improvements

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
