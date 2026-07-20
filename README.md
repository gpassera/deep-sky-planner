# Deep-Sky Session Planner

A single-file, offline-first web app for planning deep-sky astrophotography sessions. Enter your location, telescope/camera setup, and a date, and it tells you which objects are well placed for the whole night — with framing, filter recommendations, and a searchable catalog of 10,000+ objects.

**Created & maintained by Giuseppe Passera** — [www.giuseppepassera.com](https://www.giuseppepassera.com) — gpasser@gmail.com

**Live version:** https://gpassera.github.io/deep-sky-planner/index

No installation, no account, no server. It's a single HTML file that runs entirely in your browser.

## Features

- **Real astronomical calculations** — sun position, local sidereal time, and object altitude computed live from standard low-precision formulas, not pre-baked tables. Works for any date, past or future.
- **Astronomical twilight window** — automatically finds dusk/dawn for your location and date, with a fallback to nautical twilight near the summer solstice at high latitudes.
- **FOV framing** — see how much of your field of view each object fills, with a mini visual diagram per object.
- **FOV calculator** — compute your field of view from telescope focal length + camera sensor (manual entry, common sensor presets, or pixel size + resolution).
- **Narrowband guidance** — Hα / OIII / SII signal strength per object where known, plus a clear "RGB / broadband" flag for galaxies, clusters, reflection and dark nebulae.
- **10,282 built-in objects** across NGC, IC, Sharpless, Barnard (dark nebulae), LDN, and the SAC (Saguaro Astronomy Club) catalogs, filterable by type, imaging mode (narrowband/RGB/all), and minimum altitude. A "Hide raw catalog objects" toggle (on by default, given the size of the SAC set) keeps the default view focused on the curated/OpenNGC subset with richer notes and narrowband ratings.
- **Add your own objects** — manual entry (RA/Dec/size/filters), or instant lookup against the built-in catalog by name or common designation (e.g. "M42", "NGC7635", "Sh2-115").
- **Sort by visibility** — objects with the best coverage of the night are shown first.
- **Moon phase & interference** — graphical moon phase indicator, illumination %, rise/set within the dark window, and per-object angular separation from the Moon at culmination.
- **Per-object altitude track chart** — a mini graph for each object showing altitude over the night, with the dark-sky window, your minimum-altitude threshold, and the culmination time highlighted.
- **Cloud cover forecast** — average/peak cloud cover during the dark-sky window for the selected night, via the free Open-Meteo API (covers roughly the next 16 days).
- **Multi-night overview** — a 21-night outlook combining moon illumination, darkness duration, and cloud forecast, to quickly spot the best upcoming nights.
- **Saved sessions** — save/load full setups (date, location, FOV, thresholds, filters, custom objects) by name, stored locally in your browser.
- **Red-light mode** — a one-click toggle to preserve night vision while using the tool at the eyepiece.
- **Reference links** — quick links to Astrobin and NOIRLab's image galleries per object (opens their search page; you paste/type the object name shown).

## Usage

1. Open the [live version](https://gpassera.github.io/deep-sky-planner/index) or download `index.html` and open it in any browser.
2. Set your date, latitude/longitude, field of view (or use the FOV calculator), and minimum altitude threshold.
3. Browse the results, sorted by how much of the night each object stays above your altitude threshold.
4. Optionally add objects not in the built-in catalog via the "Add object" panel.

## Data sources & attribution

- **NGC/IC data** derived from [OpenNGC](https://github.com/mattiaverga/OpenNGC) by Mattia Verga (CC-BY-SA-4.0), which aggregates data from NED, HyperLEDA, SIMBAD and other sources.
- **SAC DeepSky database v8.1 (2010)**, data courtesy of the [Saguaro Astronomy Club](https://www.saguaroastro.org/sac-downloads/) (Phoenix, AZ) — ~9,000 additional objects (galaxies, clusters, planetary/dark/bright nebulae, asterisms, multiple stars, and objects in the Magellanic Clouds), deduplicated against the catalogs above. Freely distributed by the club for the amateur astronomy community; no formal license file accompanies the data, so it's credited here per the community convention used by other tools built on it.
- **Sharpless catalog** positions/sizes compiled from published amateur CCD imaging references.
- **Barnard dark nebulae** from Barnard (1927) and Dutra & Bica (2002), via a public compilation by Richard Powell (atlasoftheuniverse.com).
- **LDN (Lynds' Catalogue of Dark Nebulae)** subset cross-referenced with Barnard numbers, derived from Lynds (1962) via Wikipedia's tabulated data.

Object type classifications, sizes, and narrowband filter ratings for bulk-imported catalog entries are approximate; a small set of curated objects have filter ratings cross-checked against real imaging data (via Astrobin search).

## Known limitations

- **No live catalog lookups.** All built-in astronomical object data is baked into the file — there's no network call to any catalog/database for that part, by design, for offline reliability. The optional cloud forecast is the one feature that does call an external API (Open-Meteo) and requires an internet connection.
- **Saved objects and sessions are per-browser.** Custom objects and saved sessions are stored in your browser's local storage — they follow the browser/device you used to add them, not the file itself. Clearing browser data removes them.
- **Astrobin/NOIRLab links** open their search pages; they do not pre-fill or auto-execute a search (their apps don't support reliable deep-linking for this). The object name is shown next to the link for you to type in.
- Bulk-imported catalog entries (marked in their notes) have unverified or estimated Hα/OIII/SII ratings — treat them as a starting point, not a guarantee. This applies especially to the ~9,000 SAC entries, where narrowband ratings are type-based defaults (e.g. all galaxies get "none"), not per-object assessments.
- **The SAC catalog is large.** With it enabled ("Hide raw catalog objects" unchecked), the page renders 10,000+ object cards, which is noticeably slower to compute and scroll through than the curated ~1,250-object view. A handful of duplicate entries exist across catalogs (the same physical object catalogued under slightly different coordinates/names in two source lists) despite deduplication; they're harmless but you may occasionally see the same object twice.
- Cloud cover forecasts are only available for roughly the next 16 days (Open-Meteo's forecast horizon); planning further ahead will show moon phase and darkness duration only.

## License

© Giuseppe Passera — [www.giuseppepassera.com](https://www.giuseppepassera.com) — gpasser@gmail.com

Personal, non-commercial use, inspection, and modification for personal use are permitted. Redistribution that removes or alters authorship notices, claims of authorship by others, and commercial use are **not** permitted without the author's prior written consent. See [LICENSE.md](./LICENSE.md) for full terms.

Catalog data retains the attribution and licensing terms of its original sources listed above.
