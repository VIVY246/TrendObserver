# Genre Taxonomy

## 初期ジャンル

- game
- company
- ai
- entertainment
- vtuber
- gadget

## ジャンル指定ルール

- CLIでは `--genre game` のように指定する。
- 複数指定は `--genre game --genre ai` のように同じオプションを複数回渡す。
- sourceごとの検索語はこのファイルで管理する。
- 実装ではジャンルIDを小文字の ASCII 文字列として扱う。

## 例

```yaml
game:
  keywords:
    - ゲーム
    - Steam
    - 新作ゲーム
    - セール

ai:
  keywords:
    - AI
    - 生成AI
    - LLM
    - 機械学習
```
