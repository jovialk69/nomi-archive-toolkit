# Changelog

All notable changes to Nomi Archive will be documented here.

This project follows [Semantic Versioning](https://semver.org/):
- **MAJOR** version — breaking changes (e.g. CSV format change)
- **MINOR** version — new features, backwards compatible
- **PATCH** version — bug fixes, small improvements

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
