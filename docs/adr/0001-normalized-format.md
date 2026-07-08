# 0001: NormalizedTrendItem を共通形式にする

## Status

Accepted

## Context

SNS、動画サイト、Steam などは取得できるデータ構造と指標が異なる。取得元ごとの形式をそのまま出力すると、AI分析やCSV化のたびに source 固有の分岐が増える。

## Decision

取得したデータは `NormalizedTrendItem` に変換してから出力する。source 固有の値は `raw` に保持し、共通分析に使う値だけトップレベルへ正規化する。

## Consequences

- adapter の実装責務が明確になる。
- AI分析側は共通スキーマを前提にできる。
- source 固有の詳細分析では `raw` を参照する必要がある。
