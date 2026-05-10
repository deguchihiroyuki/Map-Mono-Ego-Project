# Repository Guidelines

## Project Structure & Module Organization
This repository is a static research project page derived from the Nerfies template.

- `index.html` contains the page content, layout, links, and media references.
- `static/css/` contains vendored Bulma-related styles plus the project-specific `index.css`.
- `static/js/` contains vendored UI scripts plus the project-specific `index.js`.
- `static/images/`, `static/videos/`, and `static/interpolation/stacked/` store visual assets used by the page.
- `README.md` documents the template origin and license.

Keep page-specific edits in `index.html`, `static/css/index.css`, and `static/js/index.js`. Avoid modifying minified vendor files unless replacing a library.

## Build, Test, and Development Commands
There is no package manager or build step. Serve the site locally as static files:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/` and verify the page renders with local relative paths.

Useful checks:

```sh
git status --short
rg "static/videos|static/images|static/interpolation" index.html
```

Use `git status --short` before committing, and `rg` to confirm referenced assets and links.

## Coding Style & Naming Conventions
Use two-space indentation in HTML, CSS, and JavaScript. Keep HTML structure readable with semantic `<section>` blocks and Bulma classes such as `hero`, `container`, `columns`, and `button`.

Name media assets with lowercase words and hyphens, for example `static/videos/dollyzoom-depth.mp4`. Interpolation frames use six-digit zero-padded JPG names such as `000000.jpg`; preserve that pattern because `static/js/index.js` loads frames programmatically.

Prefer relative asset paths beginning with `./static/...` for GitHub Pages and local servers.

## Testing Guidelines
Testing is manual. After changes, run the local server and check:

- The page loads without console errors.
- Videos autoplay or expose controls as intended, including `muted`, `loop`, and `playsinline` where needed.
- Carousel, navbar burger, and interpolation slider still work.
- New or replaced assets are reasonably sized for web delivery.

For JavaScript changes, test one desktop browser and one mobile-width viewport.

## Commit & Pull Request Guidelines
Recent commits use short imperative messages, for example `Fix videos and images.`, `Add icon.`, and `Add link to dataset.` Follow that style: concise, sentence case, and user-visible.

Pull requests should include a brief summary, screenshots or recordings for visual changes, notes about added or replaced media, and known browser concerns. Link related issues when available.

## Security & Configuration Tips
Do not commit private analytics IDs, unpublished dataset URLs, or large raw media. Keep third-party script and stylesheet URLs intentional, and prefer local vendored assets when reproducibility matters.
