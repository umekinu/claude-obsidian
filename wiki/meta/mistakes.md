---
type: meta
title: "Mistakes Log"
updated: 2026-08-03
tags:
  - meta
  - mistakes
status: evergreen
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[log]]"
  - "[[preferences]]"
---

# Mistakes Log

Navigation: [[index]] | [[hot]] | [[log]] | [[preferences]]

Append-only. New entries go at the TOP. Never edit past entries.

## Purpose

A record of corrections the user had to make explicitly, so the same mistake
isn't repeated in a later session. This is not a place for routine bugs (those
go in [[log]]) — only for patterns in *Claude's own behavior* that needed
correcting.

## When to add an entry

Add an entry only when **all three** conditions hold:

1. The user gave an explicit correction (not something Claude noticed on its own).
2. The pattern is likely to recur (not a one-off fluke).
3. It can be stated as a concrete do/don't.

## Entry format

```
## YYYY-MM-DD: [one-line description of the mistake]
**NG Action**: what actually happened
**Correct Action**: what should happen next time
**Trigger**: the situation this rule applies to
```

## Reading this file

At the start of a session touching this vault, read this file (it's short by
design) alongside [[preferences]] before doing any work.

---

<!-- Newest entries go directly below this line. -->

## 2026-08-03: Bundled too many unrelated changes into one working session
**NG Action**: Landed several independent workstreams back-to-back in one continuous session (external-memory files, a pre-existing uncommitted feature, a recovered bugfix, a fork, and a full upstream-merge attempt) instead of finishing and verifying one before starting the next. This compounded into git complications (merge conflicts, a push sent to the wrong remote, a botched merge abort) that took much longer to unwind than the original tasks.
**Correct Action**: When multiple independent changes are pending in the same vault/repo, sequence them — commit, verify, and confirm each one is clean before starting the next — rather than batching unrelated workstreams together.
**Trigger**: Any session where more than one independent change (feature work, doc update, git housekeeping, remote/repo changes) is pending at the same time.
