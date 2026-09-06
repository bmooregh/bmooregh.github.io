# Build Journal

Learning, Decision, Analytics Tools.

Notes on the learning, decision, and analytics tools I build: what I shipped, the forks in the road, what broke, and what it opened up. The audience is future me. Kept public so the work is reusable, not just describable.

Built with Quarto, deployed to GitHub Pages.

## Live Site

[bmooregh.github.io](https://bmooregh.github.io)

## Structure

- `index.qmd` — the landing page, listing every post by month/year, newest first
- `posts/` — one `.qmd` per journal entry, plus its images
- `_includes/header.html` — the site header, rendered on the landing page only
- `styles.css` — all visual styling, single source of truth
- `_templates/post.qmd` — starting point for a new entry

## Adding a New Post

1. Copy `_templates/post.qmd` into `posts/`
2. Rename it in kebab-case: `what-i-built.qmd`
3. Set `date:` to the month of the build (`"2026-09-01"`). Day is ignored, it just orders the list.
4. Put any images next to the `.qmd` in `posts/` and reference them by filename
5. Remove `draft: true`
6. Run `quarto preview` to check it locally
7. Push to `main` — GitHub Actions builds and deploys automatically
