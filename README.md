# about-me — GitHub Pages site

This repository contains the source for a simple personal website hosted with GitHub Pages. Below are concise instructions and boilerplate snippets (Jekyll-compatible) to get a clean layout and deploy quickly.

## Quick setup

- Put your site files at the repository root (or in `docs/`) and enable GitHub Pages from the repository `Settings → Pages` choosing the branch and folder where your site lives.
- If this repository is a user or organization site named `username.github.io`, publish from the repository root on `main` and GitHub will serve it automatically.

## Recommended structure

```
/_config.yml        # site config (already present)
/_layouts/
	default.html      # main HTML layout (see snippet)
/_includes/
	header.html
	footer.html
/assets/css/style.css
/index.md           # home page (uses layout)
```

## Minimal Jekyll layout (create `_layouts/default.html`)

```html
<!doctype html>
<html lang="en">
	<head>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width,initial-scale=1" />
		<title>{{ page.title | default: site.title }}</title>
		<link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
	</head>
	<body>
		<header>
			<h1><a href="{{ '/' | relative_url }}">{{ site.title }}</a></h1>
		</header>
		<main>
			{{ content }}
		</main>
		<footer>
			<p>&copy; {{ site.time | date: '%Y' }} {{ site.author | default: '' }}</p>
		</footer>
	</body>
</html>
```

## Example home page (`index.md`)

```md
---
layout: default
title: Home
---

Welcome to my personal site. Update this file with your bio, links, and projects.
```

## Minimal CSS (`assets/css/style.css`)

```css
body { font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; margin: 0; padding: 0; color: #222; }
header { background: #0b74de; color: white; padding: 1rem; }
header a { color: white; text-decoration: none; }
main { padding: 1.25rem; max-width: 900px; margin: 0 auto; }
footer { text-align: center; padding: 1rem; color: #666; font-size: .9rem; }
```

## Local preview

If you want to preview locally with Jekyll (recommended for Liquid templating):

1. Install Ruby and Bundler (platform-specific).
2. Add a `Gemfile` with `gem "jekyll"` (and optionally `gem "github-pages"`).
3. Run:

```bash
bundle install
bundle exec jekyll serve
```

Open `http://127.0.0.1:4000` to preview.

### Generating `Gemfile.lock`

Run `bundle install` in this repository to produce a `Gemfile.lock` tailored to your environment. Example:

```bash
gem install bundler
bundle install
```

If you want to explicitly lock platforms (useful in CI), run:

```bash
bundle lock --add-platform ruby
```

This will create `Gemfile.lock`. Commit that file if you want reproducible installs across machines.

## Deploying to GitHub Pages

- Push your changes to the branch configured in `Settings → Pages` (commonly `main` or `gh-pages`).
- For a repository named `username.github.io` the site is served at `https://username.github.io/`.
- For project pages, the site URL is `https://username.github.io/repo-name/` (set `baseurl` in `_config.yml` if needed).

## Next steps / customization

- Add an `_includes` folder for reusable parts like navigation.
- Add social links, projects, and an about page.
- Consider using a theme (e.g., `minima`) via `_config.yml` or customizing the layout above.

If you'd like, I can create the `_layouts/default.html`, `index.md`, and `assets/css/style.css` files directly in this repo — tell me which files to add and any preferred colors or text.