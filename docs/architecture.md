# Architecture

## 方針

- 初期 MVP は Python CLI として実装する。
- 最初の入力は TikTok の手動 CSV とする。
- TikTok CSV importer が CSV を読み込み、normalizer が共通フォーマットへ変換する。
- 正規化済みデータは SQLite に保存する。
- AI 分析用 JSONL と Markdown 週次レポートを出力する。
- source 固有の差異は importer と `source_specific` / `raw` に閉じ込める。

## 想定構成

```txt
trend-observer/
  README.md
  AGENTS.md
  config/
    genres.yml
    sources.yml
  data/
    raw/
      tiktok/
    processed/
  outputs/
    ai_input/
    ai_results/
    reports/
  src/
    importers/
      tiktok_csv.py
    core/
      models.py
      normalize.py
      genre.py
    storage/
      sqlite.py
    builders/
      ai_input_builder.py
      report_builder.py
    ai_result_importer.py
  tests/
    fixtures/
      tiktok_sample.csv
  main.py
  requirements.txt
```

## データフロー

1. `data/raw/tiktok/` に手動 CSV を配置する。
2. `src/importers/tiktok_csv.py` が CSV を読み込む。
3. `src/core/normalize.py` が `NormalizedTrendItem` へ変換する。
4. `src/storage/sqlite.py` が SQLite に保存する。
5. `src/builders/ai_input_builder.py` がジャンル別 JSONL を生成する。
6. `src/ai_result_importer.py` が AI 分析結果 JSONL を取り込む。
7. `src/builders/report_builder.py` が Markdown 週次レポートを生成する。

## 初期 MVP では作らないもの

- Steam / YouTube / Reddit adapter
- TypeScript CLI
- package.json
- TikTok スクレイピング
- Web UI
