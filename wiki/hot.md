---
type: meta
title: "Hot Cache"
updated: 2026-07-19T21:30:00
tags:
  - meta
  - hot-cache
status: evergreen
related:
  - "[[index]]"
  - "[[log]]"
  - "[[Wiki Map]]"
  - "[[getting-started]]"
  - "[[lint-report-2026-07-19]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated

2026-07-19. Maintenance session: first lint in ~3 months, dead-link repair, and this cache rebuilt from git history (`c2d7575..HEAD`, 38 commits) — the prior cache still claimed "v1.7.1 unpushed, awaiting go," which was two months stale.

## Key Recent Facts

- Plugin is at **v1.9.2, public canonical** since 2026-05-28 (`00213b7`): the public repo AgriciDaniel/claude-obsidian is the default install; AI Marketing Hub Pro repositioned as early access. Everything v1.7.1 → v1.9.2 is shipped and tagged.
- Release line since the last cache write: **v1.7.1** (egress-consent BLOCKER + 6 HIGH closed; verifier agent added) → **v1.7.2** (all MEDIUM/LOW closed; Unicode BM25 tokenizer; benchmark 54% top-1, +41% error reduction) → **v1.8.0** (methodology modes, skill #14) → **v1.8.1** (ship-gate closure; all 6 mode templates had failed YAML parse) → **v1.9.0** (10-principle `/think` framework, skill #15; repo hygiene + CI) → **v1.9.1** (audit hardening: stale-lock reaper, auto-commit opt-out, symlink canonicalization) → **v1.9.2** (prompt-cache hardening: 16 KB Haiku cache floor + telemetry; 9 test suites).
- Tag/CHANGELOG drift: CHANGELOG's "1.8.2" fixes landed inside the v1.9.0 commit `209aad9`; no v1.8.2 tag exists.

## Recent Changes (2026-07-19)

- Fixed 7 dead wikilinks (`6647754`): stray `?` stripped from 5 refs to [[How does the LLM Wiki pattern work]]; `wiki-cli`/`wiki-fold` skill refs converted to markdown links. Report: [[lint-report-2026-07-19]]. 7 LOW refs (cross-vault + missing canvas) on hold for individual review.
- `scripts/boundary-score.py`: Python 3.9 compat fix (`X | None` → `Optional[X]`, `8bc7884`).
- `.vault-meta/transport.json` written for the first time — preferred transport `filesystem` (Obsidian CLI absent on this Mac).
- **Bug found**: `scripts/wiki-lock.sh:156` calls `flock`, which doesn't exist on macOS — every `acquire` fails, silently disabling multi-writer safety. Fix in progress in a separate worktree session (`claude/festive-gates-349eaa`).
- [[index]] rebuilt (counts + new References/Folds/Meta catalog sections); [[log]] backfilled with 9 release entries reconstructed from commit history.

## Active Threads

- wiki-lock macOS fix pending in its worktree; merge when done.
- Methodology mode unset (`.vault-meta/mode.json` absent → `generic` fallback). Deliberate default; `bash bin/setup-mode.sh` to change.
- Lint LOW items on hold: 6 cross-vault refs in session notes + `[[AI Marketing Hub Cover Images Canvas]]` in [[overview]].
