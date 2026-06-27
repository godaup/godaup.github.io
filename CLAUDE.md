# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page academic personal homepage (Patrick Godau) built with Jekyll and deployed automatically by GitHub Pages at https://godaup.github.io. Based on the [Minimal Light](https://github.com/yaoyao-liu/minimal-light) theme. Content is edited in Markdown/YAML; there is no application logic or test suite.

## Commands

```bash
bundle install                 # install gems (first run)
bundle exec jekyll serve       # local preview at http://localhost:4000 with live reload
bundle exec jekyll build       # build static site into _site/
```

Pinned to `jekyll ~> 3.8.5` (Gemfile) to match GitHub Pages. Deployment happens on push to `main` via GitHub Pages — there is no CI config in the repo.

## Architecture

The whole page is one document assembled from three editable content sources, rendered through one layout:

- **[index.md](index.md)** — `layout: homepage`. Holds the "About Me" and "Expertise" prose, then pulls in the awards and publications partials via `include_relative`.
- **[_includes/awards.md](_includes/awards.md)** — plain Markdown list of challenges and awards. Edit directly.
- **[_data/publications.yml](_data/publications.yml)** — structured publication entries under the `main:` key. **[_includes/publications.md](_includes/publications.md)** is the Liquid template that loops over them; do not duplicate publication markup, just add a YAML entry. The commented block at the top of the YAML is the field template (`title`, `authors`, `conference_short`, `conference`, `pdf`, `code`, `page`, `bibtex`, `notes`, `image`); fields left out are simply not rendered.
- **[_layouts/homepage.html](_layouts/homepage.html)** — the page shell: header (avatar, position, social icons) driven entirely by **[_config.yml](_config.yml)**, then `{{ content }}`.

### Conventions that matter

- **Author highlighting:** wrap the site owner's name in `<strong>Patrick Godau</strong>` inside `authors`. HTML is allowed and used throughout the content files.
- **Publication teaser images** live in `assets/img/teaser/`. To make one from a PDF figure, the YAML header documents: `convert -density 150 concept.pdf -quality 90 -background white -alpha remove -alpha off concept.png`.
- **Site identity / links** (title, position, affiliation, email, Google Scholar, CV, GitHub, fonts, analytics) are all `_config.yml` keys — change them there, the layout only reads them. Restart `jekyll serve` after editing `_config.yml`.

### Styling and dark mode

`_config.yml` has `auto_dark_mode` and `font` toggles. The layout switches stylesheets based on them, so most style files come in **two parallel variants** that must be kept in sync:

- `_sass/minimal-light.scss` ↔ `_sass/minimal-light-no-dark-mode.scss`
- `assets/css/style.scss` ↔ `assets/css/style-no-dark-mode.scss`
- `assets/css/publications.css` ↔ `assets/css/publications-no-dark-mode.css`
- `assets/css/font.css` ↔ `assets/css/font_sans_serif.css` (selected by the `font` config value)

`.scss` files under `_sass`/`assets/css` are compiled by Jekyll into the `.css` files referenced by the layout. The favicon also has light/dark variants (`favicon.png` / `favicon-dark.png`), swapped at runtime by `assets/js/favicon-switcher.js`.
