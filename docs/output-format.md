# Output Format

## JSONL

1行1アイテムで出力する。各行は `NormalizedTrendItem` として解釈できる有効な JSON にする。

```json
{
  "source": "steam",
  "source_item_id": "example",
  "title": "Example Game",
  "genre": "game",
  "fetched_at": "2026-07-08T00:00:00Z",
  "metrics": { "reviews": 1200 },
  "raw": {}
}
```

## CSV

最低限の分析用カラムのみ出力する。

| column         | description                    |
| -------------- | ------------------------------ |
| source         | 取得元                         |
| source_item_id | 取得元でのID                   |
| url            | 元投稿・ページURL              |
| title          | タイトル                       |
| author         | 投稿者・開発元等               |
| published_at   | 投稿日時                       |
| fetched_at     | 取得日時                       |
| genre          | 指定ジャンル                   |
| keywords       | `;` 区切りのキーワード         |
| metrics_json   | metrics を JSON 文字列化した値 |

## ファイル名

```txt
outputs/{date}/{source}-{genre}.jsonl
outputs/{date}/{source}-{genre}.csv
```

`date` は実行日の `YYYY-MM-DD` とする。
