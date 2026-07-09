# Trend Observer

## 目的

Trend Observer は、SNS や公開サービスで確認した流行把握用データをローカルで整理し、AI が分析しやすい JSONL と Markdown に変換する自作用ツールです。

初期段階では公開 Web サービスや SaaS ではなく、手元で動かす Python CLI として開発します。

## 初期 MVP

最初に作るものは、TikTok Creative Center などで確認したトレンド情報を手動で CSV 化し、その CSV を取り込むローカル CLI です。

- Python で実装する
- SQLite に正規化済みデータを保存する
- TikTok の完全自動取得やスクレイピングは行わない
- ジャンル設定は YAML で管理する
- TikTok CSV を共通フォーマットへ正規化する
- ジャンル別に AI 分析用 JSONL を出力する
- AI 分析結果 JSONL を取り込む
- AI 分析結果をもとに Markdown 週次レポートを生成する

## 将来拡張

初期 MVP のあと、必要に応じて以下を検討します。

- YouTube API などを使った動画トレンド取得
- Steam の公開ページや API を使ったゲームトレンド取得
- Google Trends や GitHub などの追加ソース
- Reddit など海外コミュニティ由来のトレンド取得
- Web UI、スケジューラー、ダッシュボード

## 想定コマンド

まだ本格実装前のため、以下は予定しているコマンド例です。

```bash
python main.py import --source tiktok --file data/raw/tiktok/tiktok_2026-07-08.csv
python main.py build-ai-input --sources tiktok --genres game work --week 2026-W28
python main.py import-ai-results --file outputs/ai_results/2026-W28.jsonl
python main.py report --genres game work --week 2026-W28
```

## 構成

- `config/genres.yml`: ジャンル定義
- `config/sources.yml`: データソース定義
- `data/raw/`: 手動で置いた元 CSV
- `data/processed/`: SQLite などの処理済みデータ
- `outputs/ai_input/`: AI 分析用 JSONL
- `outputs/ai_results/`: AI 分析結果 JSONL
- `outputs/reports/`: Markdown レポート
- `src/`: Python 実装

## 主要ドキュメント

- `docs/requirements.md`
- `docs/roadmap.md`
- `docs/architecture.md`
- `docs/data-schema.md`
- `docs/source-catalog.md`
- `docs/genre-taxonomy.md`
- `docs/output-format.md`
- `docs/cli-usage.md`
- `docs/ai-analysis-guide.md`
- `docs/testing.md`
- `docs/compliance-and-rate-limits.md`
