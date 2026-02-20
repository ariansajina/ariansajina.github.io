# CLAUDE.md

This file provides guidance for AI assistants working on this repository.

## Project Overview

Personal blog and portfolio website for Arian Šajina, built with Jekyll and hosted on GitHub Pages. The site includes a blog with tag filtering, an about page, and a calendar of performances/events.

## Technology Stack

- **Jekyll** (v3.10.0) — static site generator
- **Minima** (v2.5.1) — base theme
- **SCSS/Sass** — custom styling layered on top of Minima
- **Kramdown** — Markdown processor
- **Liquid** — Jekyll's templating language
- **GitHub Pages** (`github-pages ~> 232`) — hosting and CI/CD

Ruby gems are managed via Bundler. The `Gemfile.lock` is committed and should not be manually edited.

## Repository Structure

```
.
├── _config.yml          # Site-wide Jekyll configuration
├── _layouts/
│   ├── home.html        # Homepage layout (post list + tag sidebar)
│   └── post.html        # Individual blog post layout
├── _posts/              # Blog posts (YYYY-MM-DD-title.md)
├── assets/
│   └── main.scss        # Custom styles (imports Minima, then overrides)
├── images/              # Static image assets
├── index.md             # Homepage (uses home layout)
├── about.md             # About page
├── calendar.md          # Performances/events calendar
├── Gemfile              # Ruby dependencies
└── Gemfile.lock         # Locked dependency versions
```

Jekyll builds into `_site/` (gitignored). Never commit `_site/`, `.jekyll-cache/`, or `.sass-cache/`.

## Local Development

```bash
bundle install
bundle exec jekyll serve
# Site available at http://127.0.0.1:4000/
```

No npm, no Node.js build step. All styling is SCSS processed by Jekyll.

## Content Conventions

### Blog Posts

Posts live in `_posts/` and must follow the filename format:

```
YYYY-MM-DD-slug-here.md
```

Every post requires YAML front matter:

```yaml
---
layout: post
title: "Post Title"
date: YYYY-MM-DD
tags: [tag1, tag2]
---
```

- `layout` must be `post`
- `tags` is an array; use lowercase, single-word tags where possible
- Tags automatically appear in the sidebar filter on the homepage and as links in the post header
- Tag links from post pages use the URL pattern `/?tag=<slugified-tag>`

### Pages

Static pages (about, calendar, etc.) use YAML front matter:

```yaml
---
layout: page
title: Page Title
permalink: /path/
---
```

`header_pages` in `_config.yml` controls which pages appear in the site nav:

```yaml
header_pages:
  - about.md
  - calendar.md
```

Add a file to this list to include it in the navigation header.

### Homepage

`index.md` uses `layout: home` and should remain nearly empty — the layout renders the post list and tag sidebar automatically.

## Styling

`assets/main.scss` starts with a Jekyll front matter block (two lines of `---`) followed by `@import "minima"`. Custom rules are added after the import.

Custom components defined in `main.scss`:

| Class | Purpose |
|---|---|
| `.home-container` | Flex wrapper for sidebar + post list |
| `.tag-sidebar` | Left sidebar with tag filter links |
| `.tag-list` / `.tag-link` | Tag list and individual link styles |
| `.tag-count` | Post count shown next to each tag |
| `.post-list-container` | Right-side post list area |
| `.post-tags` / `.tag` | Tag display on individual post pages |
| `.image-row` | Horizontal image gallery (flexbox) |

Responsive breakpoint: `max-width: 600px` — sidebar stacks below the post list, tag list switches to horizontal wrap.

Color palette (matching Minima defaults):
- Link/active blue: `#2a7ae2`
- Meta/muted gray: `#828282`
- Tag count light gray: `#b0b0b0`

Do not introduce external CSS frameworks. Keep custom CSS minimal and layered on Minima.

## Layouts

### `_layouts/home.html`

Extends `default`. Renders a sidebar (`tag-sidebar`) and a post list (`post-list-container`) side by side. Tag filtering is handled with vanilla JavaScript at the bottom of the file:

- Clicking a tag link sets it as active and hides non-matching posts
- On page load, checks `?tag=` URL parameter and applies the filter automatically
- Post list items carry a `data-tags` attribute with space-separated, lowercase tag slugs

### `_layouts/post.html`

Extends `default`. Includes:

- Schema.org microdata (`itemscope`, `itemtype`, `itemprop` attributes) for SEO
- Microformat classes (`h-entry`, `p-name`, `dt-published`, `e-content`, `u-url`) for semantic markup
- Post navigation (previous/next links) rendered if either `page.previous` or `page.next` exists
- Optional Disqus comments (requires `disqus.shortname` in `_config.yml` — currently not configured)

Do not remove the microdata or microformat attributes — they are intentional for SEO and feed readers.

## Jekyll Configuration (`_config.yml`)

Key settings:

| Key | Value | Notes |
|---|---|---|
| `theme` | `minima` | Base theme |
| `permalink` | `pretty` | URLs without `.html` extension |
| `show_excerpts` | `true` | Shows post excerpts on homepage |
| `header_pages` | `about.md`, `calendar.md` | Pages shown in site nav |

Plugins enabled: `jekyll-feed` (generates `/feed.xml`) and `jekyll-seo-tag` (injects meta tags).

The `exclude` list keeps `Gemfile`, `Gemfile.lock`, and `README.md` out of the built site.

## Deployment

GitHub Pages builds and deploys automatically on push to the `main` branch. No manual build or deploy step is needed. The `master` branch is used for local development; `main` is the GitHub Pages production branch.

Do not commit built files (`_site/`) — GitHub Pages runs the Jekyll build itself.

## Git Workflow

- Development branches follow the pattern `claude/<description>-<id>`
- Commit messages should be descriptive and in the imperative mood
- Push feature branches with `git push -u origin <branch-name>`

## What to Avoid

- Do not add JavaScript frameworks or npm dependencies — the site is intentionally zero-build on the frontend
- Do not modify `Gemfile.lock` manually
- Do not commit `_site/`, `.jekyll-cache/`, `.sass-cache/`, `.bundle/`, or `.DS_Store`
- Do not add Disqus without adding the `shortname` to `_config.yml`
- Do not change permalink structure — existing URLs must remain stable
- Do not strip microdata or microformat attributes from `_layouts/post.html`
