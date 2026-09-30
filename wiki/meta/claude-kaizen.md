---
type: meta
title: "Claude Kaizen Log"
aliases:
  - mistakes
  - Mistakes Log
updated: 2026-09-30
tags:
  - meta
  - mistakes
  - kaizen
status: evergreen
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[log]]"
  - "[[preferences]]"
---

# Claude Kaizen Log

(Renamed from `mistakes.md` on 2026-09-30. The `mistakes` alias keeps old `[[mistakes]]` links resolving.)

Navigation: [[index]] | [[hot]] | [[log]] | [[preferences]]

Append-only. New entries go at the TOP. Never edit past entries.

## Purpose

A record of how Claude's answers and ways of working should improve, so later
sessions get better automatically. Two kinds of entry live here:

- **Correction** — something Claude did that the user had to correct.
- **Improvement** — something that wasn't wrong, but could be done better next
  time (a better approach, order, level of detail, etc.).

This is not a place for routine bugs (those go in [[log]]) — only for patterns
in *Claude's own behavior*. Pure style/format preferences go in [[preferences]].

## When to add an entry

Add an entry when **all three** conditions hold:

1. **Source** — either (a) the user gave an explicit correction or suggested
   an improvement, or (b) Claude noticed an improvement on its own, proposed it
   to the user, and the user approved recording it. Never record a
   self-noticed item without that approval.
2. The pattern is likely to recur (not a one-off fluke).
3. It can be stated as a concrete do/don't or "next time, do X".

If an item may contain financial, health, or personnel-evaluation content,
summarize it and confirm with the user before writing (see [[preferences]],
2026-09-01).

## Entry format

Correction:

```
## YYYY-MM-DD: [Correction] [one-line description]
**NG Action**: what actually happened
**Correct Action**: what should happen next time
**Trigger**: the situation this rule applies to
```

Improvement:

```
## YYYY-MM-DD: [Improvement] [one-line description]
**Current**: how it was done
**Better**: what to do next time, and why
**Trigger**: the situation this rule applies to
```

Entries before 2026-09-30 have no type label; treat them as Corrections.

## Reading this file

At the start of a session touching this vault, read this file (it's short by
design) alongside [[preferences]] before doing any work.

---

<!-- Newest entries go directly below this line. -->

## 2026-09-30: [Improvement] Present pending decisions as a numbered table with a recommendation per row
**Current**: After listing several options in prose, Claude asked "どの方針にするか教えていただければ…" — Dr. Tai couldn't tell what was actually being asked ("どの方針とは").
**Better**: When asking Dr. Tai to decide, lay out each decision as a numbered row in a table (`# | 決めること | おすすめ`), with one concrete recommendation per row, and say that "おすすめで" is a valid answer. This makes the question explicit and lets Dr. Tai approve everything in one reply.
**Trigger**: Any time Claude needs the user to choose between options or approve a multi-part plan.

## 2026-09-30: [Improvement] Check for uncommitted changes before editing the vault
**Current**: Edited `CLAUDE.md`, `wiki/index.md`, and `preferences.md` first, and only discovered at commit time that the 2026-09-01 work in those same files was still uncommitted — forcing a decision on how to split or bundle the changes after the fact.
**Better**: Before editing, check `git status` (or ask Dr. Tai to run it when Claude cannot run git from the current surface, e.g. claude.ai chat). If uncommitted changes exist, agree on how to handle them first (commit them separately, or bundle them by theme) so the new work never gets tangled with old work.
**Trigger**: Start of any session that will modify files in this vault.

## 2026-09-30: [Correction] Proposed a new mechanism without checking the vault's existing one
**NG Action**: Asked how to record improvement points so answers improve automatically, Claude proposed creating a new feedback file plus a `CLAUDE.md` reference — without first reading `CLAUDE.md` or `wiki/meta/`, where the `mistakes.md` / `preferences.md` external-memory pair already served exactly that purpose. Only discovered the overlap when about to implement.
**Correct Action**: Before proposing any new file, rule, or workflow for this vault, read `CLAUDE.md` and list the relevant folder (e.g. `wiki/meta/`) to check whether an existing mechanism already covers it; then propose extending that mechanism rather than adding a parallel one.
**Trigger**: Any request to set up a new logging, memory, rule, or organization mechanism in the vault or its Claude configuration.

## 2026-08-03: Bundled too many unrelated changes into one working session
**NG Action**: Landed several independent workstreams back-to-back in one continuous session (external-memory files, a pre-existing uncommitted feature, a recovered bugfix, a fork, and a full upstream-merge attempt) instead of finishing and verifying one before starting the next. This compounded into git complications (merge conflicts, a push sent to the wrong remote, a botched merge abort) that took much longer to unwind than the original tasks.
**Correct Action**: When multiple independent changes are pending in the same vault/repo, sequence them — commit, verify, and confirm each one is clean before starting the next — rather than batching unrelated workstreams together.
**Trigger**: Any session where more than one independent change (feature work, doc update, git housekeeping, remote/repo changes) is pending at the same time.
