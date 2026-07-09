# Input Format

## TikTok 入力 CSV

初期 MVP では、TikTok Creative Center などで人が確認したトレンド情報を手動で CSV 化し、`data/raw/tiktok/` に配置して取り込む。

この CSV は実データを含む可能性があるため、通常はコミットしない。テスト用のサンプルだけを `tests/fixtures/tiktok_sample.csv` に置く。

## 必須列

```csv
id,collected_at,genre_query,item_type,title
```

| column         | description                                      |
| -------------- | ------------------------------------------------ |
| `id`           | CSV 内で一意にする ID                            |
| `collected_at` | データを確認・収集した日付。形式は `YYYY-MM-DD` |
| `genre_query`  | `config/genres.yml` の genre id と対応させる     |
| `item_type`    | `video` / `keyword` / `sound` など               |
| `title`        | AI 分析時の主要な表示名                          |

必須列がない場合はエラーにする。

## 推奨列

```csv
url,description,views,likes,comments,shares,hashtags,sound_name,memo
```

| column        | description                                           |
| ------------- | ----------------------------------------------------- |
| `url`         | 元投稿や参照ページの URL                              |
| `description` | AI 分析用の説明文                                     |
| `views`       | 再生数。数値として扱える場合のみ `metrics` に入れる   |
| `likes`       | いいね数。数値として扱える場合のみ `metrics` に入れる |
| `comments`    | コメント数。数値として扱える場合のみ `metrics` に入れる |
| `shares`      | シェア数。数値として扱える場合のみ `metrics` に入れる |
| `hashtags`    | TikTok 固有情報として `source_specific` に入れる      |
| `sound_name`  | TikTok 固有情報として `source_specific` に入れる      |
| `memo`        | 手動メモ。`source_specific` に入れる                  |

## 正規化ルール

- `views` / `likes` / `comments` / `shares` は数値として扱える場合のみ `metrics` に入れる。
- `hashtags` / `sound_name` / `memo` は `source_specific` に入れる。
- 元 CSV 行は `raw` に保持する。
- 欠損値を推測で補完しない。
- 実データや個人情報をテスト fixture に入れない。
