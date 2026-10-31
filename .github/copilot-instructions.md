# Copilot Instructions

This repository is a Zola static-site project. Follow the existing structure and configuration when creating or changing the site.

## Project Structure

- `zola.toml` — site-wide configuration. Keep settings here; do not introduce a second config file.
- `content/` — Markdown pages and sections. Use `_index.md` for section metadata and `index.md` for standalone pages.
- `templates/` — Tera templates for page layouts and reusable components. Extend or include existing templates rather than duplicating markup.
- `sass/` — Sass stylesheets. Zola compiles these because `compile_sass` is enabled.
- `static/` — assets copied to the site output without processing.
- `themes/` — local themes, if the project adopts one. Do not assume a theme is installed.

## Creating Site Content

- Write content as Markdown in `content/`, using TOML front matter delimited by `+++`.
- Add only the front-matter fields needed for the page, such as `title`, `date`, `description`, and `draft`.
- Put section-level metadata and section templates in `_index.md`; use a page's `path` only when a custom URL is needed.
- Use Zola's Tera template syntax in `templates/`. Follow the existing template inheritance and keep page-specific markup in the appropriate template.
- Put images, fonts, and other unprocessed files in `static/`. Reference them by their site-relative URL.
- Keep styles in `sass/` and use the existing Sass organization where possible.

## Configuration and Validation

- Preserve the configured `base_url`, Sass compilation, search index, and syntax-highlighting theme in `zola.toml` unless the task specifically changes them.
- Before running Zola, check whether it is available with `zola --version` or `command -v zola`. If it is installed but not on `PATH`, use the executable's full path. On Apple Silicon Macs with Homebrew, a common location is `/opt/homebrew/bin/zola`.
- Run `zola check` to check the site's content and links, and `zola build` to verify the production build. If Zola is not available, report that rather than claiming validation passed.
- Use `zola serve` to preview changes locally; the default address is `http://127.0.0.1:1111`. If the default port is unavailable, try another port, for example `zola serve --port 1112`, then verify the preview responds before reporting its address.
- Resolve build or check errors rather than hiding them.
- Do not commit generated output such as `public/` or local Sass caches.
