# AI Analysis Guide

## 分析目的

- どの話題が伸びているか。
- どのジャンルで急上昇しているか。
- TikTok の手動 CSV 由来データから、週次で見るべき話題は何か。
- ジャンル別のトレンド差分は何か。

## AIに渡す前提

- `outputs/ai_input/` の JSONL を入力する。
- 各行は `docs/data-schema.md` の `NormalizedTrendItem` として扱う。
- `raw` は元 CSV 行の確認用、`source_specific` は TikTok 固有情報の補助として扱う。
- metrics は同一 source 内の相対比較を優先する。

## 注意点

- 欠損値を推測で埋めない。
- 取得元ごとの人気指標を単純に横並び比較しない。
- 分析結果には対象週、source、genre を明記する。
- レポート生成で参照できるよう、根拠にした `id` を残す。
