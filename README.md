# KODKOD

Edition 0.0.1 — Wireframe isometric tank combat in a single-file HTML5 build.

## Files

- `index.html` — the entire game (Three.js loaded from a CDN at runtime).
- `sfx/` — 20 procedural tank SFX samples, loaded by the game on first user interaction.

## Play locally

These files use `fetch()` to load the SFX, which most browsers block on `file://`. Serve over HTTP:

```
cd kodkod
python3 -m http.server 8000
```

Then open `http://localhost:8000/` in any modern desktop browser.

## Deploy to GitHub Pages

1. Create a new repo, e.g. `kodkod`.
2. Drop `index.html` and the `sfx/` folder into the repo root and push.
3. In the repo settings → **Pages**, choose `main` / `/ (root)`.
4. After a minute, your site is live at `https://YOUR_USERNAME.github.io/kodkod/`.

The CDN-loaded Three.js (`unpkg.com/three@0.160.0`) means the game has no build step.

## Controls

- **W / S** — forward / reverse
- **A / D** — steer body
- **Mouse** — aim
- **LMB hold + release** — charge & fire cannon
- **RMB hold** — heavy MG (anti-air + chip damage)
- **Scroll** — zoom
- **ESC** — pause
- **≡** (top-right) — open settings panel

## Settings panel

`GAME` campaign / AI · `PHYS` vehicle / weapons / heli · `STYLE` palette / wire / camera · `SFX` volumes / synth profile / sample routing · `MAP` terrain / editor / import-export.

The **SFX** tab lets you swap each game event between the procedural synth and any of the 20 sampled sounds (or *none*). The **MAP** tab includes an in-game brush editor for placing trees and rocks.

## Survive mode

Hostiles double each round. The world starts compact (272 × 272) and **expands 10% every round**, with trees and rocks growing proportionally so the new boundary fills in naturally rather than leaving an empty rim. Helicopters drop first-aid kits between waves. The base auto-rebuilds 180 s after being destroyed.
