# overview

Starting point for all GitHub/Microsoft Partner Offerings

## GitHub Pages

This repository is published as a static GitHub Pages site with the generator in
[`Partner-Offering-Catalog/static-page-template`](https://github.com/Partner-Offering-Catalog/static-page-template).

Site content lives under `content/`:

- Every folder under `content/` becomes a navigation entry and **must** contain a
  `README.md`, which is the page shown for that entry.
- `content/framework.md` is the shared delivery framework, at the root of the menu.
- `content/authoring.md` is at the root of the menu as well, so the **Offerings** entry
  lists offerings only.
- Offering details live in `content/offerings/<offering-name>/README.md`.
- Supporting Markdown for an offering stays in the same offering folder and is linked
  from its `README.md`. Decks, spreadsheets, and images go in an `assets/` folder
  inside the offering; `assets/` is published as-is and is not scanned for pages.
- `title`, `description`, and `weight` front matter control the page title,
  summary card text, and ordering. An offering also carries `type` (`In-Person` or
  `Virtual`), `audience`, `duration`, `level`, `owner`, `status`, `updated`, and `tags`.

`site.config.json` holds the site title, brand, description, repository link, and
hero cards.

Use `template/offering/` as the starting point for a new offering: copy it to
`content/offerings/<offering-name>/` and replace the placeholders. It sits outside `content/`
on purpose, so it is never published as a page and never appears in the navigation. See
`content/authoring.md` for the full field reference.

If the shared template repository is private or internal, add a repository secret
named `SITE_TEMPLATE_TOKEN` with read access to
`Partner-Offering-Catalog/static-page-template` so the Pages workflow can check it
out. The previous `HUGO_MODULES_TOKEN` secret is still accepted as a fallback.

## Issues

Two issue forms are available under **New issue**:

- **Engagement request** — request a delivery of an offering that is already in the catalog.
- **Offering proposal** — propose a new offering, or a substantial change to an existing one.

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
