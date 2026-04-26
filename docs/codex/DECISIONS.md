# Codex Decisions

Record durable decisions here. Do not include secrets.

- Optimize the existing static Mustache templates in place before considering any build tooling or framework migration.
- Do not remove or rename existing Mustache data keys/sections during UI optimization passes.
- Use a baseline-first workflow:
  1. document current state
  2. make a small reversible pass
  3. verify visually
  4. only then continue with stronger polish
- For local visual review, generate preview pages with sample data under `docs/codex/preview/` so the theme can be inspected without a live worker render.
- Keep homepage and article-page subscription behavior aligned through lightweight page-local scripts for now; do not introduce shared partials or a template refactor until the static-template UX is stable.
- Treat the homepage and article page as related but distinct editorial surfaces:
  - homepage optimizes for discovery and CTA hierarchy
  - article page optimizes for reading comfort and supportive sidebar structure
- Cross-device continuity defaults to a dual-track model:
  - `blog-theme/docs/codex/*` is the repo-local handoff source of truth
  - sibling `codex-continuity-index` is the workspace-level session entrypoint
- Preview HTML under `docs/codex/preview/` is a local rebuild artifact:
  - use it for visual review when needed
  - do not include it in checkpoint commits by default
- For this checkpoint, `cloudflare-blog-worker` stays unchanged and is treated as a reference-only repo for render-contract checks.
- Backstage-linked preview requires the Worker render contract or staging output, not static sample HTML alone:
  - admin-saved menu/category/link/profile data must be verified on public pages
  - sample preview data should cover custom menu/footer/category values, empty profile avatars, and related articles without images
  - durable normalization and staging validation rules live in the sibling `cloudflare-blog-worker/docs/codex/*` handoff files
