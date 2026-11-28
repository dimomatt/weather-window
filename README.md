# Weather Window

Trail runs, rock climbs and ski lines that fit the forecast, the avalanche danger and your drive.

Pick a starting point, a date, a time window and a maximum one-way drive. The page pulls live data and sorts every option in range into Go, Caution or No-go, with the best time block inside your window and the reasons behind each call.

It is a single static page (`index.html`) with no build step and no backend. Everything is fetched from public APIs in the browser.

## Data sources

| What | Source |
|---|---|
| Hourly weather, past 48 h precipitation, modeled snow depth | [Open-Meteo](https://open-meteo.com/) (CC BY 4.0) |
| Avalanche danger by forecast area | [avalanche.org](https://avalanche.org/) map layer (CAIC and other centers) |
| Drive times | [OSRM](https://project-osrm.org/) demo server, with a distance-based estimate as fallback |
| Place search | Open-Meteo geocoding and [Photon](https://photon.komoot.io/) |
| Extra trails, crags and ski routes | [OpenStreetMap](https://www.openstreetmap.org/copyright) via Overpass |
| Extra crags, snow couloirs, and the route list for each crag | [OpenBeta](https://openbeta.io/) (open climbing database) |
| Terrain aspect and slope where unknown | Copernicus GLO-90 elevation via Open-Meteo |

## How the calls are made

- **Runs:** wind, cold, heat, storms, darkness, snow or mud on the trail, and avalanche paths on alpine routes in winter.
- **Climbs:** rock temperature adjusted for sun by wall aspect, wind, current precipitation, and drying time after rain or snow. Soft sandstone needs about two dry days.
- **Routes:** every crag card can list its routes from OpenBeta, grouped by wall in left-to-right order, with style and grade filters that carry across crags.
- **Ski lines:** the zone's headline (highest) avalanche danger combined with the line's terrain class (ATES) in a conservative matrix, plus modeled snow depth, new snow with wind, warming on sunny aspects and rain on snow.

This is a planning filter, not a forecast. Read the full avalanche forecast and check road and trail status before you go.

## Editing the catalog

The curated Front Range and I-70 objectives live in the `CATALOG` array near the top of the `engine` script in `index.html`. Each entry documents its fields in the comment above the array. Distances, gains and elevations are approximate; ski-line aspects and elevations follow the route pages linked in each entry's `src`.
