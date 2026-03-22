# Nomi Archive

**A free, open-source toolkit for [Nomi.ai](https://nomi.ai) users to log, organise, and browse their AI-generated images alongside the prompts that created them.**

No installation. No accounts. No cloud. Everything runs locally in your browser.

> Built by [@jovialk69](https://github.com/jovialk69) · Licensed under [GPL v3](LICENSE) · Contributions welcome

---

## Live demo

**[→ Try the gallery demo here](https://jovialk69.github.io/nomi-archive-toolkit/gallery.html)**

See the gallery in action with sample images and prompts — lightbox, NSFW covers, search, slideshow and all. No sign-in required.

---

## Why this exists

Nomi.ai doesn't currently provide a way to export your generated images or retrieve the prompts that created them via its API. This toolkit fills that gap — giving you a fast, private, offline-first way to archive your Nomi images and the prompts behind them, so you can recreate them anytime even if you delete a Nomi.

For bulk-downloading images and chat histories directly from Nomi.ai, see [Companion tools](#companion-tools) below.

---

## What's included

| File | Purpose | Runs |
|---|---|---|
| `logger.html` | Log images and prompts as you create them | Locally in any browser |
| `gallery-local.html` | Browse your archive on your desktop | Locally in any browser |
| `gallery.html` | Browse your archive as a live website | GitHub Pages or any web server |
| `prompts.csv` | Your master list of images and prompts | — |
| `images/` | Folder where your downloaded images live | — |

---

## Quick start (local, no GitHub needed)

**You only need three files: `logger.html`, `gallery-local.html`, and `prompts.csv`.**

### Step 1 — Set up your folder

```
Nomi Archive/
├── images/              ← put your downloaded Nomi images here
├── logger.html          ← open this to log new entries
├── gallery-local.html   ← open this to browse your archive
└── prompts.csv          ← exported from the logger
```

### Step 2 — Add your Nomis

1. Open `logger.html` in Safari or Chrome
2. In the left sidebar under **Add Nomi**, type each Nomi's name and press `+`

### Step 3 — Get your images

**Option A — one at a time (no extra tools needed)**

Download images from Nomi.ai as you go and drop them into your `images/` folder.

**Option B — bulk download with Nomi Downloader (recommended)**

If you have a backlog of images to archive, [Nomi Downloader](https://chromewebstore.google.com/detail/nomi-downloader/dglkpknkpjcfdbbmgidognlnanlocfem) lets you download an entire album as a zip file in one click. Extract the zip into your `images/` folder, then use `logger.html` to log each image and its prompt. The logger will show a rename hint for any files with messy Nomi.ai filenames.

See [Companion tools](#companion-tools) for more details.

### Step 4 — Log an image

For each image in your `images/` folder:

1. Select the **Nomi name** from the dropdown
2. Click the image picker and select the image
3. If the filename is messy (e.g. `Aurora Selfie (3).png`), a **rename hint** appears — hit **Copy name**, then rename it in Finder (select file → `Return` → paste → `Return`)
4. Paste the **image prompt** from Nomi.ai
5. Optionally select a **Style** — `Realistic`, `Anime`, or `Mix`
6. Optionally toggle **Mark as NSFW** — this blurs the thumbnail in the gallery until clicked
7. Click **Log entry →**

### Step 5 — Export and browse

1. In `logger.html`, click **↓ Export prompts.csv** → save it into your `Nomi Archive/` folder
2. Open `gallery-local.html` → select all images (Cmd+A) + select `prompts.csv` → click **Load gallery**

---

## Logger features

- **Style tagging** — tag each image as `Realistic`, `Anime`, or `Mix` when logging
- **Inline editing** — edit any existing prompt directly in the log list; update style at the same time
- **NSFW toggle** — mark and unmark entries as NSFW from the log list
- **Copy prompt** — one click to copy any logged prompt to clipboard
- **Rename hint** — auto-generates the correct filename and shows a copy button when the original is messy
- **Import existing CSV** — loads a previous `prompts.csv` without duplicating entries; handles old 4-column files automatically
- **Export CSV** — produces `prompts.csv` with all columns including `style` and `nsfw`
- **Persistent storage** — all data saved in browser `localStorage` between sessions

---

## Gallery features

- **Filter by Nomi** — pill tabs with image counts
- **Filter by style** — Realistic / Anime / Mix filter row, only shown when style data exists in the CSV
- **Filter by favourites** — toolbar button to show only favourited images
- **Sort order** — Newest first, Oldest first, Nomi A→Z, Nomi Z→A
- **Search prompts** — full-text search across all prompts
- **Infinite scroll** — loads 15 images at a time, auto-loads as you scroll
- **Favourites** — heart button on cards, lightbox, and bottom sheet; press `F` on desktop; syncs via CSV in remote mode
- **Related images** — strip of up to 6 keyword-matched images shown when viewing any image
- **Lightbox** — click any image for full-size view with scroll-to-zoom and double-click to reset
- **Pinch to zoom** — two-finger pinch in the lightbox on mobile
- **Slideshow** — auto-advances every 5 seconds with progress bar
- **NSFW covers** — blurred thumbnails with click-to-reveal; always shown unblurred in lightbox
- **Copy prompt** — one click from gallery or lightbox
- **Keyboard navigation** — `←` `→` to navigate, `Esc` to close, `Space` slideshow, `F` favourite
- **Dark mode** — follows your system setting automatically
- **Mobile bottom sheet** — tapping an image on mobile slides up a sheet with full prompt and controls
- **Mobile layout** — responsive 2-column grid on phones

---

## Companion tools

### Nomi Downloader

[**→ Nomi Downloader on Chrome Web Store**](https://chromewebstore.google.com/detail/nomi-downloader/dglkpknkpjcfdbbmgidognlnanlocfem)

Also available for [Firefox](https://addons.mozilla.org/en-US/firefox/addon/nomi-downloader/).

Nomi Downloader is a browser extension that fills the acquisition gap this toolkit doesn't cover — getting your images and chat history off Nomi.ai quickly. It lets you download an entire album as a zip file and export full chat histories, all in a few clicks.

**How it works alongside this toolkit:**

| Nomi Downloader | Nomi Archive Toolkit |
|---|---|
| Bulk-downloads images from Nomi.ai | Organises, renames, and catalogues those images |
| Exports raw chat history | Stores and browses image prompts specifically |
| Gets your media off the platform fast | Displays, searches, and slideshows your archive |

> **Important:** When exporting chat history, Nomi Downloader can surface prompts for selfies generated **within the chat** — but it does **not** capture prompts from Nomi.ai's **Create Art** feature. If you use Create Art, you'll need to copy those prompts manually into `logger.html` as usual.

**Recommended workflow for a backlog of images:**

1. Use Nomi Downloader to download your full album as a zip
2. Extract the zip into your `Nomi Archive/images/` folder
3. Open `logger.html` and log each image — the rename hint will guide you to clean up filenames
4. Export `prompts.csv` and browse with `gallery-local.html`

**A note on trust:** Nomi Downloader is a third-party extension not affiliated with this project. It has a small user base, so exercise normal caution when installing any browser extension. The developer has disclosed that no user data is collected or sold.

---

## CSV format

The `prompts.csv` file uses four columns:

```
filename, nomi_name, prompt, nsfw, style, favourite
aurora_001.png, Aurora, "silver hair, cinematic portrait, soft morning light", false, Realistic, false
aurora_002.png, Aurora, "dark forest, bioluminescent glow, fantasy art", true, Anime, true
```

| Column | Required | Notes |
|---|---|---|
| `filename` | Yes | Must match the file in `images/` exactly, including extension |
| `nomi_name` | Yes | Drives the filter tabs in the gallery |
| `prompt` | Yes | Wrap in quotes if the prompt contains commas |
| `nsfw` | No | `true` or `false` — defaults to `false` if omitted |
| `style` | No | `Realistic`, `Anime`, or `Mix` — leave blank if not set |
| `favourite` | No | `true` or `false` — defaults to `false` if omitted |

You can edit this file in Numbers, Excel, or any text editor. Always save as `.csv`.

---

## Hosting on GitHub Pages (optional)

Hosting on GitHub Pages unlocks `gallery.html` — it auto-loads `prompts.csv` and all images automatically with no file picking required.

### One-time setup

**Step 1 — Create a GitHub repository**

1. Go to [github.com](https://github.com) → click **+** → **New repository**
2. Name it `nomi-archive-toolkit` → set to **Public** → click **Create repository**

**Step 2 — Generate a Personal Access Token**

GitHub requires a token instead of your password for Git operations.

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token** → **Generate new token (classic)**
3. Name it `nomi-archive-toolkit-mac`, set expiration to **No expiration**, tick **repo**
4. Click **Generate token** — copy it immediately (shown only once)

**Step 3 — Push your files**

Open Terminal and run (replace `YOUR_USERNAME` with your GitHub username):

```bash
git config --global credential.helper osxkeychain
cd ~/Desktop
git clone https://github.com/YOUR_USERNAME/nomi-archive-toolkit.git
cd nomi-archive-toolkit
```

Copy all toolkit files into this folder, then:

```bash
git add .
git commit -m "Initial release"
git push
```

When prompted, enter your GitHub username and paste your token as the password.

**Step 4 — Enable GitHub Pages**

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Under **Source** → select **Deploy from a branch** → **main** → **/ (root)** → **Save**
3. Wait 30–60 seconds — your gallery is live at `https://YOUR_USERNAME.github.io/nomi-archive-toolkit/`

### Updating with new images

```bash
# 1. Export fresh prompts.csv from logger.html into your nomi-archive-toolkit folder
# 2. Copy new images into the images/ folder
# 3. Then run:
cd ~/Desktop/nomi-archive-toolkit
git add .
git commit -m "Add new images"
git push
```

---

## Forking and contributing

Forks and contributions are welcome. This project is licensed under **GPL v3** — any forks or derivative works must also be open source under the same licence.

### To fork this project

1. Click **Fork** at the top-right of this GitHub page
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/nomi-archive-toolkit.git`
3. Make your changes
4. Submit a **Pull Request** if you'd like your changes merged back

### Ideas for contributions

- A Python companion script to auto-rename files
- Better mobile UX improvements
- Tag or rating system for images
- Multi-language support
- Bulk NSFW flagging

### Reporting bugs or requesting features

Open an [Issue](../../issues) on GitHub. Please include:
- What you expected to happen
- What actually happened
- Your browser and OS

---

## Compatibility

- Safari and Chrome on Mac ✓
- Chrome on Windows ✓
- Mobile browsers (iOS Safari, Chrome Android) ✓
- Works fully offline after first load (fonts load from Google Fonts on first use)
- No installation, no Node.js, no dependencies

---

## Nomi.ai API note

As of early 2026, the Nomi.ai API does not expose an endpoint for retrieving generated images or prompts. If this changes, the logger workflow could be further automated. You can request this feature from Nomi.ai at [support@nomi.ai](mailto:support@nomi.ai) or via their [Discord](https://discord.com/invite/nomiai).

---

## Version history

See [CHANGELOG.md](CHANGELOG.md) for full release notes.

Current version: **v1.4.0**

---

## Licence

This project is licensed under the [GNU General Public License v3.0](LICENSE).
Copyright © 2025 [@jovialk69](https://github.com/jovialk69)

You are free to use, modify, and distribute this software, provided that any derivative works are also licensed under GPL v3 and remain open source.
