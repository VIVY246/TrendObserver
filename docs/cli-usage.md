# CLI Usage

## 想定コマンド

```bash
trend-observer collect --source steam --genre game --format jsonl
trend-observer collect --source steam --source reddit --genre game --genre ai --format csv
```

## オプション

| option     | required | description                           |
| ---------- | -------: | ------------------------------------- |
| `--source` |      yes | 取得元。複数指定可                    |
| `--genre`  |      yes | ジャンル。複数指定可                  |
| `--format` |       no | `jsonl` または `csv`。既定は `jsonl`  |
| `--output` |       no | 出力先ディレクトリ。既定は `outputs/` |
| `--limit`  |       no | sourceごとの最大取得件数              |

## 方針

- CLIはデータ取得、正規化、出力までを1回の実行で行う。
- source固有の引数が必要になった場合は adapter 側で扱い、共通CLIを複雑にしすぎない。
- 実装後、このファイルに実際のコマンドと例を追記する。
