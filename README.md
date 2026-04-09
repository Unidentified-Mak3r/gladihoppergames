# Gladihopper Games

This repository is a **static browser-game site** (an arcade-style game portal), not a typical app with a backend build system.

At a high level:
- `index.html` is the main landing/play page for **Gladihoppers**.
- Other root HTML files (for example `slope.html`, `cookie-clicker.html`, etc.) are individual game pages.
- `detail.html` is a reusable template page with placeholders (`gameName`, `gameLink`) that appears intended for cloning into new game pages.
- `file/` contains embedded game builds/assets (Unity WebGL builds, Construct exports, game media, etc.).
- `assets/` contains shared CSS, JavaScript, and images for layout/UI behavior.

## What kind of project this is

It is essentially a **static game-hosting website**:
- Front-end stack: plain HTML/CSS/JavaScript (jQuery + Bulma + plugins).
- Content model: one page per game, often embedding a game via `<iframe>`.
- Deployment target: works well with static hosting (for example GitHub Pages).

## Repo structure

- `index.html` — main page and featured game embed.
- `*.html` at repo root — individual game entry pages.
- `detail.html` — template for new game detail pages.
- `assets/css/` — stylesheets.
- `assets/js/` — shared UI/search/interaction scripts.
- `assets/images/` — site UI imagery/icons.
- `file/<game-name>/` — self-contained game distributions and assets.

## Run locally

Because this is static content, you can run it with any local web server.

### Option A: Python

```bash
python3 -m http.server 8080
```

Then open: `http://localhost:8080`

### Option B: VS Code Live Server

Open the repo and run “Open with Live Server” on `index.html`.

## How pages are wired

Typical game page pattern:
1. Page includes shared CSS/JS from `assets/`.
2. `<iframe>` points to a game URL (commonly under `file/<game>/...` or another hosted URL).
3. “More Games” cards link to other root pages.

## How to add a new game page (simple workflow)

1. Copy `detail.html` to a new file, e.g. `my-new-game.html`.
2. Replace placeholder values:
   - `gameName` → display title
   - `gameLink` → iframe source URL/path
3. Add/update thumbnail card links in `index.html` and any other listing pages.
4. If hosting game files in-repo, place them under `file/my-new-game/` and point iframe there.

## Notes and caveats

- Some scripts reference legacy endpoints like `/includes/*.php`; on purely static hosting these dynamic features (votes/comments/load-more via AJAX) won’t function unless you add a backend.
- Analytics/ads snippets are present in HTML and may need your own IDs/policies for production use.

---

If you want, I can also create a **cleaned-up “getting started for maintainers”** section next (naming conventions, page template checklist, and a safer way to manage the game catalog).
