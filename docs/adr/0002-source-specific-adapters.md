# 0002: 取得元ごとに adapter を分ける

## Status

Accepted

## Context

Steam、YouTube、Reddit などは取得方法、rate limit、認証要否、レスポンス形式が異なる。共通処理に差異を混ぜると保守が難しくなる。

## Decision

データ取得は source ごとの adapter に閉じ込める。adapter は raw data を返し、normalizer が `NormalizedTrendItem` へ変換する。

## Consequences

- 新しい取得元を追加しやすい。
- source 固有の制約を局所化できる。
- adapter ごとの fixture と unit test が必要になる。
