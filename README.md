# 🗺️ KL Facility Heatmap

An interactive heatmap for exploring facility density and house price distribution across **Kuala Lumpur** — built as a single-file web app, no backend required.

> **Hackathon Demo** — drop `index.html` anywhere and it just works.

---

## What it does

Ever wondered where the cafes cluster in KL? Or which neighbourhoods are gym deserts? This tool lets you overlay different facility categories onto a live map and instantly see where things are dense — and where the gaps are.

Switch between seven layers with one click:

| Layer | What it shows |
|-------|--------------|
| 🏠 House Price | Relative property price density by area |
| ☕ Cafes | Where the coffee shops congregate |
| 👕 Laundry | Self-service laundry coverage |
| 🍜 Mamak | The heartbeat of KL — mamak stall density |
| 🏥 Clinic | GP and clinic availability |
| 💪 Gym | Fitness centre spread |
| 🏪 Convenience | 24-hour and convenience store reach |

Each layer has its own colour gradient so you can tell them apart at a glance. Red/hot = high density, blue/cool = sparse or missing.

---

## Areas covered

The map spans 16 KL neighbourhoods and surrounding areas:

KLCC · Bukit Bintang · Chow Kit · Mid Valley · Bangsar · Mont Kiara · PJ SS2 · Kepong · Wangsa Maju · Ampang · Setapak · Puchong · Sri Petaling · TTDI · Hartamas · Desa Park

---

## How to run it

No build step, no npm install, no server. Just open the file:

```bash
# Clone the repo
git clone https://github.com/kelokchan/kl-facility-heatmap.git
cd kl-facility-heatmap

# Open in your browser
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

Or host it anywhere static — GitHub Pages, Netlify, Vercel, an S3 bucket. It loads all dependencies from CDN.

---

## How to use the map

1. Open the page — it defaults to **House Price** density
2. Click any filter button in the header to switch layers
3. Use the map normally — scroll to zoom, drag to pan
4. The legend in the bottom-right tells you what you're looking at
5. Area name labels are pinned on the map as orientation guides

The **cool blue zones** on each layer are the interesting ones — they show where a facility type is underrepresented, which could be an opportunity for new businesses or infrastructure investment.

---

## Tech stack

- **[Leaflet.js](https://leafletjs.com/)** `v1.9.4` — map rendering
- **[leaflet-heat](https://github.com/Leaflet/Leaflet.heat)** `v0.2.0` — heatmap layer
- **[OpenStreetMap](https://www.openstreetmap.org/)** — base tile layer
- Vanilla HTML/CSS/JS — zero dependencies to install

The dark map aesthetic is achieved with a CSS `invert + hue-rotate` filter on the tile layer, with a counter-invert on the overlay panes so the heatmap colours stay accurate.

---

## Data note

The current dataset is **simulated** — points are procedurally generated around real KL landmarks with realistic density distributions. The `jitter()` function scatters N points within a spread radius around each area centre, with a weighted intensity value.

To use real data, replace the `data` object in the `<script>` block with actual lat/lng coordinates in the format `[lat, lng, intensity]`.

---

## Folder structure

```
kl-facility-heatmap/
└── index.html     # Everything — map, styles, data, and logic in one file
```

---

## License

MIT — use it, fork it, ship it.
