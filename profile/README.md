**OSMCha** (OpenStreetMap Changeset Analyzer) is a tool for reviewing and visualizing edits to OpenStreetMap. It aims to help human reviewers more easily spot editing mistakes and vandalism. The production instance is available at [osmcha.org](https://osmcha.org).

Each time someone makes an edit to OpenStreetMap, it creates a record called a Changeset. The changeset records both what the user changed (additions, modifications, and deletions) as well as metadata (their user name, timestamp, and a description they provided about their changes). OSMCha can show any changeset as a visualization on a map, with added elements in green, modified elements in yellow or gray, and deleted elements in red. OSMCha also lets you search or filter changesets to find those with certain properties, like those by a certain user, or those that modified elements with certain OSM tags.

OSMCha also includes automated checks to flag changesets that may need special attention from reviewers, for example changesets that modify a huge number of elements or whose descriptions contain suspicious words. These checks help volunteers efficiently identify changesets that may need closer examination.

OSMCha is an [OpenStreetMap US](https://www.openstreetmap.us/) Charter Project. You can support its development and maintenance by [making a donation](https://openstreetmap.app.neoncrm.com/forms/osmcha).

## Architecture

**Web application**
- [osmcha-frontend](https://github.com/OSMCha/osmcha-frontend) - React web application
- [osmcha-django](https://github.com/OSMCha/osmcha-django) - Django backend providing the REST API

**Augmented Diff pipeline**
- [osmx-adiff-builder](https://github.com/OSMCha/osmx-adiff-builder) - Scripts to generate augmented diffs from OSM replication files, using an [OSMExpress](https://github.com/bdon/OSMExpress) database
- [changeset-adiffs-worker](https://github.com/OSMCha/changeset-adiffs-worker) - Cloudflare Worker that processes new augmented diffs and computes tag changes
- Augmented diffs are served at [adiffs.osmcha.org](https://adiffs.osmcha.org/) for use by OSMCha and other tools

**Helper libraries**
- [osmcha](https://github.com/OSMCha/osmcha) - Python library for applying automated checks to changesets; used by the backend
- [osm-adiff-parser](https://github.com/OSMCha/osm-adiff-parser) - Parses augmented diff XML into JavaScript objects; used by the frontend
- [maplibre-adiff-viewer](https://github.com/OSMCha/maplibre-adiff-viewer) - MapLibre GL JS plugin for visualizing augmented diffs on a map; used by the frontend

There is also a command line tool called [osmcha-cli](https://github.com/OSMCha/osmcha-cli) which can show an OSMCha-style visualization of any augmented diff file (even if the diff does not represent a specific changeset).

## Bug reports

To report issues or request features, please file them in the [osmcha-frontend repository](https://github.com/osmcha/osmcha-frontend/issues).
