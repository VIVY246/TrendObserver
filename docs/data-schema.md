# Data Schema

## NormalizedTrendItem

| field          | type     | required | description                  |
| -------------- | -------- | -------: | ---------------------------- |
| source         | string   |      yes | x, youtube, steam, reddit 等 |
| source_item_id | string   |      yes | 取得元でのID                 |
| url            | string   |       no | 元投稿・ページURL            |
| title          | string   |       no | タイトル                     |
| body           | string   |       no | 本文・説明文                 |
| author         | string   |       no | 投稿者・開発元等             |
| published_at   | string   |       no | 投稿日時 ISO8601             |
| fetched_at     | string   |      yes | 取得日時 ISO8601             |
| genre          | string   |      yes | 指定ジャンル                 |
| keywords       | string[] |       no | 抽出キーワード               |
| metrics        | object   |       no | likes, views, comments 等    |
| raw            | object   |      yes | 元データ                     |

## 方針

- source固有の値は raw に残す。
- AI分析で共通利用する値はトップレベルに正規化する。
- 欠損値を無理に埋めない。
- 取得元ごとの差異は adapter 層と raw に閉じ込める。
