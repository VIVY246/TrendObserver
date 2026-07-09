# CLI Usage

## 想定コマンド

まだ本格実装前のため、以下は Python CLI の想定コマンドです。

```bash
python main.py import --source tiktok --file data/raw/tiktok/tiktok_2026-07-08.csv
python main.py build-ai-input --sources tiktok --genres game work --week 2026-W28
python main.py import-ai-results --file outputs/ai_results/2026-W28.jsonl
python main.py report --genres game work --week 2026-W28
```

## コマンド案

| command             | purpose                                      |
| ------------------- | -------------------------------------------- |
| `import`            | 手動 CSV を読み込み、正規化して SQLite に保存する |
| `build-ai-input`    | ジャンル別に AI 分析用 JSONL を出力する       |
| `import-ai-results` | AI 分析結果 JSONL を取り込む                  |
| `report`            | AI 分析結果から Markdown 週次レポートを生成する |

## 主なオプション案

| option      | required | description                                  |
| ----------- | -------: | -------------------------------------------- |
| `--source`  |      yes | 取り込み元。初期 MVP では `tiktok`           |
| `--file`    |      yes | 入力 CSV または AI 分析結果 JSONL のパス     |
| `--sources` |       no | AI 入力作成時の source 指定。複数指定可      |
| `--genres`  |       no | 対象ジャンル。複数指定可                     |
| `--week`    |       no | レポート対象週。例: `2026-W28`               |

## 方針

- CLI はローカル実行を前提にする。
- 初期 MVP では TikTok CSV の取り込みを中心にする。
- 自動取得やスクレイピング用のコマンドは作らない。
- source 固有の引数が必要になった場合は importer 側で扱い、共通 CLI を複雑にしすぎない。
- 実装後、このファイルに実際のコマンドと例を追記する。
