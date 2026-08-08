# Senet: Soul of Egypt — Build Plan

*Ancient strategy reimagined. A 5,000-year-old race game with modern UI, smooth visuals, and a 3D tomb museum.*

---

## The pitch in one line
Senet is the oldest board game we can still play — pharaohs were buried with it so they could keep playing in the afterlife. We bring it to mobile with a clean board, satisfying stick-casting, and an unlockable 3D museum of real Egyptian tomb art.

---

## What ships (single-file PWA, same recipe as Stonecutter)
- `index.html` — the whole app (inline CSS + JS), Three.js r128 from CDN
- `manifest.json` + `sw.js` — installable offline PWA
- `icon-192` / `icon-512` — app icons
- Deploys to `potassiumsolutions.github.io/senet` (GitHub Pages), same as your other web games

---

## The three layers

### 1. The Game (core loop)
- **30-square board**, 3 rows of 10, played in an S-path (boustrophedon): 1–10 left→right, 11–20 right→left, 21–30 left→right.
- **5 pawns each.** Classic opening: pawns pre-placed alternating on squares 1–10.
- **Casting sticks** (4 sticks, flat/round faces) instead of dice. Light faces up = how far you move. 0 light faces = a 5.
- **Throw of 1, 4, or 5 = roll again** (keeps tension and momentum).
- **Move forward, can't land on your own pawn.** Land on an opponent = swap places (a "capture" that sends them backward).
- **Guarded pairs** (two of a color side-by-side) can't be captured. **Blockade of three** in a row can't be passed. — this is the whole strategy.
- **Special squares (reconstruction rules, tunable):**
  - **15 — House of Rebirth (Ankh):** where trapped pieces re-enter.
  - **26 — House of Happiness (Nefer):** safe square, everyone aims to pass through it.
  - **27 — House of Water (Mai):** the trap. Land here and the Nile sweeps you back to 15.
  - **28 — House of Three Truths:** leave only with a throw of 3.
  - **29 — House of Re-Atoum:** leave only with a throw of 2.
  - **30 — House of Horus:** leave (bear off) with a throw of 1.
- **Win:** first to bear all 5 pawns off the far end.
- **Opponent:** local AI (greedy heuristic first; smarter later). Pass-and-play and online are later stretch goals.

### 2. The Feel (modern UI + visuals)
- v0.1: clean 2D board that plays great on a phone (tap a pawn, tap to move, animated stick throw).
- v0.2+: upgrade the board to Three.js 3D (the "smooth 3D visuals" hook) — same orbit/drag camera you already built for the Stonecutter museum.
- Sand/limestone palette, gold accents, papyrus texture, soft shadows, sound (stick clatter, pawn tap, capture chime).

### 3. The Meta / Edutainment (the reason it sticks)
Senet was a metaphor for the soul's journey through the **Duat** (the afterlife). We make that literal:
- **Winning a match unlocks an artifact** in a **3D museum** — reusing the exact Three.js voxel-museum framework from Stonecutter (`render3D`, orbit controls, drop-in animation, artifact cards).
- Each artifact = **a real Egyptian object or tomb-wall scene** + a plain-English card + a **hieroglyph translation** ("read the wall").
- Artifact set (starter): Ankh, Eye of Horus (Wedjat), Scarab, Djed pillar, Canopic jar, Was scepter, Sarcophagus, the Weighing of the Heart scene.
- Framing: each win moves your soul one gate further through the Duat toward the Field of Reeds.

---

## Roadmap
- **v0.1 (this scaffold):** playable 2D Senet vs. AI, stick-casting, capture/water/gates, win detection, museum stub with 3D voxel artifacts + cards. *← we are here*
- **v0.2:** polish rules edge-cases (must-stop-on-26, 3-blockade passing), better AI, sound, animations, tutorial overlay.
- **v0.3:** swap 2D board for Three.js 3D board; real hieroglyph cards; more artifacts; Duat progression map.
- **v0.4:** PWA install polish, icons, offline, deploy to GitHub Pages; optional Google Play wrapper (Capacitor) like your other apps.

## Open design questions (decide as we go)
- Exact rule set — Senet has no single surviving rulebook; we use the common Kendall/British-Museum reconstruction and tune for fun.
- Do 1/4/5 grant extra throws, or a different set? (Currently 1/4/5.)
- Bearing-off strictness (exact-throw gates vs. forgiving). Currently exact gates on 28/29/30.
- Museum art style: voxel (reuse Stonecutter) vs. flat illustrated tomb panels. Currently voxel for v0.1.
