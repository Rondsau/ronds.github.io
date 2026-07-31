# Article Publishing Guide

## 1. Purpose

This guide defines the approved, repeatable process for adding new articles to ronds.au without changing its current static architecture. The site must continue to use static HTML, Tailwind CSS through the CDN, GitHub Pages, standalone HTML article pages, and manually maintained homepage and article archive entries.

Article publishing must not introduce Astro, Jekyll, Eleventy, Markdown page generation, a CMS, Node.js, npm, a package manager, a build system, or new dependencies.

## 2. Standard workflow

Follow this sequence for every article:

> Article drafted and approved in ChatGPT → publishing details finalised → ChatGPT creates a precise Codex implementation prompt → Codex inspects the current repository → Codex creates the article and updates its links → Codex runs checks → Codex creates a draft pull request → changed files are reviewed → pull request is marked ready → squash and merge → temporary branch is deleted → live GitHub Pages site is tested

Responsibilities are divided as follows:

- **ChatGPT:** writing, editing, product decisions, publishing details, the implementation prompt, and review support.
- **Codex:** repository inspection, HTML implementation, homepage and archive link updates, testing, and creation of the draft pull request.
- **GitHub:** change review and approval.
- **GitHub Pages:** live deployment.

Human review is required before a draft pull request is marked ready or merged.

## 3. Required publishing information

Every article publishing task should provide:

- Series or category
- Article number, where applicable
- Article title
- Italic tagline
- Publication date
- Filename
- Homepage description
- Archive description
- Meta description
- Complete approved article body

Use this reusable publishing packet:

```text
Series:
Article number:
Title:
Tagline:
Publication date:
Filename:
Homepage description:
Archive description:
Meta description:
Article body:
```

Resolve missing or ambiguous publishing information before implementation begins.

## 4. Filename conventions

Use the current naming convention:

`articles/series.###.html`

Examples:

- `articles/fulcrum.002.html`
- `articles/fulcrum.003.html`
- `articles/duit.001.html`

Rules:

- Use lowercase filenames.
- Use three-digit article numbers.
- Do not use spaces.
- Do not use brackets.
- Do not use inconsistent separators.
- Do not rename existing published article URLs unless explicitly approved.
- Treat existing published article URLs as permanent links.

## 5. Canonical article structure

`articles/fulcrum.001.html` is the current approved article-page reference.

Future articles should preserve its established:

- Header
- Navigation
- Article header
- Title treatment
- Italic tagline treatment
- Publication date placement
- Typography
- Colours
- Spacing
- Maximum reading width
- Section heading treatment
- Blockquote treatment
- Footer
- Favicon reference
- Mobile behaviour

Codex should inspect the current repository before every publishing task because the latest approved article page may contain improvements made after this guide was written. If a newer approved article page has superseded the reference, follow the latest approved implementation while preserving the established design.

Do not create a separate, unused HTML template file unless explicitly requested; it could drift away from the live article design.

## 6. Article creation rules

For each new article, Codex should:

1. Start from the latest `main` branch.
2. Create a separate branch.
3. Inspect the current homepage, article archive, and latest approved article page.
4. Create the new standalone HTML article.
5. Preserve the existing design system.
6. Replace all article-specific titles, descriptions, dates, and body content.
7. Use the article title as the main `<h1>`.
8. Place the tagline directly below the title in italics.
9. Use proper `<h2>` elements for main article sections.
10. Use the established article paragraph styling.
11. Use the established blockquote styling where required.
12. Preserve punctuation, apostrophes, em dashes, and wording from the approved article.
13. Do not rewrite article content unless the task explicitly requests editorial changes.
14. Keep the page readable and usable on mobile.
15. Avoid changing unrelated pages or application logic.

## 7. Homepage publishing rules

- Once at least three real articles exist, the homepage writing section should show the three most recently published articles.
- Show the newest articles first.
- Include each published article's date, title, and short description.
- Link every published entry to the correct article URL.
- A real article may replace a “Coming soon” placeholder.
- Keep unfinished articles non-clickable.
- Do not create working links for articles that have not been published.
- When a fourth real article is published, the oldest article should remain in the archive but may be removed from the homepage.

## 8. Article archive rules

- `articles/index.html` is the complete article archive.
- Add every published article to the archive.
- List articles newest first.
- Include each article's publication date, title, short description, and correct URL.
- Do not remove older published articles from the archive.
- Do not add unfinished articles as working links.
- Avoid duplicate archive entries.

## 9. Design rules

Preserve the current ronds.au identity:

- Warm ivory background
- Dark ink text
- Muted green
- Restrained burgundy
- Gold accents
- Space Grotesk headings
- Inter body copy
- IBM Plex Mono for small labels and navigation
- Calm typography
- Restrained motion
- Mobile usability
- Japanese-minimal, retro-light feel
- Premium but not corporate

Do not redesign the site during article publishing. Do not introduce flashy animation, dark-tech styling, unrelated visual changes, or new dependencies.

## 10. Safety rules

- Never delete or unintentionally modify `CNAME`.
- Never merge directly into `main`.
- Always review unexpected file changes.
- Do not alter Fulcrum financial calculations, `localStorage` behaviour, or application logic during an article publishing task.
- Do not rename existing published URLs without explicit approval.
- Do not expose draft or unfinished content.
- Keep each article publishing task narrowly scoped.
- Do not queue dependent implementation tasks before the earlier pull request has been reviewed.

## 11. Required checks

Before creating the pull request, Codex must confirm:

1. The new article exists at the intended path.
2. The browser title is correct.
3. The meta description is correct.
4. The title, tagline, and publication date are correct.
5. The publication date is consistent across the article, homepage, and archive.
6. The homepage link points to the correct article.
7. The archive link points to the correct article.
8. Internal links and fragment links are valid.
9. Unpublished placeholders remain non-clickable.
10. Mobile navigation remains intact.
11. Existing published article links still work.
12. `CNAME` is unchanged.
13. No unrelated files were modified.
14. `git diff --check` passes.

Checks should be performed against the current repository and reported accurately. Any limitation, assumption, or unexpected condition must be recorded in the pull request.

## 12. Pull request requirements

For each article publishing task:

- Create a draft pull request.
- Report every changed file.
- Summarise the published article.
- State the final article URL.
- List the checks performed.
- Identify any assumptions or unexpected repository conditions.
- Do not mark the pull request ready or merge it automatically.

After human review, the preferred merge method is:

`Squash and merge`

Delete the temporary branch after merging.

## 13. Post-merge live checks

After GitHub Pages deployment, verify:

- Homepage article link
- Article archive link
- Article page layout
- Desktop readability
- Mobile readability
- Navigation back to the homepage or archive
- Publication date
- Title and tagline
- No visible regressions
- GitHub Pages deployment completed successfully

If a live check fails, document the issue and address it through a separate, narrowly scoped pull request rather than making unreviewed changes directly on `main`.
