# Static Frontend Demo

Open `index.html` directly in a browser. No server, SSH, Git checkout, or backend
is needed. The existing page layouts are retained as local HTML shells.

All observations are fictional, anchored to 2030-04-16. The inventory has four
hosts per site with names such as `alpha-compute-01`, reserved example addresses,
and invented measurements, certificate dates, versions, and crash events.
Site-Alpha and Site-Gamma both contain UP, DOWN, WARN, and NO DATA health checks.
The status color preview is green, red, yellow, and gray respectively.

The **Status colors** checkbox opts the status elements out of browser forced
colors for this static preview only. Uncheck it to use system contrast colors.
No Windows settings or production styles are changed. Navigation typography is
shared in `static-shared.css`: 14px text and a 20px line height on every page.

## Rebuild

From this directory, with the dependency in `requirements.txt` installed:

```bash
python build_static_site.py --check
python build_static_site.py
```

The builder reads only these local HTML shells and writes only within this folder.
It replaces the CSV exports under `data/` with five synthetic exports: one health
export per site, one version audit, and one monitor export. It does not import,
copy, or connect to production data. Validation checks the four-state coverage,
table schemas, tile summaries, internal page links, and known identifying markers.

Chart.js is loaded from the existing CDN reference. When unavailable, numeric
detail tables still work; charts require access to that CDN.