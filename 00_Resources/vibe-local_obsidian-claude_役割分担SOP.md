---
title: vibe-local / Obsidian-Claude 役割分担SOP
type: SOP
status: draft
created: 2026-08-06
---

# vibe-local / Obsidian-Claude 役割分担SOP

## 1. 判定基準（最初に確認する一問）

> **最終成果は「動くもの」か、「後から理解・再利用できる知識」か。**

- [ ] 動くもの（コード・処理結果・ログ） → **vibe-local**
- [ ] 知識・判断・文脈（ノート・SOP・意思決定） → **Obsidian-Claude**
- [ ] 両方必要 → Obsidian-Claudeで設計 → vibe-localで実行 → Obsidian-Claudeで確定

## 2. vibe-localに任せてよいか チェックリスト

- [ ] Python/PowerShell/バッチ等のコード作成・改修
- [ ] PDF ingest / chunk / curate 前処理の実装
- [ ] API・CLI操作、定型作業の自動化
- [ ] エラーログ解析、テスト作成・実行
- [ ] CSV・測定データの整形、統計処理コード化
- [ ] Vault裏方処理（重複候補抽出、未リンク一覧化、Frontmatter/タグ一括修正、ファイル名正規化、整合性チェック）

**vibe-localに置かないもの（該当したらObsidian-Claudeへ）**
- [ ] 研究上の最終判断
- [ ] 概念の定義
- [ ] 長期プロジェクト方針
- [ ] 文献レビューの完成版
- [ ] WITTW／WTTDの正式モデル
- [ ] 正本ノート（人が読んで理解するためのもの）

## 3. Obsidian-Claudeに任せてよいか チェックリスト

- [ ] 情報の入口整理（00_Inbox, 20_Sources等の運用）
- [ ] 文献の構造化要約（目的・方法・結果・限界）
- [ ] 複数論文の比較、既存ノートとのリンク
- [ ] WITTW/WTTD整理、パフォーマンスモデル構築
- [ ] IDT役割・情報フロー整理、評価指標定義
- [ ] 意思決定ログ・SOP・フレームワークへの昇格判断
- [ ] Vault整理での「統合するか」「正本はどれか」の判断

## 4. 両方を使うタスクの分担早見表

| タスク | vibe-local | Obsidian-Claude |
|---|---|---|
| 論文取り込み | PDFテキスト化・メタデータ抽出・チャンク分割・重複チェック・ファイル配置 | 内容妥当性確認・構造化要約・関連ノートリンク・テーマ統合・実践含意 |
| データ分析 | データクリーニング・コード作成・統計処理・グラフ生成・手順保存 | 分析目的明確化・結果解釈・現場的意味づけ・判断基準照合 |
| Vault整理 | 重複/リンク切れ検出・タグ一括修正・一覧/差分生成 | 統合判断・正本決定・概念関係の記述・MOC更新 |

## 5. 新規仕組み構築フロー（Implementation Brief方式）

1. [ ] Obsidian-Claudeで仕様を先に書く（目的／入力／出力／完了条件／制約／検証方法）
2. [ ] 仕様をvibe-localに渡して実装
3. [ ] vibe-localがImplementation Resultを返す（実施内容／変更ファイル／テスト結果／既知の問題／使用方法／次の改善候補）
4. [ ] Obsidian-Claudeで結果をプロジェクトノート・SOPに統合

## 6. 標準ワークフロー（全体像）

```
00_Inboxに課題投入
  → Obsidian-Claudeで目的・仕様・完了条件整理
  → 実装が必要ならvibe-localへ
  → vibe-localで作成・実行・テスト
  → 結果とログをObsidianへ戻す
  → Obsidian-Claudeで意味づけ・正本ノート更新
  → 再利用可能ならSOP／Frameworkに昇格
```

## 7. 安全確認（毎回チェック）

- [ ] 100件超の一括操作は、実行前に件数と失われる情報を提示して確認を取ったか
- [ ] gitワークツリー環境作業前に `pwd` と `.claude/skills/` の存在を確認したか
- [ ] hot.md / index.mdの日付が古くないか確認したか
