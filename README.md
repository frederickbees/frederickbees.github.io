# Frederick County Beekeeping Association — Website

A Jekyll site that runs for free on GitHub Pages.

## Layout

```
_config.yml          site settings + club details
_data/               all site content (navigation, meetings, FAQ, links, …)
_layouts/            page shells (default, home, page)
_includes/           reusable partials (header, footer, hero, SVG defs)
_sass/               styling — split into tokens, base, components, sections
pages/               one file per URL route. Markdown or minimal HTML.
assets/
  css/style.scss     entry point that imports _sass
  img/               logos, photos
  docs/              PDFs (bylaws, etc.)
index.html           home page
```

**All content lives in `_data/*.yml` and `pages/*.md`.** Styling lives in
`_sass/`. You should never need to touch HTML or CSS to update a meeting date,
add a vendor, or rewrite the mission statement.

## Running locally

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then visit <http://localhost:4000>.

## Deploying to GitHub Pages

1. Create a new repo named `<your-org>.github.io` (for a root-domain site) or
   any repo name (for a project site).
2. Unzip this package and push its contents to the repo's `main` branch.
3. In **Settings → Pages**, set **Source** to `Deploy from a branch` and
   **Branch** to `main` / `/ (root)`.
4. If you're using the custom domain `www.frederickbees.org`, add a `CNAME`
   file at the repo root with `www.frederickbees.org` inside.

Builds run automatically on every push.

## Editing guide

| To change… | Edit… |
|---|---|
| A meeting date | `_data/meetings.yml` |
| The Bee Removal form URL | `_config.yml` → `club.bee_removal_form` |
| Add a vendor | `_data/vendors.yml` |
| Add an FAQ entry | `_data/faqs.yml` |
| Edit the About page copy | `pages/about.md` |
| Add a page to the nav | `_data/nav.yml` |
| Change colors or fonts | `_sass/_tokens.scss` |

Nothing here is magic; it's just YAML and Markdown all the way down.
