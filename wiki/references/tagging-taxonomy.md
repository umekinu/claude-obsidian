---
type: reference
title: "Tagging Taxonomy — gtd / kind / lens"
updated: 2026-08-04
tags:
  - reference
  - taxonomy
  - tagging
gtd: reference
kind: fact
lens:
  - art
  - science
  - design
  - engineering
  - bz
  - com
status: evergreen
related:
  - "[[methodology-modes]]"
  - "[[index]]"
---

# Tagging Taxonomy — gtd / kind / lens

Navigation: [[index]] | [[methodology-modes]]

## Decision

This vault moves from folder-based organization to **tag-based organization**
(decided 2026-08-04). Every note carries up to three tag axes instead of
living in exactly one folder path.

## The three axes

| 大項目 | 中項目 | 説明 | 選択 |
|---|---|---|---|
| `gtd` | `inbox` | とりあえずなんでも入れる。アクションが必要かの判定前 | 単一 |
| | `pending` | 自分待ち（判断保留） | 単一 |
| | `waiting` | 他者待ち | 単一 |
| | `reading` | いつか読む | 単一 |
| | `maybe` | いつかやる（someday/maybe） | 単一 |
| | `action` | 次のアクションへ | 単一 |
| | `done` | 完了 | 単一 |
| | `reference` | アクション管理の対象外。資料として保存 | 単一 |
| `kind` | `fact` | インプット系。一次資料 | 単一 |
| | `insight` | インプット系。まだ言語化しきれていない気づき・直観 | 単一 |
| | `question` | アウトプット系 | 単一 |
| | `idea` | アウトプット系 | 単一 |
| | `wish` | アウトプット系 | 単一 |
| | `others` | その他整理できないもの | 単一 |
| `lens` | `art` | 表現軸 | 複数可 |
| | `science` | 表現軸 | 複数可 |
| | `design` | 表現軸。つくる | 複数可 |
| | `engineering` | 表現軸 | 複数可 |
| | `bz` | 実務軸。ビジネス戦略・プロジェクト | 複数可 |
| | `com` | 実務軸。つたえる | 複数可 |

## Selection rules

- **`gtd`** — single-select. It's a workflow status; a note can't be
  simultaneously `inbox` and `done`.
- **`kind`** — single-select. `fact`/`insight`/`question`/`idea`/`wish` are
  mutually exclusive by nature (a note claiming to be both `fact` and
  `insight` signals it hasn't been distilled yet — split it).
- **`lens`** — **multi-select**. Folders forced exclusivity; tags don't have
  to. A note can legitimately be `design`×`bz` (e.g. design-driven branding)
  or `design`×`com` (e.g. visual communication). Forcing single-select here
  would re-impose the folder limitation the migration is meant to remove.

## Design rationale

- `gtd` extends canonical GTD (inbox → clarify → organize → reflect →
  engage) with `waiting` (other-dependent, distinct from `pending`
  self-dependent) and keeps `reference` as GTD's own non-actionable filing
  branch — not a stage of progress, an exit from the action pipeline.
- `kind`'s fact/insight split follows 立花隆's method: collect one次資料 in
  volume before synthesizing, and keep pre-verbal insight (直観) instead of
  forcing it into a fully-formed idea prematurely.
- `lens`'s bz/com axis follows 佐藤可士和's practice: his work sits at the
  business-strategy/communication layer, not purely in the art-science-
  design-engineering expression axis. Without bz/com, his kind of
  cross-disciplinary note (design decisions justified by business logic)
  has nowhere to go.

## Open items

- `reading` vs `maybe` overlap not fully resolved — both are variants of
  someday/maybe. Working rule: `reading` = the read itself is the whole
  action; `maybe` = something else follows after.
- Migration mechanics (how existing folder-based notes get retagged) not
  yet decided.
