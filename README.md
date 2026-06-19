# Cull — RAW photo sorter

A single-file, offline photo culling tool for the browser. Open a folder of
photos and quickly flag picks/rejects, then move or delete the rejects — all
without uploading anything. Files never leave your disk.

- Pulls the full-size JPEG preview embedded in RAW files (CR2, CR3, NEF, ARW,
  RAF, DNG, ORF, RW2, …), plus regular JPEG/PNG/WebP/TIFF at full resolution.
- EXIF-aware orientation, a folder sidebar (one folder at a time), contact-sheet
  grid, and a Lightroom-style 1:1 zoom with a navigator minimap and sticky zoom.
- Runs entirely client-side. No build step, no dependencies.

## Requirements

Cull uses the [File System Access API](https://developer.mozilla.org/docs/Web/API/File_System_API),
so it needs a Chromium-based browser: **Chrome, Edge, Arc, or Brave**. Safari and
Firefox don't support folder read/write access and won't work.

## Run locally

It's just a static file — no server required. Either open `cull.html` directly,
or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000/
```

## Deploy on GitHub Pages

This repo is preconfigured to deploy via GitHub Actions (`.github/workflows/deploy.yml`).

1. Push this repo to GitHub.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Push to `main` (or run the workflow manually). The site publishes to
   `https://<user>.github.io/<repo>/`.

The root `index.html` redirects to `cull.html`, so the app loads at the root URL.

## Keyboard shortcuts

| Key | Action |
| --- | --- |
| `P` | Flag as pick |
| `X` | Flag as reject |
| `U` / `0` | Remove flag |
| `←` / `→` | Previous / next photo |
| `Z` / `Space` | Toggle 1:1 zoom |
| `G` | Toggle grid / single view |
| `Esc` | Stop zoom (clears the locked level) or exit grid |

Vertical scroll moves through the gallery; horizontal scroll zooms. Drag to pan,
and use the navigator box to jump around while zoomed.
