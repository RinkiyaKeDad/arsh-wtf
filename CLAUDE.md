# CLAUDE.md

Guidance for working in this repo (arsh.wtf — a personal Hugo blog).

## What this is

- A **Hugo** static site (`config.toml`), deployed via **Netlify** (`netlify.toml`), served at https://arsh.wtf/.
- Blog posts live under `content/posts/<slug>/`. Each post is a page bundle: an `index.md` plus its images in the same folder.
- Build: `hugo` (local binary is `hugo v0.160.1+extended`). Output goes to `public/` — that's a generated artifact, don't hand-edit it.

## Theme: Ananke (git submodule)

- The theme is **Ananke**, pinned as a git submodule at `themes/ananke/` (see `.gitmodules`). `config.toml` sets `theme = 'ananke'`.
- Currently on **v2.19.0**. To bump: `git -C themes/ananke fetch --tags && git -C themes/ananke checkout <tag>`, then `hugo` to verify it builds, then commit the submodule pointer.
- Theme docs: **https://ananke-documentation.netlify.app/**
- After cloning, the theme must be fetched: `git submodule update --init`. **Netlify must have submodule fetching enabled**, or `themes/ananke/` is empty at build time and the build fails.

## Overriding theme templates

- Files in the project's `layouts/` take precedence over the same path in `themes/ananke/layouts/`. Edit overrides here, never inside the submodule (changes there get lost on a theme bump).
- Ananke v2.19.0 uses the **new Hugo layout structure**: partials live in `layouts/_partials/` (underscore), defaults in `layouts/_defaults/`. Match that path when overriding.
- Active overrides:
  - `layouts/_partials/site-navigation.html` — header nav. Menu links are styled `f3 fw2` to match the "arsh.wtf" site title.
  - `layouts/_defaults/baseof.html`
  - `layouts/_markup/render-image.html` — image render hook that wraps every Markdown image in `<figure>` + `<figcaption>` so the alt text shows as a visible caption (the theme has no caption support otherwise).
- Note: `layouts/partials/page-header.html` is a **stale no-op** — it's an identical copy of the theme file under the old (pre-`_partials`) path. Don't rely on it.

## Post conventions

- Front matter: `title`, `date`, `image` + `featured_image` (thumbnail in the bundle), and `tags`.
- **Summary / preview** on the homepage and `/posts/` list comes from Hugo's `.Summary`. By default it auto-takes the first ~70 words, which can spill past the intro. Put a `<!--more-->` divider after the intro paragraph to control exactly where the preview ends (see `content/posts/italy-trip-2026/index.md`).
- **Image captions**: write images as standard Markdown `![caption text](image.jpeg)`. The `render-image.html` hook turns the alt text into a visible caption automatically — no shortcode needed.

## Navigation & listing

- The homepage (`themes/ananke/layouts/home.html`) only shows the few most recent posts + a short "more" title list — it is NOT a full archive.
- The full, paginated list of every post is the auto-generated `/posts/` section page (`pagerSize = 6` in `config.toml` — a multiple of the 3-per-row grid so rows line up evenly). Link to it via a main menu entry in `config.toml`:
  ```toml
  [[menu.main]]
  name = "All Posts"
  url = "/posts/"
  weight = 1
  ```
  The nav partial renders `.Site.Menus.main`.

## Spelling

- The author prefers **American spelling** (color, flavor, neighbor).
