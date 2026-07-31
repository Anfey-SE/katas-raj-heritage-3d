# Katas Raj Temples — Site Survey Record

A digital preservation working file for the Katas Raj Temples (Chakwal, Punjab, Pakistan), built as part of the **TechRealm × PreserveMy.World (PMW) Platform & Web Engineering internship**, Team Indus.

**Live site:** https://katas-raj-heritage-3d.vercel.app

## What this is

A field-survey-styled record of one heritage site, presented as three exhibits a reviewer can switch between:

- **Exhibit A — Photograph.** The primary field capture of the site.
- **Exhibit B — AR Survey Lines.** A manually logged measurement overlay on the field photo, showing estimated structural spans between key points.
- **Exhibit C — Capture-to-3D.** A first-pass depth-relief mesh generated from photo luminance (brighter pixels are displaced forward), rendered in Three.js. This is **not** a full photogrammetry reconstruction — it's an early-stage visualization step toward one, and is labeled as such in the UI ("Depth Relief · First Pass").

Also included: a pretrained image classifier run against the field photographs (`ml_visualization_output.png`), and `RESEARCH.md`, a research log on 3D reconstruction methods considered for heritage sites.

## Controls (Exhibit C)

- Drag to orbit
- Right-click drag (or shift+drag) to pan
- Scroll to zoom

## Tech stack

- Vanilla HTML/CSS/JS
- Three.js r128 (CDN, no build step)
- Deployed via Vercel

## Files

| File | Purpose |
|---|---|
| `index.html` | Main survey record page, tabbed exhibit viewer |
| `capture_to_3d_depth.html` | Depth-relief 3D viewer (embedded via iframe in Exhibit C) |
| `capture_to_3d.html` | Earlier multi-image orbit prototype (superseded by the depth-relief version) |
| `ar_lines_overlay.html` | Standalone AR measurement overlay prototype |
| `RESEARCH.md` | Research log on 3D reconstruction methods for heritage sites |
| `katas_raj_*.png/jpeg` | Field photographs used across exhibits |
| `ml_visualization_output.png` | Output from the pretrained image classifier run |

## Run locally

No build step required — clone and open `index.html` in a browser, or serve the folder:

```bash
git clone https://github.com/Anfey-SE/katas-raj-heritage-3d.git
cd katas-raj-heritage-3d
python3 -m http.server 8000
# then open http://localhost:8000
```

## Role & context

Built by Amna Hafeez (Team Indus) as internship coursework connecting web engineering, lightweight ML, and AR/3D visualization to PMW's mission of making heritage sites like Katas Raj documentable and explorable by a wider audience.
