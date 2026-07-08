# AGENTS.md

## Project overview

このリポジトリは、SNS・Steam等から流行把握用データを取得し、AIが分析しやすい形式で出力する無料自作ツールです。

## Important docs

- 要件確認: docs/requirements.md
- ロードマップ: docs/roadmap.md
- 全体設計: docs/architecture.md
- 出力形式: docs/data-schema.md, docs/output-format.md
- データ取得元: docs/source-catalog.md
- ジャンル分類: docs/genre-taxonomy.md
- CLI利用: docs/cli-usage.md
- AI分析ガイド: docs/ai-analysis-guide.md
- テスト方針: docs/testing.md
- 制約・規約: docs/compliance-and-rate-limits.md
- 意思決定記録: docs/adr/

## Development rules

- 実装前に該当docsを確認する。
- データ取得元ごとの差異はadapter層に閉じ込める。
- AI分析用の正規化スキーマを壊さない。
- 新しい取得元を追加する場合は source-catalog.md と data-schema.md を更新する。
- 仕様変更が大きい場合は docs/adr/ に意思決定を残す。
