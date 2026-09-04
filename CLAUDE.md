# CLAUDE.md

## Site Purpose

A build journal. Notes on the learning, decision, and analytics tools I build: what I shipped, the forks in the road, what broke, what it produced, and what it opens up next.

The audience is future me. Kept public so the work is reusable, not just describable.

Governing belief: the most important future question is "What have you built?" Each post is a partial answer, with evidence of results, skills, effort, and compounding advantage. Understated and specific beats impressive and vague.

## Content Rules

Two goals, in order:

1. **Crystallize thinking.** If the decision, tradeoff, and result can't be explained clearly, the build isn't finished.
2. **Leave breadcrumbs.** Future me should be able to recover what was built, why that way, what broke, what to reuse, and what to build next.

**Uniqueness test.** Content belongs only if it's something that happened on this specific build, a judgment only someone who did the build could make, or a reusable artifact it produced. If a passage could appear unchanged in someone else's post on the same tool, cut it or link the canonical source. Setup steps, feature overviews, and tool definitions fail by default.

**Voice.**
- First person, plain, short sentences. Numbers over adjectives. No hype, no throat-clearing.
- No em dashes. Use a period, comma, colon, or parentheses.
- Failures at the same depth as wins. Length follows content.
- Never invent numbers, quotes, or adoption. Leave `[TODO: ...]` where the detail is missing.

## Guardrail

If a content request drifts from this — not anchored to a real build, no first-hand experience behind it, or generic advice anyone could write — reject it or redirect back to the site purpose.

## Tech Stack

- Quarto website project, output dir `docs/`, deployed to GitHub Pages via GitHub Actions
- Single `posts/` directory for all content, images stored alongside the `.qmd` that uses them
- No categories, no status taxonomy, no tags
- Each post has a `date` in front matter (`"2026-09-01"`). Only month and year are ever displayed; the day is arbitrary and exists to order the list.
- Landing page lists posts newest first, showing month/year above the title

## Layout & Styling

- All visual styling lives in `styles.css` — single source of truth
- `_includes/header.html` renders the single-line site header (`Build Journal | Learning, Decision, Analytics Tools`). It is wired into `index.qmd` only, via `include-before-body` in that file's front matter. Post pages deliberately have no site header, so the post title leads.
- `_includes/post-footer.html` gives post pages a back-link to the landing page, wired via `include-after-body` in `posts/_metadata.yml`. It is injected after `</main>`, outside `#quarto-content`, so it carries its own gutters.
- Default Quarto navbar and TOC are hidden via CSS
- Responsive breakpoints at 768px and 420px — verify both desktop and mobile when making layout changes

## Adding Content

1. Copy `_templates/post.qmd` into `posts/`
2. Rename in kebab-case
3. Set `date` to the month of the build, drop `draft: true` when ready
4. Write
5. Push to main — GitHub Actions builds and deploys automatically

## Local Preview

After making changes (content, styling, or config), run `quarto preview` to verify locally before pushing. Do not rely on production to test changes.

## Verifying Prod After Deploy

GitHub Actions typically deploys in ~40s. After a styling change, browser cache can mask the new CSS — hard-refresh (Cmd+Shift+R) or use an incognito window before concluding something is broken. If the deployed HTML and `styles.css` on the server look correct but the page renders old styles, it's cache, not the build.
