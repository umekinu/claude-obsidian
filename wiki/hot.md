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
- ~~Bug found: `scripts/wiki-lock.sh:156` calls `flock`, which doesn't exist on macOS~~ — **resolved** in `c0254a9` ("fix(locks): portable flock for macOS in wiki-lock.sh + allocate-address.sh"): uses the `flock` CLI where available, else a `python3 fcntl.flock` fallback. Shipped the same day as this cache entry was written; the note below was simply never updated.
- [[index]] rebuilt (counts + new References/Folds/Meta catalog sections); [[log]] backfilled with 9 release entries reconstructed from commit history.

## Active Threads

- ~~wiki-lock macOS fix pending in its worktree~~ — done, see above.
- Methodology mode unset (`.vault-meta/mode.json` absent → `generic` fallback). Deliberate default; `bash bin/setup-mode.sh` to change.
- Lint LOW items on hold: 6 cross-vault refs in session notes + `[[AI Marketing Hub Cover Images Canvas]]` in [[overview]].
- `main` is 4 commits ahead of `origin/main` (unpushed): `6647754`, `370a0d1`, `8bc7884`, `c0254a9`.
- WIP in the working tree (2026-08-03, uncommitted at time of writing): paper-ingest support for 落合フォーマット — `scripts/wiki-mode.py` routes a new `paper` page type to `wiki/papers/`, `skills/wiki-ingest/SKILL.md` extended, `wiki/papers/_index.md` and `wiki/gaps/_index.md` added, plus a draft `_proposals/ochiai-summary-SKILL.md`. Also present: local Claudian plugin install (`.claudian/`, `.obsidian/plugins/realclaudian/`) for testing the Obsidian-native Claude Code integration.
- New this session: `wiki/meta/mistakes.md` and `wiki/meta/preferences.md` added as an external-memory pair (AI mistake log + discovered user preferences), per the "Claude × Obsidian 連携ルール" pattern from a YouTube walkthrough. Read/write rules documented in `CLAUDE.md`.
