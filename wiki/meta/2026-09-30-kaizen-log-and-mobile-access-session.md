---
type: session
title: "Kaizen Log & Mobile Vault Access"
created: 2026-09-30
updated: 2026-09-30
tags:
  - meta
  - session
  - kaizen
  - external-memory
status: developing
related:
  - "[[claude-kaizen]]"
  - "[[preferences]]"
  - "[[2026-09-01-memory-and-correction-rules-session]]"
  - "[[index]]"
  - "[[hot]]"
---

# Kaizen Log & Mobile Vault Access

Navigation: [[index]] | [[hot]] | [[claude-kaizen]] | [[preferences]]

## Problem: the vault is local-only

The vault (`/Users/kinu/claude-obsidian`) was intended as the home for md/csv files, but it lives only on the Mac. The specific pain point is that **Claude on mobile cannot read the vault** (not Dr. Tai's own mobile viewing).

Options compared:

| Option | Pros | Cons |
|---|---|---|
| A. Use Cowork / Claude Code remotely from the Claude mobile app | Runs on the Mac, reads the vault in place; no migration; existing skills and rules keep working | Mac must be on and online; separate entry point from normal chat |
| B. Move the vault to Google Drive | Readable from any chat via the connected Drive connector, even with the Mac off | Migration work (links, `.obsidian` settings, sync conflicts); search and bulk operations weaker than local |

Direction: try A first (zero migration risk). Move to B, or mirror only frequently read files such as `hot.md` / `index.md` to Drive, if the Mac being off turns out to be a frequent problem. Not yet executed.

## Decision: `mistakes.md` renamed to `claude-kaizen.md`

Goal: record improvement points in the vault so that later sessions answer better automatically.

The vault already had this mechanism: `CLAUDE.md` § External Memory makes every session read `wiki/meta/mistakes.md` and [[preferences]]. Three options were weighed (rename `mistakes.md`; add a separate `claude-kaizen.md`; add it and freeze `mistakes.md`). Chosen: **rename**, so there is one place to read and write.

- `wiki/meta/mistakes.md` → `wiki/meta/claude-kaizen.md`, with aliases `mistakes` and `Mistakes Log` so old `[[mistakes]]` links still resolve. Historical notes were left unedited.
- References updated in `CLAUDE.md`, [[preferences]], and [[index]].

## Decision: Improvement entries added

[[claude-kaizen]] now holds two entry types:

- **Correction** — `NG Action` / `Correct Action` / `Trigger`. Something Dr. Tai had to correct.
- **Improvement** — `Current` / `Better` / `Trigger`. Not wrong, but could be done better next time.

Recording conditions: (1) Dr. Tai gave a correction or suggested an improvement, or Claude noticed one, proposed it, and Dr. Tai approved recording it (self-noticed items are never recorded without approval); (2) likely to recur; (3) statable as a concrete rule. Financial/health/personnel-evaluation content is summarized and confirmed before writing. Pure style preferences stay in [[preferences]]. Entries dated before 2026-09-30 carry no type label and count as Corrections.

First new entry (Correction, 2026-09-30): Claude proposed a new feedback file without first checking `CLAUDE.md` and `wiki/meta/`, where the mechanism already existed. Rule: check existing mechanisms before proposing new ones.

## Git

- Commit `88c26f8`: the 2026-09-01 memory/auto-logging work (previously uncommitted) and today's rename + Improvement entries, committed together as one external-memory-rules theme. `.obsidian/`, `_proposals/ochiai-summary-SKILL.md`, and `00_Resources/` were deliberately left out as unrelated.
- Git recorded the rename as delete + create (the file content changed too much for rename detection). Pre-rename history is at `git log -- wiki/meta/mistakes.md`.
- `main` is ahead of `origin/main`; not yet pushed.
- This session note was written via the filesystem transport from claude.ai chat, without `wiki-lock` (scripts cannot run from that surface).

## Related
- [[claude-kaizen]]
- [[preferences]]
- [[2026-09-01-memory-and-correction-rules-session]]
