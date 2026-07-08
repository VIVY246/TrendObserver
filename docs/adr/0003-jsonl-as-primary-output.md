# 0003: JSONL を主出力形式にする

## Status

Accepted

## Context

トレンドデータは1件ごとの構造が可変になりやすく、metrics や raw には object が入る。CSVのみを主形式にすると情報を落とすか、列設計が複雑になる。

## Decision

主出力形式は JSONL とする。CSV は分析しやすい最小列に絞った補助出力として扱う。

## Consequences

- AI分析に渡しやすい。
- 1行単位でストリーミング処理しやすい。
- 表計算ソフト向けにはCSV writerで必要な列だけ出力する。
