# 🗺️ Facility Heatmap

**Find the gaps, anywhere.** Flip between seven layers — house prices, cafes, laundry, street food, clinics, gyms, convenience stores — and see which neighbourhoods are packed and which are underserved. The cold spots are the point: they show where a new business or public service could land.

One `index.html`. No backend, no build step, no API keys.

> **Hackathon demo:** data is currently simulated around real Kuala Lumpur landmarks. The tool is built to work with any city — swap in your own `[lat, lng, intensity]` points and re-centre the map to use it anywhere.

---

## What it does

Pick a facility category and the map instantly paints a heatmap showing where that thing is concentrated — and more importantly, where it's missing. It's useful for business site selection, urban planning research, or just deciding where to move.

Switch between seven layers with one click:

| Layer          | What it shows                           |
| -------------- | --------------------------------------- |
| 🏠 House Price | Relative property price density by area |
| ☕ Cafes       | Where the coffee shops congregate       |
| 👕 Laundry     | Self-service laundry coverage           |
| 🍜 Street Food | Local food stall density                |
| 🏥 Clinic      | GP and clinic availability              |
| 💪 Gym         | Fitness centre spread                   |
| 🏪 Convenience | 24-hour and convenience store reach     |

Each layer has its own colour gradient. Red/hot = high density, blue/cool = sparse or missing.

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
3. Scroll to zoom, drag to pan
4. The legend in the bottom-right tells you what layer you're on
5. Neighbourhood labels are pinned on the map as orientation guides

The **cool blue zones** are the interesting ones — they show where a facility type is underrepresented.

---

## Adapting it to your city

The data lives in a single `data` object inside `index.html`. Each entry is an array of `[lat, lng, intensity]` points — intensity is a value between `0` and `1`.

```js
// Replace or extend this with your city's coordinates
const areas = {
  city_centre: [YOUR_LAT, YOUR_LNG],
  neighbourhood_a: [YOUR_LAT, YOUR_LNG],
  // ...
};

const data = {
  cafe: [
    ...jitter(...areas.city_centre, 80, 0.018, 1.0),
    // or supply raw [lat, lng, intensity] arrays directly
  ],
  // ...
};
```

Then update the map's initial view to centre on your city:

```js
const map = L.map('map').setView([YOUR_LAT, YOUR_LNG], 12);
```

That's it — no other changes needed.

---

## Tech stack

- **[Leaflet.js](https://leafletjs.com/)** `v1.9.4` — map rendering
- **[leaflet-heat](https://github.com/Leaflet/Leaflet.heat)** `v0.2.0` — heatmap layer
- **[Esri World Dark Gray](https://www.arcgis.com/home/item.html?id=358ec1e175ea41c3bf5c68f0da11ae2b)** — base tile layer (no API key required)
- Vanilla HTML/CSS/JS — zero dependencies to install

---

## Data note

The bundled dataset is **simulated** — points are procedurally generated around real KL landmarks using a `jitter()` helper that scatters N random points within a spread radius at a given intensity. It's a stand-in for real data; the visual patterns roughly match reality but are not authoritative.

To plug in real data, replace the `data` object entries with actual coordinates sourced from OpenStreetMap, government open data portals, or any spatial dataset.

---

## Folder structure

```
kl-facility-heatmap/
└── index.html     # Everything — map, styles, data, and logic in one file
```

---

## License

MIT — use it, fork it, ship it.
