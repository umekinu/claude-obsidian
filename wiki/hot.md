---
type: meta
title: "Hot Cache"
updated: 2026-09-30T00:00:00
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
  - "[[tagging-taxonomy]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated

2026-08-04. This vault is now a **personal fork**, not a live mirror of upstream — see below before assuming version facts from before this date still hold.

## Key Recent Facts

- **This is `umekinu/claude-obsidian`, a fork of `AgriciDaniel/claude-obsidian`** (Daniel Agrici's public OSS project — confirmed via README, CODEOWNERS, CITATION.cff, and git author history; not something this user maintains upstream). Remote `origin` → the fork, `upstream` → Daniel Agrici's original.
- This fork's `main` is pinned at a **customized v1.9.2-era snapshot plus 7 local commits** (external-memory pair, paper-ingest/落合フォーマット feature, tiling-check.py Py3.9 fix). It does **not** track upstream's v2.0.0/v2.1.0 line.
- Upstream (`AgriciDaniel/claude-obsidian`) has since shipped **v2.0.0 and v2.1.0**: a major restructure into a `claude_obsidian/` Python package, an audited release manifest (`RELEASE_MANIFEST.json` + `SHA256SUMS`), native Windows support, and — importantly — it **no longer ships demo `wiki/` content or `CLAUDE.md` in the repo root** (moved to `examples/sample-vault/` and `templates/vault/`). A `git merge upstream/main` was attempted once, produced ~20 conflicts (mostly modify/delete on exactly the files this fork customizes), and was deliberately abandoned rather than reconciled.
- Plugin metadata still says v1.9.2 in this fork's own files (CITATION.cff etc.) — that's accurate for *this fork's* lineage, just stale relative to upstream.

## Recent Changes (2026-09-30)

- `wiki/meta/mistakes.md` renamed to [[claude-kaizen]] (aliases `mistakes` / `Mistakes Log` keep old links working). It now holds two entry types: **Correction** and **Improvement** (`Current` / `Better` / `Trigger`). Claude-noticed improvements are recorded only after Dr. Tai approves. Read at session start alongside [[preferences]], per `CLAUDE.md`.
- New kaizen rule (Correction): check `CLAUDE.md` and the relevant folder for an existing mechanism before proposing a new file/rule/workflow.
- Open thread: mobile Claude cannot read this vault. Plan is to try remote Cowork / Claude Code from the mobile app first; Google Drive migration (or a partial mirror of `hot.md` / `index.md`) is the fallback. Not yet executed.
- Commit `88c26f8` bundled the previously uncommitted 2026-09-01 memory-rules work with today's rename. `main` is ahead of `origin` and not yet pushed.
- See [[2026-09-30-kaizen-log-and-mobile-access-session]].

## Recent Changes (2026-09-01)

- New correction-formatting rule logged in [[preferences]]: when Claude revises Dr. Tai's text, show the full revised Markdown, bold only changed/added parts, list deletions briefly at the end only if needed, and flag anything needing confirmation separately under "要確認".
- Clarified scope of Dr. Tai's account-level "don't save/learn from this conversation" instruction: it applies to Claude's own personal-memory system (`mcp__memory__`), not to this vault — vault writes/saves from conversations remain welcome. Recorded in Claude's personal memory and in [[2026-09-01-memory-and-correction-rules-session]].
- New `Auto-Session-Logging (2026-09-01+)` rule added to `CLAUDE.md`: every session touching this vault now auto-files a full session note at session end, bypassing `/save`'s usual Skip-curation filter. `skills/save/SKILL.md` itself left unmodified; the override lives in `CLAUDE.md`.
- Finalized the "don't save/learn" account instruction wording (2026-09-01, see [[preferences]]): scope is Claude's own `mcp__memory__` only; Vault/file saves are exempt (a standing setup like Auto-Session-Logging counts as "explicit request"); before saving financial/health/personnel-evaluation-type sensitive content anywhere, Claude must summarize and confirm with Dr. Tai first. Dr. Tai still needs to paste this into the account's custom-instruction settings — Claude cannot edit that setting directly.
- See [[2026-09-01-memory-and-correction-rules-session]] for the full session record.

## Recent Changes (2026-08-04)

- Vault organization decision: **folders → tags**. New taxonomy documented in [[tagging-taxonomy]]: `gtd` (inbox/pending/waiting/reading/maybe/action/done/reference, single-select), `kind` (fact/insight/question/idea/wish/others, single-select), `lens` (art/science/design/engineering/bz/com, multi-select). Migration mechanics for existing folder-based notes not yet decided.

## Recent Changes (2026-08-03)

- `wiki/meta/mistakes.md` + `wiki/meta/preferences.md` added (external-memory pair). Read/write rules in `CLAUDE.md`. See [[log]] for the full session entry.
- Paper-ingest (落合フォーマット) WIP committed (`7155eac`); `tiling-check.py` Py3.9 fix recovered from a worktree and applied (`25b8a38`).
- Forked to `umekinu/claude-obsidian` (`origin`); original renamed to `upstream`. 7 commits pushed to the fork.

## Recent Changes (2026-07-19)

- Fixed 7 dead wikilinks (`6647754`): stray `?` stripped from 5 refs to [[How does the LLM Wiki pattern work]]; `wiki-cli`/`wiki-fold` skill refs converted to markdown links. Report: [[lint-report-2026-07-19]]. 7 LOW refs (cross-vault + missing canvas) on hold for individual review.
- `scripts/boundary-score.py`: Python 3.9 compat fix (`X | None` → `Optional[X]`, `8bc7884`).
- `.vault-meta/transport.json` written for the first time — preferred transport `filesystem` (Obsidian CLI absent on this Mac).
- ~~Bug found: `scripts/wiki-lock.sh:156` calls `flock`, which doesn't exist on macOS~~ — **resolved** in `c0254a9` ("fix(locks): portable flock for macOS in wiki-lock.sh + allocate-address.sh"): uses the `flock` CLI where available, else a `python3 fcntl.flock` fallback. Shipped the same day as this cache entry was written; the note below was simply never updated.
- [[index]] rebuilt (counts + new References/Folds/Meta catalog sections); [[log]] backfilled with 9 release entries reconstructed from commit history.

## Active Threads

- Methodology mode unset (`.vault-meta/mode.json` absent → `generic` fallback). Deliberate default; `bash bin/setup-mode.sh` to change.
- Lint LOW items on hold: 6 cross-vault refs in session notes + `[[AI Marketing Hub Cover Images Canvas]]` in [[overview]].
- Local Claudian plugin install present (`.claudian/`, `.obsidian/plugins/realclaudian/`) for testing the Obsidian-native Claude Code integration — gitignored, personal-environment only, not part of the fork's tracked tree.
- Open decision, not yet made: whether/how to selectively pull any of upstream's v2.0.0/v2.1.0 work (native Windows support, security-audit hardening) into this fork later. Deliberately deferred, not forgotten — see [[log]] 2026-08-03 entry for why the straight merge was abandoned.
- `origin` = `umekinu/claude-obsidian` (this fork), `upstream` = `AgriciDaniel/claude-obsidian` (Daniel Agrici's original, now 29+ commits ahead on its own v2.x line — histories have diverged, not simply ahead/behind).
