# Product

<!-- impeccable:product-schema 1 -->
<!-- Inferred from README.md; user asked for no questions. Confirm when convenient. -->

## Platform

web

## Users

(inferred) Hackathon judges, would-be business owners, urban-planning researchers and people deciding where to live, browsing on laptop or phone. Their job: spot which neighbourhoods are packed with a facility and which are underserved.

## Product Purpose

GapMap paints a density heatmap per facility category (house price, cafes, laundry, street food, clinics, gyms, convenience) across a city. The cold spots are the point: they show where a new business or public service could land. Success = a visitor finds a gap within seconds of switching layers.

## Positioning

Gap-first, not map-first: the underserved area is the result, the dense area is context. One static file, no backend, no API keys, city-agnostic.

## Constraints

- Single `index.html`, Leaflet + leaflet.heat from CDN, no build step.
- Must open from `file://` (Esri tiles chosen because OSM blocks file:// Referer).
- Data is simulated around real Kuala Lumpur / Klang Valley landmarks; must stay labelled as demo data.
- Seven layers, one active at a time.
