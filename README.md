# Deep-Sky Session Planner

A single-file, offline-first web app for planning deep-sky astrophotography sessions. Enter your location, telescope/camera setup, and a date, and it tells you which objects are well placed for the whole night — with framing, filter recommendations, and a searchable catalog of 1,250+ objects.

**Live version:** https://gpassera.github.io/deep-sky-planner/index

No installation, no account, no server. It's a single HTML file that runs entirely in your browser.

## Features

- **Real astronomical calculations** — sun position, local sidereal time, and object altitude computed live from standard low-precision formulas, not pre-baked tables. Works for any date, past or future.
- **Astronomical twilight window** — automatically finds dusk/dawn for your location and date, with a fallback to nautical twilight near the summer solstice at high latitudes.
- **FOV framing** — see how much of your field of view each object fills, with a mini visual diagram per object.
- **FOV calculator** — compute your field of view from telescope focal length + camera sensor (manual entry, common sensor presets, or pixel size + resolution).
- **Narrowband guidance** — Hα / OIII / SII signal strength per object where known, plus a clear "RGB / broadband" flag for galaxies, clusters, reflection and dark nebulae.
- **1,255 built-in objects** across NGC, IC, Sharpless, Barnard (dark nebulae), and LDN catalogs, filterable by type, imaging mode (narrowband/RGB/all), and minimum altitude.
- **Add your own objects** — manual entry (RA/Dec/size/filters), or instant lookup against the built-in catalog by name or common designation (e.g. "M42", "NGC7635", "Sh2-115").
- **Sort by visibility** — objects with the best coverage of the night are shown first.
- **Red-light mode** — a one-click toggle to preserve night vision while using the tool at the eyepiece.
- **Reference links** — quick links to Astrobin and NOIRLab's image galleries per object (opens their search page; you paste/type the object name shown).

## Usage

1. Open the [live version](https://gpassera.github.io/deep-sky-planner/index) or download `deep-sky-planner-v4_1.html` and open it in any browser.
2. Set your date, latitude/longitude, field of view (or use the FOV calculator), and minimum altitude threshold.
3. Browse the results, sorted by how much of the night each object stays above your altitude threshold.
4. Optionally add objects not in the built-in catalog via the "Add object" panel.

## Data sources & attribution

- **NGC/IC data** derived from [OpenNGC](https://github.com/mattiaverga/OpenNGC) by Mattia Verga (CC-BY-SA-4.0), which aggregates data from NED, HyperLEDA, SIMBAD and other sources.
- **Sharpless catalog** positions/sizes compiled from published amateur CCD imaging references.
- **Barnard dark nebulae** from Barnard (1927) and Dutra & Bica (2002), via a public compilation by Richard Powell (atlasoftheuniverse.com).
- **LDN (Lynds' Catalogue of Dark Nebulae)** subset cross-referenced with Barnard numbers, derived from Lynds (1962) via Wikipedia's tabulated data.

Object type classifications, sizes, and narrowband filter ratings for bulk-imported catalog entries are approximate; a small set of curated objects have filter ratings cross-checked against real imaging data (via Astrobin search).

## Known limitations

- **No live data lookups.** All astronomical object data is baked into the file. There's no network call to any catalog or database at runtime — this is intentional, for offline reliability.
- **No persistent storage outside Claude.ai.** If you open this file standalone (downloaded, or via GitHub Pages), objects you add manually are only kept for the current browser session — they are not saved between visits. (Only within Claude.ai's own artifact environment does the app have access to persistent storage.)
- **Astrobin/NOIRLab links** open their search pages; they do not pre-fill or auto-execute a search (their apps don't support reliable deep-linking for this). The object name is shown next to the link for you to type in.
- Bulk-imported catalog entries (marked in their notes) have unverified or estimated Hα/OIII/SII ratings — treat them as a starting point, not a guarantee.

## License

The code in this file may be freely used, modified, and redistributed. Catalog data retains the attribution and licensing terms of its original sources listed above.
