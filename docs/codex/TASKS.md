# Codex Tasks

## Pending
- Push the checkpointed commits so another device can continue from `main`.
- Fix article video embed visual sizing in the next theme pass:
  - player width should align with article content edges
  - mobile must not introduce horizontal scrolling
- On the next device, validate clean state before any new edits:
  - `blog-theme` on `main`
  - `blog-theme` clean after pull
  - `cloudflare-blog-worker` clean
- Regenerate `docs/codex/preview/` locally only when visual review is needed; do not add it to commits by default.
- When previewing backstage/admin-driven options on a new device, use the sibling Worker render contract or staging output; do not treat static sample preview HTML as enough to validate menu/category/link/profile integration.
- Use the cross-project assessment to choose the next shared theme/backend development slice.

## In Progress
- Checkpoint packaging and cross-device handoff for the updated `blog-theme` front-end pass.
- Cross-project planning with the sibling `cloudflare-blog-worker` repo.

## Done
- Created Codex continuity files.
- Documented the front-end baseline in `docs/codex/BASELINE.md`.
- Completed the first safe template cleanup for `index.html` and `article.html`.
- Generated local preview pages with sample data for visual review.
- Added a homepage footer newsletter band that reuses the existing `/subscribe` behavior.
- Polished the homepage and article newsletter UI with stronger spacing, helper copy, and feedback reset on input.
- Polished the homepage hero, article cards, and footer hierarchy for a stronger editorial landing-page feel.
- Polished the article page hero, reading surface, sidebar cards, and previous/next navigation for stronger long-form readability.
- Tightened homepage mobile spacing across nav, hero, story cards, pagination, and footer/newsletter sections.
- Tightened article-page mobile spacing across hero, reading layout, sidebar cards, and previous/next navigation.
- Aligned repeated editorial typography tokens across both templates:
  - eyebrow labels
  - metadata rows
  - newsletter support copy
  - footer rhythm and navigation treatment
- Completed a front-end QA pass for this slice, including:
  - mobile-safe wrapping for long site titles
  - keeping long nav labels scrollable on small screens
  - a safe CSS unicode escape for the blockquote opening quote
- Added backend-linkage template safeguards:
  - homepage profile avatar fallback when `profile.avatar` is empty
  - article related-card fallback when a related article has no `img`
  - no new Mustache field names or public route changes
- Locked the handoff policy for device switching:
  - repo-local `docs/codex/*` plus sibling `codex-continuity-index`
  - preview HTML stays local and is rebuilt on demand
- Documented the backstage-linked preview expectation for future devices:
  - admin-saved menu/category/link/profile data must be checked through the Worker render contract or staging output
  - local sample preview data should include custom menu/footer/category values plus empty-avatar and no-related-image cases
- Added article-page theme support for externally embedded videos:
  - responsive `.video-embed` styling for YouTube/Bilibili iframe content produced by the Worker
  - no new Mustache fields or public route changes
- Widened desktop article video embeds as a first attempt while preserving mobile `100%` width, but manual QA still reports that sizing needs another pass.
