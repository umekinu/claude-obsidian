---
type: preference
title: "Preferences Log"
updated: 2026-09-01
tags:
  - meta
  - preferences
status: evergreen
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[claude-kaizen]]"
---

# Preferences Log

Navigation: [[index]] | [[hot]] | [[claude-kaizen]]

## Purpose

Working-style and formatting preferences discovered *during sessions* — not
the fixed profile facts already in `CLAUDE.md` (affiliation, response
language, citation format, etc.). Those stay in `CLAUDE.md` since they're
static. This file is for things noticed along the way that aren't written
down anywhere yet.

Append-only. New entries go at the TOP. Never edit past entries.

## When to add an entry

- The user states or demonstrates a preference not already covered in
  `CLAUDE.md` or here.
- It's specific enough to act on next time (not a vague impression).

## Entry format

```
## YYYY-MM-DD: [short label]
**Observation**: what was noticed
**Applies to**: the situation this preference applies to
```

---

<!-- Newest entries go directly below this line. -->


## 2026-09-01: Finalized wording for the "don't save/learn" account instruction
**Observation**: Dr. Tai finalized the account-level custom-instruction text governing what Claude may save/learn from conversations:

> この会話の内容を、あなた自身の長期記憶(mcp__memory__)には保存・学習させないでください。ただし、私が明示的に依頼した（Auto-Session-Loggingのような恒常設定を含む）Vaultやファイルへの保存は対象外です。機密情報（財務・健康・人事評価等）を含む可能性がある内容は、保存前に必ず要約して確認を取ってください。

This resolves the open question logged earlier the same day (see [[2026-09-01-memory-and-correction-rules-session]]). Key points: (1) scope is Claude's own `mcp__memory__` only; (2) Vault/file saves are exempt, and a standing setup like Auto-Session-Logging counts as "explicit request" — it doesn't need to be re-requested every session; (3) a new cross-cutting rule: before saving anything that may contain financial/health/personnel-evaluation-type sensitive content, anywhere, summarize it and confirm with Dr. Tai first — this applies on top of Auto-Session-Logging's normal no-skip behavior.
**Applies to**: All future saves to Claude's own memory and to this vault. The confirm-before-saving-sensitive-content rule takes precedence over Auto-Session-Logging's "log everything, don't filter" default whenever financial/health/personnel-evaluation content is involved.

## 2026-09-01: Always auto-log full sessions to the vault (Claude's own memory excluded)
**Observation**: User wants every conversation that touches this vault to always be retrievable from long-term memory — specifically the vault (not Claude's separate `mcp__memory__` personal-memory system, which stays excluded per the 2026-09-01 "don't save/learn" scope entry above). Confirmed this means comprehensive auto-logging of the full session at session end, not selective filing of only notable insights.
**Applies to**: Session end for any session touching this vault. Overrides the `/save` skill's default "What to Save vs. Skip" curation filter — see the new "Auto-Session-Logging" rule in `CLAUDE.md`.

## 2026-09-01: 文章修正時は修正箇所を太字で示す
**Observation**: ユーザーから、文章の校正・推敲を依頼する際の出力ルールが明示された。
- 修正後の全文をMarkdownで示す
- 原文から変更・追加した箇所のみを **太字** にする
- 削除した箇所は、必要な場合のみ末尾に簡潔に示す
- 内容上の確認が必要な点は、本文と分けて「要確認」として示す
- 太字以外の表現や構成は、必要以上に変えない
**Applies to**: ユーザーの文章（原稿・メール・申請書・論文ドラフト等）を校正・推敲・修正する全ての場面。

## 2026-08-04: Shifted from folder-based to tag-based organization
**Observation**: User noted a change in working policy — moving away from Obsidian folder-based organization toward tag-based organization, in the context of wanting the vault to stay tidy over time.
**Applies to**: How new content should be filed/organized going forward. Relevant to the vault's `methodology mode` setting (`.vault-meta/mode.json`, `bin/setup-mode.sh`) — no mode is currently set (generic default), which is folder-oriented (`wiki/sources/`, `entities/`, `concepts/`). A mode more aligned with tag-based, flatter organization (e.g. `zettelkasten`) has not yet been formally selected; this entry records the stated intent pending that decision.
