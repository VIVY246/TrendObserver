# Genre Taxonomy

## 初期ジャンル

- game
- work

## 将来候補

- company
- ai
- entertainment
- vtuber
- gadget

## ジャンル指定ルール

- CLIでは `--genres game work` のように指定する想定とする。
- sourceごとの検索語は `config/genres.yml` で管理する。
- 実装ではジャンルIDを小文字の ASCII 文字列として扱う。

## 例

```yaml
genres:
  - id: game
    name: Game
    queries:
      - game
  - id: work
    name: Work
    queries:
      - work
```
