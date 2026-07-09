# Data Schema

## NormalizedTrendItem

共通フォーマットは、AI 分析で横断利用するトップレベル項目と、サービス固有情報を保持する `source_specific` / `raw` に分ける。

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
  "metrics": {},
  "source_specific": {},
  "raw": {}
}
```

| field             | type   | required | description                                           |
| ----------------- | ------ | -------: | ----------------------------------------------------- |
| `id`              | string |      yes | source 内で一意に識別できる ID                        |
| `source`          | string |      yes | データソース。初期 MVP では `tiktok`                  |
| `collected_at`    | string |      yes | データを確認・収集した日付。`YYYY-MM-DD`              |
| `genre_query`     | string |      yes | CSV 取り込み時に紐づけるジャンルまたは検索意図        |
| `item_type`       | string |      yes | `video`、`keyword`、`sound` などの項目種別            |
| `title`           | string |      yes | タイトル、名称、キーワードなど                        |
| `url`             | string |       no | 元投稿や参照ページの URL                              |
| `description`     | string |       no | AI 分析用に使う説明文                                 |
| `metrics`         | object |       no | views、likes、comments など比較しやすい数値           |
| `source_specific` | object |       no | TikTok などサービス固有の補助情報                     |
| `raw`             | object |      yes | 取り込み元 CSV の行データをできるだけ欠落なく保持する |

## 方針

- AI 分析で共通利用する値はトップレベルに正規化する。
- source 固有の値は `source_specific` に整理し、元データは `raw` に残す。
- 欠損値を無理に埋めない。
- 共通スキーマのフィールド名は不用意に変更しない。
- 新しい取得元を追加する場合も、このトップレベル構造を維持する。
