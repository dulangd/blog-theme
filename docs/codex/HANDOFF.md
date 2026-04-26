# Codex Handoff

## Current Goal
Keep the updated `blog-theme` checkpoint stable while the next cross-project planning pass evaluates the public templates together with the sibling `cloudflare-blog-worker` admin/backend implementation.

## Current State
- Baseline documented in `docs/codex/BASELINE.md`.
- The template checkpoint itself only changed `blog-theme`.
- Since that checkpoint, the sibling `cloudflare-blog-worker` repo has entered an admin safe-convergence pass and a combined project assessment.
- Cross-project follow-on planning now uses:
  - this repo as the public-surface baseline
  - `cloudflare-blog-worker/docs/codex/CROSS_PROJECT_ASSESSMENT.md` as the shared roadmap
- `index.html` completed a first-pass cleanup:
  - fixed pagination markup
  - added skip-link, navigation labels, safer external links, and resource hints
  - added a homepage footer newsletter band that reuses the existing `/subscribe` flow
  - second-pass polish added stronger CTA hierarchy, helper copy, and cleaner mobile form spacing
  - third-pass polish strengthened the homepage hero, article card rhythm, and footer hierarchy for a more editorial landing-page feel
  - fourth-pass polish tightened mobile spacing, aligned shared label/meta/footer/newsletter typography tokens with the article page, and kept long mobile nav labels horizontally scrollable
  - backend linkage pass added a no-avatar fallback to avoid broken profile image placeholders when profile avatar is empty
  - preserved all existing Mustache data keys and feature blocks
- `article.html` completed a first-pass cleanup:
  - fixed previous/next navigation markup
  - converted newsletter area into a semantic form flow
  - added resource hints, highlight.js defer loading, and stronger image/link semantics
  - second-pass polish aligned newsletter input sizing and feedback-clearing behavior with the homepage band
  - third-pass polish introduced a calmer hero shell, a dedicated reading frame, card-based sidebar modules, and clearer previous/next navigation cards for better long-form readability
  - fourth-pass polish tightened mobile hero/sidebar spacing, aligned repeated editorial tokens with the homepage, added mobile-safe wrapping for long site titles, and fixed the blockquote quote mark to use a safe CSS escape
  - backend linkage pass added a related-article image fallback to avoid empty `<img src="">` placeholders when related articles have no cover image
- `docs/codex/preview/` is currently absent on this device:
  - missing preview HTML is normal
  - regenerate it locally only when a visual review pass is needed
  - do not include regenerated preview files in commits

## Last Session
Completed the next front-end slice across both public templates:
- homepage: tightened mobile spacing across nav, hero, story grid, pagination, and footer/newsletter modules
- article page: tightened mobile spacing across hero, reading layout, sidebar cards, and previous/next navigation
- shared chrome: aligned eyebrow labels, metadata rows, newsletter supporting copy, footer rhythm, and link treatment between pages
- QA fixes: allowed long site titles to wrap on small screens while keeping menu labels scrollable, and changed the blockquote quote mark to a CSS unicode escape

## Submission Scope
- Intended code/template checkpoint:
  - `index.html`
  - `article.html`
- Intended continuity checkpoint:
  - `docs/codex/HANDOFF.md`
- Do not commit:
  - `docs/codex/preview/`
  - any file under `cloudflare-blog-worker`

## Device Switch Resume
- Cross-device continuity uses two layers together:
  - repo-local source of truth: `blog-theme/docs/codex/*`
  - workspace-level entrypoint: sibling `codex-continuity-index`
- On the next device, resume in this order:
  1. open the workspace root `blog-workspace`
  2. sync `blog-theme` on `main`
  3. sync `cloudflare-blog-worker` only as a reference repo
  4. confirm sibling `codex-continuity-index` exists
  5. start the session with the existing continuity script
     - if the device has no saved local path yet, choose this device's preferred repo path before any clone/pull continues
  6. read `README.md`, then `blog-theme/docs/codex/BASELINE.md`, `HANDOFF.md`, `TASKS.md`, `DECISIONS.md`
  7. only read `cloudflare-blog-worker/docs/codex/HANDOFF.md` if template/rendering contract details are needed
- First validation step after resume:
  - `blog-theme` should be on `main`
  - `blog-theme` should be clean after pulling the checkpoint commits
  - `cloudflare-blog-worker` should be clean
  - missing `docs/codex/preview/` is normal because preview HTML is rebuilt locally on demand
- Default next development slice if goals stay unchanged:
  - submit and push the updated checkpoint
  - only then decide whether any later pass should focus on content-specific polish or broader accessibility refinements
- Suggested continuation prompt:
  - `继续 blog-theme 当前 checkpoint，不新增后端改动；先核对 docs/codex 中的 handoff 和模板 diff，再决定是直接提交 checkpoint，还是再做一轮更细的前端 polish。`

## Local Preview Rebuild
- Preview HTML is intentionally treated as local-only output.
- If visual review is needed on the next device:
  1. use the current `blog-theme` templates
  2. reuse the Mustache rendering contract from `cloudflare-blog-worker/src/worker.js`
  3. regenerate `docs/codex/preview/index.preview.html` and `article.preview.html` with sample data
  4. inspect the generated files locally
- Do not submit regenerated preview HTML unless the workflow policy changes later.

## Backstage-Linked Preview Notes
- The latest front-end templates include safeguards needed when the admin/backend configuration changes public-page data:
  - homepage profile avatar fallback when `profile.avatar` is empty
  - article related-card fallback when a related article has no cover image
  - mobile-safe shared nav/footer/newsletter typography that still accepts Worker-provided menu/category/footer data
- For a next-device preview that needs to reflect backstage/admin options, do not rely only on static hand-written HTML samples.
- Preferred preview flow:
  1. sync both sibling repos: `blog-theme` and `cloudflare-blog-worker`
  2. read `cloudflare-blog-worker/docs/codex/HANDOFF.md` and `STAGING_VALIDATION.md`
  3. use the Worker render contract or staging Worker output to generate/review public pages
  4. verify admin-saved menu/category/link/profile data appears on homepage and article page
- `cloudflare-blog-worker` currently owns the active config normalization and staging validation:
  - menu/category/link/profile/social values are normalized before reaching Mustache
  - local and staging validation check that saved menu/category/link values render on public pages
  - staging validation preserves and restores user-managed KV values so preview checks do not overwrite manual admin config
- If another device cannot run staging immediately, rebuild `docs/codex/preview/` with sample data that includes:
  - custom menu items
  - categories and footer links
  - empty profile avatar
  - related articles with and without images
  - newsletter states

## Next Actions
1. Submit the checkpoint in two commits:
   - template checkpoint
   - handoff checkpoint
2. Push the checkpoint so another device can pull from `main`.
3. Use the cross-project assessment before starting the next shared theme/backend phase:
   - `..\cloudflare-blog-worker\docs\codex\CROSS_PROJECT_ASSESSMENT.md`
4. On the next device, resume from the `Device Switch Resume` flow above before any new edits.

## Constraints
Do not commit secrets, tokens, Codex internal session files, or local caches.

## Useful Commands
- Start continuity session from the workspace root:
  - `powershell.exe -NoProfile -ExecutionPolicy Bypass -File ..\codex-continuity-index\scripts\codex-start-session.ps1 -Name blog-theme`
- Check repo state:
  - `git -C .\blog-theme status --short`
  - `git -C .\blog-theme branch --show-current`
  - `git -C .\cloudflare-blog-worker status --short`
- Review the cross-project roadmap:
  - `Get-Content ..\cloudflare-blog-worker\docs\codex\CROSS_PROJECT_ASSESSMENT.md`
- Preview files remain local-only:
  - open `docs/codex/preview/index.preview.html` or `article.preview.html` manually if visual review is needed
