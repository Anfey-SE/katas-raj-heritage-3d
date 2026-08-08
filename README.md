# Katas Raj Temples — Site Survey Record

A digital preservation working file for the Katas Raj Temples (Chakwal, Punjab, Pakistan), built as part of the **TechRealm × PreserveMy.World (PMW) Platform & Web Engineering internship**, Team Indus.

**Live site:** https://katas-raj-heritage-3d.vercel.app

## What this is

A field-survey-styled record of one heritage site, presented as three exhibits a reviewer can switch between:

- **Exhibit A — Photograph.** The primary field capture of the site.
- **Exhibit B — AR Survey Lines.** A manually logged measurement overlay on the field photo, showing estimated structural spans between key points.
- **Exhibit C — Capture-to-3D.** A first-pass depth-relief mesh generated from photo luminance (brighter pixels are displaced forward, then smoothed to remove per-pixel noise), rendered in Three.js with a soft contact shadow and a cinematic dolly-in on load. This is **not** a full photogrammetry reconstruction — it's an early-stage visualization step toward a walkable reconstruction, and is labeled as such in the UI ("Depth Relief · First Pass").

Also included: a pretrained image classifier run against the field photographs (`ml_visualization_output.png`), and `RESEARCH.md`, a research log on 3D reconstruction methods considered for heritage sites.

## Controls (Exhibit C)

- Drag to orbit
- Right-click drag (or shift+drag) to pan
- Scroll to zoom

## Tech stack

- Vanilla HTML/CSS/JS
- Three.js r128 (CDN, no build step)
- Deployed via Vercel

## Module 23 revision (01 Aug 2026)

This artifact was originally built in Module 10 and revised for certificate-readiness in Extension Sprint 5:

- Added this README (previously missing)
- Corrected a stale module reference in the UI (was showing "Module 10/18" from an earlier program structure)
- Added pan controls to the Exhibit C viewer — previously orbit/zoom only, no way to move through the scene
- Smoothed the depth-relief geometry (box blur on luminance before displacement) to remove noisy per-pixel bumps, while keeping the photo texture sharp
- Added a soft contact shadow so the mesh reads as resting in the scene rather than floating
- Added a slow cinematic dolly-in on load instead of an instant camera pop
- Fixed a real performance bug: the Exhibit C iframe was loading unconditionally on every page visit, even for visitors who never opened that tab. It's now lazy-loaded only on first click, which stabilized and improved Lighthouse Performance scores.

## Module 28 revision (08 Aug 2026)
Performance fix for Extension Sprint 8:

- Diagnosed a Lighthouse Performance score of 52, largely caused by an oversized hero image (2160×1346px served at a 673×495px display size) and a font-loading mismatch.
- Converted hero images to WebP — improved score to 58, but Lighthouse's own diagnostics showed the image was still far larger than its display size.
- Resized the hero image to 900px wide using Lanczos3 resampling — the correct fix, since compression alone wasn't enough.
- Corrected a font-weight mismatch: the site was loading unused Fraunces/Inter weights while missing IBM Plex Mono 600, which the tabs and ledger values actually use (previously causing fake-bold rendering).
- Result: Performance improved from 52 → 80. Accessibility, Best Practices, and SEO remained at 100 throughout.
- Before/after Lighthouse screenshots: [linked in evidence folder](https://drive.google.com/drive/folders/1YghzmCT5SshKxxVxLpx_my8iEbNYTA2K?usp=sharing).

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
