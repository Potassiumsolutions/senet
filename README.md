# Senet: Soul of Egypt

The oldest board game on Earth, reimagined for mobile. Cast the ancient sticks, race 5 pawns across 30 squares, dodge the Nile, and cross the Duat — the Egyptian underworld. Every match you win unlocks a real Egyptian artifact in a 3D museum.

**▶ Play online:** https://potassiumsolutions.github.io/senet/

**Status:** v0.1 vertical slice — playable vs. AI, with the museum framework wired up.

## Files
- `index.html` — the whole game (single-file PWA, Three.js r128 from CDN)
- `manifest.json` / `sw.js` — installable, offline-capable PWA
- `icon-192.png` / `icon-512.png` — app icons
- `PLAN.md` — full design + roadmap
- `assets/` — future art

## Run it
Open `index.html` in a browser, or serve the folder:
```bash
npx serve .
```
Then open the shown URL on your phone (same Wi-Fi) or desktop.

## How it plays
Cast 4 sticks — light faces up = squares to move (all dark = 5). Throws of 1/4/5 grant another throw. Land on the opponent to swap them backward; two pawns side-by-side are safe; three in a row wall the path. Square 27 (the Nile) sends you back to 15. Squares 28/29/30 release a pawn only on an exact 3/2/1. Bear all 5 pawns off to win.

## Reused from Stonecutter
The 3D museum (`render3D`, orbit/drag camera, voxel artifacts, drop-in animation) is the same Three.js pattern built for Stonecutter's monument museum.

*A Potassium Solutions game.*
