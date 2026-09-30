---
type: meta
title: "Wiki Index"
updated: 2026-09-30
tags:
  - meta
  - index
status: evergreen
related:
  - "[[overview]]"
  - "[[log]]"
  - "[[hot]]"
  - "[[dashboard]]"
  - "[[Wiki Map]]"
  - "[[concepts/_index]]"
  - "[[entities/_index]]"
  - "[[sources/_index]]"
  - "[[papers/_index]]"
  - "[[gaps/_index]]"
  - "[[LLM Wiki Pattern]]"
  - "[[Hot Cache]]"
  - "[[Compounding Knowledge]]"
  - "[[Andrej Karpathy]]"
---

# Wiki Index

Last updated: 2026-09-30 | Total pages: 58 | Sources ingested: 2

Navigation: [[overview]] | [[log]] | [[hot]] | [[dashboard]] | [[Wiki Map]] | [[getting-started]]

---

## Concepts

- [[LLM Wiki Pattern]] — the pattern for building persistent, compounding knowledge bases using LLMs (status: mature)
- [[Hot Cache]] — ~500-word session context file, updated after every ingest and session (status: mature)
- [[Compounding Knowledge]] — why wiki knowledge grows more valuable over time, unlike RAG (status: mature)
- [[cherry-picks]] — prioritized feature backlog from ecosystem research; 13 features to add to claude-obsidian (status: current)
- [[SVG Diagram Style Guide]] — canonical visual style for all diagrams: Space Grotesk, #0A0A0A dark theme, #E07850 accent, full design tokens (status: evergreen)
- [[Pro Hub Challenge]] — community challenge pattern for building claude-seo/claude-blog extensions; first challenge produced 6 submissions, 5 integrated in v1.9.0 (status: evergreen)
- [[Semantic Topic Clustering]] — SERP-based keyword grouping replacing paid tools; hub-spoke architecture with interactive visualization (status: evergreen)
- [[Search Experience Optimization]] — "read SERPs backwards" methodology for page-type mismatch detection and persona scoring (status: evergreen)
- [[SEO Drift Monitoring]] — "git for SEO" baseline/diff/track with 17 comparison rules and SQLite persistence (status: evergreen)
- [[DragonScale Memory]] — memory-layer spec inspired by the Heighway dragon curve; fold operator, deterministic page addresses, semantic tiling, boundary-first autoresearch (status: shipped v0.4, all four mechanisms opt-in)
- [[Persistent Wiki Artifact]]: durable Markdown page as the LLM's memory object, distinct from ephemeral chat turns (status: developing)
- [[Source-First Synthesis]]: provenance discipline; raw sources stay immutable while the wiki layer is synthesized and cited (status: developing)
- [[Query-Time Retrieval]]: wiki query path synthesizes with citations; complementary to Obsidian's in-vault search (status: developing)

---

## Entities

- [[Andrej Karpathy]] — AI researcher, creator of the LLM Wiki pattern, former Tesla AI director (status: developing)
- [[Ar9av-obsidian-wiki]] — multi-agent compatible LLM Wiki plugin; delta tracking manifest (status: current)
- [[Nexus-claudesidian-mcp]] — native Obsidian plugin + MCP bridge; workspace memory, task management (status: current)
- [[ballred-obsidian-claude-pkm]] — goal cascade PKM; auto-commit hooks, /adopt command (status: current)
- [[rvk7895-llm-knowledge-bases]] — 3-depth query system, Marp slides, parallel deep research (status: current)
- [[kepano-obsidian-skills]] — official skills from Obsidian creator; defuddle, obsidian-bases (status: current)
- [[Claudian-YishenTu]] — native Obsidian plugin embedding Claude Code; plan mode, @mention (status: current)
- [[Claude SEO]] — Tier 4 Claude Code skill for SEO analysis; 23 skills, 17 agents, 30 scripts at v1.9.0 (status: evergreen)

---

## Sources

- [[claude-obsidian-ecosystem-research]] — 2026-04-08 | web research across 16+ repos | 8 wiki pages created

---

## Papers

Academic papers summarised in 落合フォーマット. See [[papers/_index|Papers Index]].

<!-- Add paper pages here -->

---

## Gaps

Future ingest candidates surfaced by 「6. 次に読むべき論文」. See [[gaps/_index|Gaps Index]].

<!-- Add gap entries here -->

---

## Questions

- [[How does the LLM Wiki pattern work]] — how the pattern works and why it outperforms RAG at human scale (status: developing)

---

## Comparisons

- [[Wiki vs RAG]] — when to use a wiki knowledge base versus RAG; verdict: wiki wins at <1000 pages
- [[claude-obsidian-ecosystem]] — feature matrix of 16+ Claude+Obsidian projects; where claude-obsidian wins and gaps

---

## Decisions

- [[2026-04-14-community-cta-rollout]] - Skool community CTA footer added to 6 skill repos with per-tool frequency rules (status: active)
- [[2026-04-15-slides-and-release-session]] - Claude SEO v1.9.0 slides (15-slide HTML deck) + GitHub release v1.9.0 with PDF asset (status: complete)
- [[2026-04-15-release-report-session]] - Claude SEO v1.9.0 Release Report PDF: dark theme, 13 pages, WeasyPrint layout fixes, Challenge v2 added (status: complete)
- [[2026-04-14-claude-seo-v190-session]] - Claude SEO v1.9.0 Pro Hub Challenge integration: 5 submissions, 4 new skills, 4 review rounds, cybersecurity audit (status: complete)

---

## References

- [[transport-fallback]] — transport fallback decision tree (CLI → MCP → filesystem); consulted by mutating skills (status: evergreen)
- [[methodology-modes]] — short decision tree for LYT / PARA / Zettelkasten / Generic vault modes (status: evergreen)
- [[tagging-taxonomy]] — gtd/kind/lens tag axes replacing folder-based organization; single-select gtd/kind, multi-select lens (status: evergreen)

---

## Folds

- [[fold-k3-from-2026-04-23-to-2026-04-24-n8]] — first real DragonScale fold; 8 children spanning 2026-04-23 → 04-24 (status: complete)

---

## Meta & Reports

- [[2026-09-30-git-housekeeping-session]] — session record: hot.md review (stale lines fixed), leftover uncommitted changes committed by theme (Obsidian property types, role-split SOP draft, plugin enables)
- [[2026-09-30-kaizen-log-and-mobile-access-session]] — session record: mobile Claude vault access (remote Cowork vs. Google Drive), mistakes → claude-kaizen rename, Improvement-type entries
- [[2026-09-01-memory-and-correction-rules-session]] — session record: correction-formatting bold rule, vault learning-mechanism review, scope of the "don't save/learn" instruction (Claude memory vs. vault), and the auto-session-logging decision (full-session auto-save to vault; "don't save/learn" wording still open)
- [[claude-kaizen]] — append-only log of corrected Claude behavior patterns / improvement points (renamed from `mistakes` on 2026-09-30); read alongside [[preferences]] at session start (status: evergreen)
- [[preferences]] — append-only log of working-style preferences discovered during sessions, distinct from the static profile in `CLAUDE.md` (status: evergreen)
- [[dashboard]] — Dataview dashboard: recent activity, seed pages, open questions
- [[lint-report-2026-07-19]] — 2026-07-19 lint: 14 dead refs → 7 fixed, 6 orphans triaged, 15 frontmatter gaps
- [[tiling-report-2026-04-24]] — first real semantic-tiling run (0 errors, 15 review pairs)
- [[retrieval-benchmark-v1.7]] — 50-query benchmark corpus behind the v1.7 retrieval gate
- [[boundary-frontier-2026-04-24]] — first real boundary-first autoresearch frontier run
- [[2026-04-24-v1.6.0-release-session]] — v1.6.0 closeout session record
- [[2026-04-10-backlink-empire-session]] — backlink-empire session note (cross-vault refs on hold per 2026-07-19 lint)
- [[claude-obsidian-v1.2.0-release-session]] — v1.2.0 release session record
- [[claude-obsidian-v1.4-release-session]] — v1.4 release session record
- [[full-audit-and-system-setup-session]] — full audit + system setup session record

---

## Domains

<!-- Add domain entries here after scaffold -->
