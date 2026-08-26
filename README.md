# overview
Starting point for all GitHub/Microsoft Partner Offerings

## GitHub Pages

This repository is published as a static GitHub Pages site with Hugo. Offering details live in folders under `offerings/<offering name>/readme.md`; supporting static files for an offering should be kept in the same offering folder and linked from its `readme.md`.

If the shared Hugo template module is in a private/internal repository, add a repository secret named `HUGO_MODULES_TOKEN` with read access to `Partner-Offering-Catalog/static-page-template` so the Pages workflow can download Hugo modules.
