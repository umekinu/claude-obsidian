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
