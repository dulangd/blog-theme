# Codex Tasks

## Pending
- Push the checkpointed commits so another device can continue from `main`.
- On the next device, validate clean state before any new edits:
  - `blog-theme` on `main`
  - `blog-theme` clean after pull
  - `cloudflare-blog-worker` clean
- Continue from the next front-end slice:
  - mobile spacing and hierarchy tuning
  - cross-page typography consistency
  - final QA pass
- Regenerate `docs/codex/preview/` locally only when visual review is needed; do not add it to commits by default.

## In Progress
- Checkpoint packaging and cross-device handoff for `blog-theme`.

## Done
- Created Codex continuity files.
- Documented the front-end baseline in `docs/codex/BASELINE.md`.
- Completed the first safe template cleanup for `index.html` and `article.html`.
- Generated local preview pages with sample data for visual review.
- Added a homepage footer newsletter band that reuses the existing `/subscribe` behavior.
- Polished the homepage and article newsletter UI with stronger spacing, helper copy, and feedback reset on input.
- Polished the homepage hero, article cards, and footer hierarchy for a stronger editorial landing-page feel.
- Polished the article page hero, reading surface, sidebar cards, and previous/next navigation for stronger long-form readability.
- Locked the handoff policy for device switching:
  - repo-local `docs/codex/*` plus sibling `codex-continuity-index`
  - preview HTML stays local and is rebuilt on demand
