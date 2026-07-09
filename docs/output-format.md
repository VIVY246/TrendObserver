# Output Format

## AI 分析用 JSONL

`outputs/ai_input/` に出力する。1 行 1 アイテムで、各行は `NormalizedTrendItem` として解釈できる有効な JSON にする。

```json
{
  "id": "source_unique_id",
  "source": "tiktok",
  "collected_at": "2026-07-08",
  "genre_query": "game",
  "item_type": "video",
  "title": "タイトルまたは名称",
  "url": "https://example.com",
  "description": "AI分析用の説明文",
  "metrics": { "views": 1200 },
  "source_specific": {},
  "raw": {}
}
```

## AI 分析結果 JSONL

`outputs/ai_results/` に保存する。AI が返した分析結果も 1 行 1 JSON とし、後続の Markdown レポート生成で読み込める形にする。

```json
{
  "week": "2026-W28",
  "genre": "game",
  "summary": "今週の主要トレンド要約",
  "topics": [],
  "source_ids": ["source_unique_id"]
}
```

## Markdown レポート

`outputs/reports/` に出力する。人間が読める週次レポートとして、対象週、対象ジャンル、主要トピック、根拠となる source を含める。

## 入力 CSV

TikTok CSV は出力形式ではなく入力形式として扱う。サンプル fixture は `tests/fixtures/tiktok_sample.csv` に置く。

## ファイル名

```txt
outputs/ai_input/{week}/{genre}.jsonl
outputs/ai_results/{week}.jsonl
outputs/reports/{week}.md
```

`week` は `2026-W28` のような ISO 週形式を想定する。
