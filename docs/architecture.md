# Architecture

## 方針
- sourceごとにadapterを分ける
- adapterはraw dataを取得する
- normalizerがNormalizedTrendItemへ変換する
- writerがJSONL/CSVへ出力する

## 想定構成

```txt
src/
  adapters/
    steam/
    youtube/
    reddit/
  core/
    normalize.ts
    schema.ts
    genre.ts
  writers/
    jsonl.ts
    csv.ts
  cli.ts
```
