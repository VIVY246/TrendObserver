# AGENTS.md

## Project overview

このリポジトリは、流行把握用データをローカルで整理し、AIが分析しやすい形式で出力する無料自作ツールです。

初期MVPは Python CLI です。最初の対象は TikTok Creative Center などで人が確認し、手動CSV化した TikTok トレンドデータの取り込みです。

Steam / YouTube / Reddit などの自動取得や adapter 実装は初期MVPでは行いません。

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

- 実装前に docs/requirements.md、docs/architecture.md、docs/data-schema.md を確認する。
- データ取得元ごとの差異は importer / adapter 層に閉じ込める。
- AI分析用の共通スキーマを壊さない。
- `raw` と `source_specific` を保持する。
- CSVやSQLiteなどの実データを不用意にコミットしない。
- 初期MVPでは Python / SQLite / CSV / JSONL / Markdown / YAML の構成を前提にする。
- TypeScript構成や package.json は、明示的な方針変更があるまで作らない。
- 新しい取得元を追加する場合は source-catalog.md と data-schema.md を更新する。
- 仕様変更が大きい場合は docs/adr/ に意思決定を残す。
