# SnowRunner Save Editor (Web Port)

## What this web version supports

- Main save upload/edit/download:
  - Game Stats editor (`distance` + `gameStat`)
  - Money & Rank
  - Time
  - Objectives+ (search/filter/select and mark complete)
    - Uses embedded catalog data only (no runtime fetch required)
    - Search includes key/name/region/category/type fields from catalog data
  - Regions+ (desktop-aligned bulk region actions)
    - Upgrades
    - Watchtowers
    - Discoveries
    - Levels
    - Garages
    - Optional legacy Missions / Contests toggle
  - Rules (desktop-aligned New Game+ rule editor)
- CommonSslSave upload/edit/download:
  - Trials
  - PROS entitlements
  - Achievements unlock for existing entries

All edits are done in-browser. Files are not uploaded to a server. The folder loader also supports decoded WGS / Xbox App save folders and rebuilds their original layout on zip download.

## Objectives+ data notes

- Embedded catalog is bundled in `app.js`, so Objectives+ works even on `file://`.
- If you want frequent updates, regenerate `data/maprunner_data.csv` with your Python tool, then run `python data/embed_catalog_into_app.py` to re-embed it into `app.js`.
- Optional automation: `.github/workflows/update-objectives-catalog.yml` can run in GitHub Actions on schedule and auto-refresh `data/maprunner_data.csv` + embedded catalog in `app.js`.
