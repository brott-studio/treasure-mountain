# Berry Dragon's Land

A picture-book exploration toy for young children (5yo+).

**Live:** https://brott-studio.github.io/berry-dragon/

## Concept (v0.2)

The homepage is the original hand-drawn treasure map. Every named zone on the map is an invisible tappable hotspot (marked with a gentle pulsing dot). Tap a zone to visit it — each zone is a tiny self-contained interaction. Tap the back arrow to return to the map.

**Design rules:**
- No fail states. No gating. No timers. No losing.
- All 10 zones are always accessible.
- Zero reading required — visuals and audio only.
- Mobile/tablet first. Big tap targets.
- Auto-play audio unlocks on the first user tap (mobile-safe).

## Zones

| # | Zone | State |
|---|---|---|
| 1 | Vacation Island | ✅ Polished (sun rises/sets + chime) |
| 2 | Sea of Wave | 🟡 Stub (emoji + speech + pop) |
| 3 | Fantastic Forest | 🟡 Stub |
| 4 | Deserted Desert | 🟡 Stub |
| 5 | Golden Maze of Gold | 🟡 Stub |
| 6 | Fog of Misdirection | 🟡 Stub |
| 7 | Dragonberries | 🟡 Stub |
| 8 | Berry Dragon | 🟡 Stub |
| 9 | Quicksand Pool | 🟡 Stub |
| 10 | Treasure Mountain | 🟡 Stub |

## Tech

- Single `index.html`, vanilla HTML/CSS/JS, zero dependencies
- Web Audio API for chimes and pops (no audio files)
- SpeechSynthesis for zone name announcements
- Images: `assets/map-original.jpg` (4032×3024, untouched) and `assets/map-web.jpg` (2000×1500, 430KB — served to web)

## Tweaking hotspot positions

Hotspot coordinates are normalized (0..1) and live in one place near the top of `index.html`:

```js
const ZONES = [
  { name: "Vacation Island", x: 0.08, y: 0.45, ... },
  ...
];
```

To visualize hotspots (magenta dashed rings + labels), flip `window.DEV = true` at the top of the `<script>`.

## Notes

- `assets/map-web.jpg` is a resized copy generated via PIL; regenerate with:
  ```
  python3 -c "from PIL import Image; im=Image.open('assets/map-original.jpg'); im.thumbnail((2000,2000), Image.LANCZOS); im.save('assets/map-web.jpg','JPEG',quality=85,optimize=True)"
  ```
