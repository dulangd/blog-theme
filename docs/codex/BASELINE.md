# Blog Theme Baseline

## Date
- 2026-04-24

## Scope
- Project: `blog-theme`
- Public templates:
  - `index.html`
  - `article.html`
- Runtime contract:
  - Templates are fetched remotely by `cloudflare-blog-worker`
  - Current rendering relies on Mustache-style placeholders such as `{{ siteName }}` and `{{ #articleList }}`

## Current Feature Baseline
- Home page:
  - Sticky top navigation
  - Author hero area
  - Article grid list
  - Pagination
  - Footer category and link areas
- Article page:
  - Hero section with title/meta/cover
  - Rich article content area
  - Previous/next navigation
  - Related article list
  - Newsletter subscription entry
  - Social links in sidebar and footer

## Constraints For Optimization
- Do not delete any existing public feature
- Do not change current Mustache data keys or section names
- Do not introduce a build step before the static-template baseline is stabilized
- Prefer progressive enhancement:
  - valid HTML
  - stronger semantics
  - safer external links
  - better resource hints
  - form interaction improvements without changing endpoints

## Baseline Risks Found
- `index.html` pagination contains malformed closing markup in the older-page link
- `article.html` previous/next block contains malformed closing markup in the older-article label
- External links opened in a new tab are missing `rel="noopener noreferrer"`
- Subscription UI is not a semantic form, so keyboard submit and feedback are weak
- Critical pages rely on multiple remote resources without connection hints
- Images and landmark navigation are missing part of the accessibility metadata

## First Optimization Pass
- Fix invalid HTML structure
- Add skip-link and landmark labels
- Improve image and link accessibility
- Standardize newsletter form submission behavior
- Add low-risk performance hints for remote fonts/CDNs
