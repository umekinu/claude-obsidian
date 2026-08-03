---
type: meta
title: "Gaps Index"
updated: 2026-07-19
tags:
  - meta
  - index
  - gap
domain: research
status: evergreen
related:
  - "[[index]]"
  - "[[papers/_index]]"
  - "[[questions/_index]]"
---

# Gaps Index

Navigation: [[index]] | [[papers/_index|Papers]] | [[questions/_index|Questions]]

Future ingest candidates — papers named under 「6. 次に読むべき論文」 that are **not yet in the vault**. Populated automatically by the Academic Paper Ingest flow in `skills/wiki-ingest/SKILL.md`.

A gap is not a question. Questions ([[questions/_index]]) are things the vault does not know; gaps are specific documents the vault has not yet read.

---

## Format

One entry per candidate:

```markdown
- **[Author Year]** "Title" — Journal, vol(no), pages.
  - Cited by: [[Source Paper Page]]
  - Why: one line on what this would resolve
  - Status: pending | acquired | ingested | rejected
```

Mark `ingested` and move the wikilink to [[papers/_index]] once the paper is in the vault. Keep `rejected` entries with a one-line reason — knowing what was deliberately skipped is worth as much as the queue itself.

---

## Queue

<!-- Add ingest candidates here -->
