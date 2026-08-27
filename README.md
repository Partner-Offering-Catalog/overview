# overview

Starting point for all GitHub/Microsoft Partner Offerings

## GitHub Pages

This repository is published as a static GitHub Pages site with the generator in
[`Partner-Offering-Catalog/static-page-template`](https://github.com/Partner-Offering-Catalog/static-page-template).

Site content lives under `content/`:

- Every folder under `content/` becomes a navigation entry and **must** contain a
  `README.md`, which is the page shown for that entry.
- Offering details live in `content/offerings/<offering-name>/README.md`.
- Supporting static files for an offering should be kept in the same offering
  folder and linked from its `README.md`; the Pages workflow publishes them next
  to the offering page.
- `title`, `description`, and `weight` front matter control the page title,
  summary card text, and ordering.

`site.config.json` holds the site title, brand, description, repository link, and
hero cards.

Use `template/offering/` as the starting point for a new offering: copy it to
`content/offerings/<offering-name>/`, rename `readme.md` to `README.md`, and
replace the placeholders.

If the shared template repository is private or internal, add a repository secret
named `SITE_TEMPLATE_TOKEN` with read access to
`Partner-Offering-Catalog/static-page-template` so the Pages workflow can check it
out. The previous `HUGO_MODULES_TOKEN` secret is still accepted as a fallback.

## Local preview

The generator lives in the template repository, so build against a local checkout
of it:

```bash
git clone https://github.com/Partner-Offering-Catalog/static-page-template.git
cd static-page-template
npm ci
rm -rf content && cp -R ../overview/content content
cp ../overview/site.config.json site.config.json
BASE_URL=/ npm run build
npm run serve
```
