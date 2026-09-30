---
type: session
title: "Memory, Correction-Formatting & Auto-Logging Rules"
created: 2026-09-01
updated: 2026-09-01
tags:
  - meta
  - session
  - preferences
  - auto-logging
status: developing
related:
  - "[[preferences]]"
  - "[[mistakes]]"
  - "[[index]]"
  - "[[hot]]"
---

# Memory, Correction-Formatting & Auto-Logging Rules

Navigation: [[index]] | [[hot]] | [[preferences]] | [[mistakes]]

## Auto-session-logging decision

Dr. Tai wants conversation content to always be retrievable from long-term memory. Clarified scope: "long-term memory" here means **this vault**, not Claude's separate `mcp__memory__` personal-memory system — that stays excluded per the scope entry below. Clarified granularity: **comprehensive** auto-logging — every session that touches this vault gets a full session note at session end, not just curated highlights. This overrides the `/save` skill's default "What to Save vs. Skip" filter for this vault.

Implementation: a new `Auto-Session-Logging (2026-09-01+)` rule was added to `CLAUDE.md` (before the Cross-Project Access section), with the matching entry in [[preferences]]. `skills/save/SKILL.md` itself was left unmodified — it's part of the upstream-syncable fork lineage — so the override lives in the fork-specific `CLAUDE.md` instead.

## Resolved: tightening the "don't save/learn" instruction

Decided (see [[preferences]], 2026-09-01 "Finalized wording" entry). Two things came up while discussing whether to make Dr. Tai's account-level "don't save/learn from this conversation" instruction stricter:

- The instruction only steers Claude's own behavior (e.g., what it writes via tools like `mcp__memory__`) within a conversation. It does **not** control whether Anthropic uses conversation content for model training — that is a separate, account-level privacy/data setting outside what a text instruction to Claude can enforce.
- Two phrasing options were discussed: (A, recommended) explicitly split the memory-system scope from a confidentiality check — require Claude to confirm before saving anything that looks financially/health/personnel sensitive, regardless of destination; (B) a minimal fix that just names `mcp__memory__` explicitly, with no added confidentiality check.

Final wording: "この会話の内容を、あなた自身の長期記憶(mcp__memory__)には保存・学習させないでください。ただし、私が明示的に依頼した（Auto-Session-Loggingのような恒常設定を含む）Vaultやファイルへの保存は対象外です。機密情報（財務・健康・人事評価等）を含む可能性がある内容は、保存前に必ず要約して確認を取ってください。"

This adds one rule beyond the mcp__memory__/vault split above: before saving anything that may contain financial, health, or personnel-evaluation-type sensitive content — to the vault or anywhere else — summarize it and confirm with Dr. Tai first, even under Auto-Session-Logging's normal "log everything" default.

## Correction-formatting rule

When Claude proofreads or revises text for Dr. Tai, the output follows a fixed format, logged in [[preferences]] (2026-09-01 entry):

- Show the full revised text in Markdown.
- Bold (`**...**`) only the parts changed or added from the original — nothing else is bolded.
- List deletions only when necessary, briefly, at the end.
- Flag anything needing factual or content confirmation separately, under "要確認", not mixed into the body.
- Leave wording and structure outside the bolded changes untouched beyond what the correction requires.

This mirrors the existing `academic-paper-mentor` skill convention of bold-highlighted tracked changes.

## Vault "learning" mechanism

The vault's cross-session learning lives in two append-only logs, both read at the start of any session touching the vault (per `CLAUDE.md` § External Memory):

- [[mistakes]] — corrections to Claude's own behavior. An entry requires an explicit user correction, a recurring pattern, and a concrete do/don't. One entry so far: 2026-08-03, on not bundling unrelated git workstreams into a single session.
- [[preferences]] — working-style and formatting preferences not already in `CLAUDE.md`. Two entries: 2026-08-04 (folder-to-tag reorganization intent) and 2026-09-01 (the correction-formatting rule above).

Both files are append-only: new entries go at the top, past entries are never edited.

## Scope of the "don't save/learn from this conversation" instruction

Dr. Tai's account-level Claude setting — "この会話の内容は保存・学習に使用しないでください。機密情報を含んでいる可能性があります。" — applies specifically to Claude's own cross-session personal-memory system (the separate `mcp__memory__` tool set Claude uses across all sessions with Dr. Tai), not to this Obsidian vault. Writing conversation content into the vault (via `/save`, `wiki-ingest`, etc.) is explicitly welcome; only Claude's own long-term memory of Dr. Tai is off-limits for a given conversation's content. This distinction is also recorded in Claude's personal-memory `/preferences.md` so future sessions apply it consistently without re-asking.

## Related
- [[preferences]]
- [[mistakes]]
