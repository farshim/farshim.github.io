# farshim.github.io

Personal academic site for Pooya Farshim, built with Jekyll and served by GitHub Pages.

Originally a fork of [AcademicPages](https://github.com/academicpages/academicpages.github.io)
(itself a fork of [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)).
The theme layer has since been replaced with a hand-written one; no vendored
framework code remains.

## Local development

```sh
bundle install
bundle exec jekyll serve --config _config.yml,_config.dev.yml
```

Then open <http://localhost:4000>.

## Layout of the repository

| Path | Purpose |
|---|---|
| `_pages/` | All site content. One file per page; each declares its own `permalink`. |
| `_layouts/` | `default.html` (page shell) and `page.html` (content + optional sidebar). |
| `_includes/` | `head`, `masthead`, `profile`, `footer`. |
| `_sass/` | `_tokens`, `_base`, `_layout`, `_content`, `_print`. |
| `assets/css/main.scss` | Imports the five partials. The only stylesheet. |
| `_data/navigation.yml` | Main nav. `url` must match the target page's `permalink`. |

There are **no collections**. Every page is written by hand in `_pages/`, so
adding a publication means editing `_pages/research.md` directly.

## Design system

Tokens live in [`_sass/_tokens.scss`](_sass/_tokens.scss) as CSS custom
properties, so the palette can be changed in one place and is overridden
wholesale for dark mode and for print.

- **Type** — system-font stacks only: a transitional serif for headings and
  titles, a neutral sans for body and UI. No web fonts, so no extra requests
  and no layout shift. Sizes are fluid via `clamp()` rather than stepped at
  breakpoints.
- **Colour** — warm ivory ground (`#faf9f5`) with near-black ink. Every token
  used for text meets WCAG AA in both light and dark themes. Note that the
  clay accent `#d97757` is only 2.96:1 on the ivory ground, so it is reserved
  for decoration (rules, hover borders, underline tints) and never used for
  text; links use `--accent-text` (`#a34f2a`, 5.37:1).
- **Layout** — CSS Grid and Flexbox. Line length is capped by `--measure`
  (~68 characters). The two-column layout collapses to one below `56rem`, and
  the nav becomes a disclosure panel below `40rem`.

## Adding a page

Create a file in `_pages/` with front matter:

```yaml
---
layout: page
title: "Title"
permalink: /some-path/
author_profile: true   # false drops the sidebar and centres the content
mathjax: true          # optional; loads MathJax 3 only on this page
---
```

Then add it to `_data/navigation.yml` if it belongs in the main nav.
