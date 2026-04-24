# Frederick County Beekeeping Association — Website

The source code for [www.frederickbees.org](https://www.frederickbees.org).
It is a [Jekyll](https://jekyllrb.com) site hosted for free on
[GitHub Pages](https://pages.github.com).

This README is written for the club's **webmaster** (who will maintain the
site) and for any **non-technical member** who wants to help keep it up to
date. You don't need to know HTML, CSS, or JavaScript — the site is
designed so almost every piece of content can be edited by changing a
Markdown file or a small YAML list.

---

## For the completely non-technical member

Welcome! If that word salad at the top scared you, take a breath. The
short version is:

- **Everything you see on the site** — meeting dates, the FAQ, the
  vendor list, the people on the contacts page — is kept in plain text
  files in this repository on GitHub.
- You can **edit those files right in your web browser** without
  installing anything. Assuming you are logged in to GitHub and have
  permissions to write to this repository, you should see a little pencil (✎) icon on every
  file. Click it, make a change, write a short note in the "Commit
  changes" box at the bottom, and save. That's it. Within a minute or
  two the live site updates itself.
- The two formats you'll run into are **Markdown** (for prose) and
  **YAML** (for lists of things like meetings or FAQs). Both are
  deliberately designed to look like notes you'd write by hand. The
  [Editing guide](#editing-guide) below shows exactly which file to
  touch for common changes.
- If something goes wrong, GitHub keeps the history of every change, so
  nothing is ever truly broken. The webmaster can always undo anything.

If you'd like help, reach out to the current webmaster before editing —
they're happy to walk you through your first change.

---

## How this site is built

The site is built with **Jekyll**, a tool that takes plain-text files
(Markdown for prose, YAML for structured data) and turns them into a
static website (plain HTML that any browser can serve). GitHub Pages
then hosts those HTML files for free on the public internet.

The design philosophy is **content vs. style, separated**:

| Where | What lives there | Who edits it |
|---|---|---|
| `pages/` and `_data/` | **Content** — the words, dates, lists, and links visible on the site | Any member with a GitHub account |
| `_layouts/`, `_includes/`, `_sass/`, `assets/css/` | **Style** — how the content looks, the grid, the colors, the fonts | The webmaster (requires more care) |

So adding a new vendor or FAQ answer is a safe one-line YAML change.
Redesigning the home page is not. The site is deliberately structured so
those two tasks don't get confused with each other.

---

## Repository layout

```
_config.yml          Site-wide settings (title, URLs, club details)
_data/               Structured content — one YAML file per dataset
    nav.yml              Main navigation + footer columns
    meetings.yml         Upcoming monthly meetings
    faqs.yml             Questions + answers for the FAQ page
    vendors.yml          Vendor / supplier list
    contacts.yml         Board officers + general inquiry info
    links.yml            Resource links (grouped by category)
    past_editions.yml    Fair history by year
    what_we_do.yml       Community outreach program list

_layouts/            HTML "skeletons" that wrap page content
    default.html         The outermost shell (<head>, header, footer)
    home.html            The home page
    page.html            A generic content page (title + prose)
    list.html            A page with a hero + custom body (FAQ, vendors, …)
    resource-list.html   Auto-renders a numbered link grid from _data/links.yml

_includes/           Reusable HTML snippets pulled into layouts
    header.html          Top navigation bar
    footer.html          Site footer with link columns
    svg-defs.html        Inline SVG logos and icons

_sass/               Styling — split into tokens, base, components, sections
    _tokens.scss         Colors, fonts, spacing, radii
    _base.scss           Resets and typography
    _components.scss     Buttons, cards, forms, etc.
    _sections.scss       Page-specific grids and heroes

pages/               One file per URL route
    about.md             /about/
    faq.md               /faq/
    meetings.md          /meetings/
    …etc                 Most are Markdown (.md); a few are HTML for custom layouts

assets/
    css/style.scss       Entry point — imports everything in _sass/
    img/                 Logos, photos (community/, logos/, etc.)
    docs/                PDFs (bylaws, forms)
    js/site.js           A small script for the mobile menu + scroll reveal

index.html           The home page
404.html             The "page not found" page
CNAME                Custom domain (www.frederickbees.org)
Gemfile              Ruby dependencies (only used for local preview)

.github/workflows/
    jekyll-gh-pages.yml  Builds and deploys the site on every push to main
```

**The key idea**: you should never need to touch HTML, CSS, or
JavaScript to update a meeting date, add a vendor, correct a typo, or
rewrite the About page. Everything routine lives in `_data/*.yml` and
`pages/*.md`.

---

## Editing guide

| To change… | Edit… |
|---|---|
| A meeting date or speaker | `_data/meetings.yml` |
| Past fair editions | `_data/past_editions.yml` |
| Add or update a vendor | `_data/vendors.yml` |
| Add or edit an FAQ entry | `_data/faqs.yml` |
| Board officers and their emails | `_data/contacts.yml` |
| Resource links (YouTube, organizations, periodicals, etc.) | `_data/links.yml` |
| Outreach / "What We Do" programs | `_data/what_we_do.yml` |
| The main navigation menu | `_data/nav.yml` |
| About, Contact, Donations, Members, etc. page text | the matching file in `pages/` |
| The Bee Removal form URL | `_config.yml` → `club.bee_removal_form` |
| Club meeting location / schedule (shown in header & footer) | `_config.yml` → `club.*` |
| Add a new page | Create `pages/new-page.md`, then add it to `_data/nav.yml` |
| Change colors, fonts, or spacing | `_sass/_tokens.scss` |
| Page layout, grid, hero styling | `_sass/_sections.scss` |

**Tip for quick edits**: on GitHub.com, open the file, click the pencil
(✎) in the upper right, make your change, then click "Commit changes"
at the bottom. The site will rebuild itself within a minute. You can
watch the deploy progress under the repo's **Actions** tab.

---

## Running the site locally (for the webmaster)

You only need to run Jekyll locally if you're making bigger changes and
want to preview them before pushing. Routine content edits can go
straight to GitHub via the web UI.

**Prerequisites** (one-time setup on macOS):

```bash
# Install Homebrew if you don't have it: https://brew.sh
brew install ruby@3.3

# Add this to your ~/.zshrc so the shell uses Homebrew's Ruby
# (macOS's built-in Ruby is too old for Jekyll)
export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"
```

**Each time you work on the site**:

```bash
# Install the Ruby gems this site needs (reads Gemfile)
bundle install

# Start the local preview server with live reload
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000> in your browser. Edits to any content
file will refresh the browser automatically.

When you're done, `Ctrl+C` to stop the server, then commit and push
your changes:

```bash
git add -A
git commit -m "Describe what you changed"
git push
```

---

## How deployment works

There is **no manual deploy step**. Every push to the `main` branch
triggers a GitHub Actions workflow (`.github/workflows/jekyll-gh-pages.yml`)
that:

1. Checks out the latest code.
2. Runs `jekyll build` to produce the static HTML in `_site/`.
3. Uploads that build as the GitHub Pages artifact and publishes it.

You can watch runs under the repo's **Actions** tab. A green check means
the live site is updated. A red X means the build failed — click into
the run to see the error. The most common cause is a syntax error in a
YAML file (e.g. a missing colon or bad indentation).

---

## Setting up the custom domain `www.frederickbees.org`

The repo is **technically published at two URLs**:

1. The default GitHub Pages URL: <https://frederickbees.github.io>
2. The custom domain: <https://www.frederickbees.org> (preferred)

The `CNAME` file in the repo root (containing just `www.frederickbees.org`)
tells GitHub to serve the site at the custom domain. For that to actually
work, DNS records must be set up at the domain registrar (wherever
`frederickbees.org` was purchased — e.g. Namecheap, GoDaddy, Google Domains).

**DNS records to configure** at the registrar:

| Type | Host / Name | Value |
|---|---|---|
| `CNAME` | `www` | `frederickbees.github.io` |
| `A` | `@` (apex) | `185.199.108.153` |
| `A` | `@` (apex) | `185.199.109.153` |
| `A` | `@` (apex) | `185.199.110.153` |
| `A` | `@` (apex) | `185.199.111.153` |

The four `A` records let `frederickbees.org` (without `www.`) redirect
to `www.frederickbees.org`. GitHub also publishes IPv6 (`AAAA`) records
— optional but nice to add:
`2606:50c0:8000::153`, `2606:50c0:8001::153`,
`2606:50c0:8002::153`, `2606:50c0:8003::153`.

**On GitHub, under Settings → Pages**:

1. Confirm **Custom domain** is set to `www.frederickbees.org`.
2. Wait for GitHub's DNS check to pass (a green check appears — may
   take a few minutes after DNS changes propagate).
3. Tick **Enforce HTTPS**. GitHub will provision a free Let's Encrypt
   certificate automatically (can take up to an hour after the DNS
   check passes).

**References**:

- [GitHub: Managing a custom domain for your Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub: Troubleshooting custom domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/troubleshooting-custom-domains-and-github-pages)

Once the custom domain is live, the old `frederickbees.github.io` URL
automatically redirects to it.

---

## Reference and learning links

**Markdown** (how to write prose with formatting)
- [Markdown Guide — basic syntax](https://www.markdownguide.org/basic-syntax/)
- [Kramdown reference](https://kramdown.gettalong.org/syntax.html) — Jekyll's flavor of Markdown
- [GitHub's Markdown cheatsheet](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

**YAML** (how to write structured data for `_data/*.yml`)
- [Learn YAML in 5 minutes](https://www.codeproject.com/Articles/1214409/Learn-YAML-in-five-minutes)
- Every file in `_data/` is itself a working example — copy an entry
  and tweak it.

**Jekyll** (the site generator)
- [Jekyll docs home](https://jekyllrb.com/docs/)
- [Jekyll front matter](https://jekyllrb.com/docs/front-matter/) — the `---` block at the top of every page
- [Jekyll data files](https://jekyllrb.com/docs/datafiles/) — how `_data/*.yml` is loaded
- [Liquid template language](https://shopify.github.io/liquid/) — the `{% ... %}` and `{{ ... }}` tags in layouts

**GitHub Pages** (the host)
- [GitHub Pages docs](https://docs.github.com/en/pages)
- [Supported Jekyll plugins on GitHub Pages](https://pages.github.com/versions/)

**Git basics** (for anyone learning)
- [GitHub's "Hello World" tutorial](https://docs.github.com/en/get-started/quickstart/hello-world)
- [GitHub Desktop](https://desktop.github.com) — a friendlier GUI if the command line isn't for you.

---

## Troubleshooting

**The site didn't update after I pushed.**
Check the **Actions** tab on GitHub. If the latest run has a red X,
click in to see the error. A build failure means nothing is deployed
— the previous working version stays live until you fix the problem.

**Build fails with a YAML error.**
Usually a missing colon, a stray tab, or inconsistent indentation. YAML
is picky. Paste the file into [yamllint.com](https://www.yamllint.com)
to spot the line.

**Build fails with a Liquid error.**
Something in a page's `{% ... %}` tags is referencing missing data.
Check the file mentioned in the error and compare to the corresponding
`_data/*.yml` structure.

**`bundle install` fails on macOS with "Ruby version too old".**
macOS ships Ruby 2.6 which Jekyll no longer supports. Install Ruby 3.3
via Homebrew and add `/opt/homebrew/opt/ruby@3.3/bin` to your PATH — see
the [Running locally](#running-the-site-locally-for-the-webmaster) section.

**The custom domain shows a certificate warning.**
HTTPS certificate issuance takes up to an hour after the DNS check
passes. If it's been longer, un-tick and re-tick **Enforce HTTPS** in
Settings → Pages to re-trigger provisioning.

---

## Getting help

- **Questions about content** (FAQ wording, meeting details, etc.) —
  raise it at a monthly meeting or email the board.
- **Questions about the site itself** — open a GitHub issue on this
  repo. The commit history is a log of every change ever made to the
  site, so it's easy to see who did what and why.

Nothing here is magic; it's just YAML and Markdown all the way down.
