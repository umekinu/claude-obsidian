---
type: meta
title: "Lint Report 2026-08-04"
created: 2026-08-04
updated: 2026-08-04
tags: [meta, lint]
status: developing
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[lint-report-2026-07-19]]"
---

# Lint Report: 2026-08-04

Navigation: [[index]] | [[hot]] | [[lint-report-2026-07-19]]

Transport: filesystem (per `.vault-meta/transport.json`). Triggered by user request to review vault hygiene ahead of a folder→tag workflow shift.

## Summary

- Pages scanned: 55 markdown files under `wiki/` (index.md currently claims 52 — stale, see Stale Index Entries)
- Dead wikilinks: 38 raw hits, of which ~10 are genuine broken references (rest are intentional syntax examples in prose, e.g. `` `[[Foo]]` `` used to illustrate link syntax, or links to non-`.md` assets like canvases that a markdown-only scan can't see)
- Orphan pages: 0 (excluding nav/meta pages) — cross-linking discipline is actually solid
- Frontmatter gaps: 20 pages missing `created` (mostly nav/meta pages, low severity); 1 page missing everything
- DragonScale address errors: 3 post-rollout pages missing required `address:`
- Stale index entry: page count mismatch
- Outside strict wiki-lint scope but found during the pass: 2 stale/prunable git worktrees and 2 stray local branches sitting inside the repo (~22MB), and one un-filed note at vault root

## Genuine Dead Links (BLOCKER/HIGH)

- `[[AI Marketing Hub Cover Images Canvas]]` — referenced in [[hot]], [[overview]], [[lint-report-2026-07-19]]. No matching `.canvas` file exists anywhere in `wiki/canvases/`. Carried over unresolved from the 2026-07-19 report.
- `[[E-commerce SEO]]` — referenced in [[Claude SEO]] and a meta session log. No matching page.
- `[[questions/_index]]` — referenced in [[gaps/_index]]. `wiki/questions/` has no `_index.md` (only one leaf page exists there); every other domain folder has one.
- `[[dashboard.base]]` — referenced in [[dashboard]] as a wikilink; the file exists at `wiki/meta/dashboard.base` but `.base` files aren't resolved by a markdown-link scan, so double-check this renders correctly in Obsidian.
- `[[mcp-setup]]` — referenced in [[transport-fallback]]. No matching page (only `skills/wiki/references/mcp-setup.md` exists, which is a skill doc, not a wiki page).
- `[[methodology-modes-guide]]`, `[[wiki-mode]]` — referenced in [[methodology-modes]]. Both point to skill docs (`docs/methodology-modes-guide.md`, `skills/wiki-mode/`), not wiki pages.
- `[[claude-obsidian-presentation]]` — referenced in [[overview]]. The canvas exists at `wiki/canvases/claude-obsidian-presentation.canvas` but the link isn't path-qualified, so it won't resolve in-vault as written.

**Carried over from 2026-07-19, still unresolved (already flagged "on hold" once):** `[[wiki-cli]]` / `[[wiki-fold]]` in [[log]] — intentional per that report's note ("skills have no vault page"); consider converting to markdown links as [[log]] itself says was already done elsewhere, or formally close this out.

## Ambiguous Wikilinks (MEDIUM)

- `[[_index]]` (bare, unqualified) in [[lint-report-2026-07-19]] — five files share the name `_index.md` (concepts, entities, gaps, papers, sources). Per this skill's own naming rule, unqualified wikilinks only resolve reliably when filenames are unique vault-wide. Everywhere else in the vault this is correctly written path-qualified (e.g. `[[concepts/_index]]`); this is the one holdout.

## DragonScale Address Errors (HIGH — per skill's own severity rule, these are hard errors)

Post-rollout pages (created ≥ 2026-04-23) missing required `address:`:
- [[Persistent Wiki Artifact]] (`wiki/concepts/Persistent Wiki Artifact.md`, created 2026-04-24)
- [[Query-Time Retrieval]] (`wiki/concepts/Query-Time Retrieval.md`, created 2026-04-24)
- [[Source-First Synthesis]] (`wiki/concepts/Source-First Synthesis.md`, created 2026-04-24)

No format errors, no collisions. Counter peek = 3, consistent with observed addresses (no drift).

Legacy pages pending backfill (informational, expected, not an error): 25 pages created before 2026-04-23 without an address — see `.vault-meta/legacy-pages.txt` policy.

3 pages have neither `address` nor `created`: [[methodology-modes]], [[preferences]], [[tagging-taxonomy]], [[transport-fallback]] — can't even classify these as legacy vs. post-rollout without a `created` date.

## Frontmatter Gaps (LOW unless noted)

20/55 pages missing `created`. Most are single-instance nav/meta pages (`index`, `hot`, `log`, `overview`, `getting-started`, `dashboard`, the four `_index.md` folder notes) where this is arguably by design. Two worth a closer look:
- `wiki/meta/tiling-report-2026-04-24.md` — missing type, status, created, updated, AND tags. Looks like a raw script-generated report that never got the frontmatter pass.
- `wiki/references/tagging-taxonomy.md` — missing `created`; also currently untracked in git (new/uncommitted).

## Stale Index Entries (MEDIUM)

`wiki/index.md` states "Total pages: 52" (last updated 2026-08-03); actual count is 55. At minimum `wiki/references/tagging-taxonomy.md` (untracked) isn't reflected yet.

## Semantic Tiling

Skipped — ollama not reachable in this environment (`tiling-check.py --peek` exit 10). Thresholds are uncalibrated (`calibrated: false`) regardless. Not actionable from this session; run locally where Obsidian/ollama are both up if duplicate-detection is wanted.

## Beyond wiki-lint scope: repo/vault housekeeping found during the pass

These aren't wiki-content issues but they're exactly the kind of thing that makes a vault feel "煩雑" (cluttered) over time, so noting them here:

- **Two prunable git worktrees inside the vault**: `.claude/worktrees/competent-shirley-373cca` and `.claude/worktrees/relaxed-noyce-ebc08e`, ~11MB each, both flagged `prunable` by `git worktree list`. Each is a full nested copy of `wiki/` (its own canvases, dashboard.base, etc.) — these are exactly the sort of stray, self-similar duplicate content a future semantic-tiling pass would flag as noise, except it's a whole nested vault copy rather than a single page.
- **Two local branches with no worktree**: `claude/festive-gates-349eaa`, `claude/goofy-gould-fef19e` — check whether these are merged/stale before deleting.
- **Uncommitted changes**: several tracked files modified (`hot.md`, `index.md`, templates, `.obsidian/*.json`) plus untracked `.claude/`, `2026.08.04.md`, `wiki/references/tagging-taxonomy.md`.
- **Un-filed root note**: `2026.08.04.md` at the vault root (outside `wiki/`) — content is a one-line policy note about switching from folder-based to tag-based Obsidian management. Not part of the wiki structure at all.

## Not run this pass

- Stale-claims check (needs source-diffing judgment, not scripted this round)
- Missing-pages check (concepts mentioned repeatedly but lacking their own page) — no strong candidates surfaced in a first pass, worth a dedicated look if the tag-migration touches concept boundaries
