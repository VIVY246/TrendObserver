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

## Item-level AI 分析結果 JSONL

初期実装では、元データ 1 件ごとの AI 分析結果を取り込める必要がある。`outputs/ai_results/` に保存する AI 分析結果 JSONL は 1 行 1 JSON とし、各行の `id` を元の `NormalizedTrendItem.id` と対応させる。

```json
{
  "id": "tiktok_sample_001",
  "ai_genre": "ゲーム",
  "sub_genre": "ゲーム実況",
  "format_type": "あるある共感型",
  "hook_type": "対象指定",
  "emotion": "共感",
  "target_audience": "ゲーム実況を見る10代〜20代",
  "sound_usage": "ネタ音源",
  "trend_reason": "共感コメントがつきやすい",
  "reusable_template": "〇〇な人あるあるを3つ見せる",
  "applicable_to": ["game", "service_promotion"],
  "confidence": 0.78
}
```

### Item-level 分析結果のルール

- `id` は元の `NormalizedTrendItem.id` と対応する。
- AI 分析結果 JSONL も 1 行 1 JSON とする。
- レポート生成時は `id` をキーに元データと分析結果を紐づける。
- `confidence` は 0.0〜1.0 の数値とする。
- 欠損値を AI 側で推測して埋めない。

## Weekly AI 分析結果 JSONL

週次サマリーが必要な場合も、AI が返した分析結果は 1 行 1 JSON とし、後続の Markdown レポート生成で読み込める形にする。

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

TikTok CSV は出力形式ではなく入力形式として扱う。仕様は `docs/input-format.md` に定義する。サンプル fixture は `tests/fixtures/tiktok_sample.csv` に置く。

## ファイル名

```txt
outputs/ai_input/{week}/{genre}.jsonl
outputs/ai_results/{week}.jsonl
outputs/reports/{week}.md
```

`week` は `2026-W28` のような ISO 週形式を想定する。
