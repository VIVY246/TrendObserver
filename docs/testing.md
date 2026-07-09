# Testing

## 必須チェック

- TikTok CSV を読み込める
- 必須列がない CSV でエラーになる
- TikTok CSV を共通フォーマットに正規化できる
- 正規化済みデータを SQLite に保存できる
- AI 分析用 JSONL が 1 行 1 JSON として壊れていない
- AI 分析結果 JSONL を取り込める
- Markdown レポートが生成できる

## テスト観点

- 必須列が欠けている場合、どの列が足りないか分かるエラーになる。
- 任意列が欠けている場合でも、`raw` には元行データを保持する。
- `source_specific` に TikTok 固有の値を保持できる。
- `metrics` は数値として扱える値を壊さず保持する。
- ジャンル複数指定で AI 分析用 JSONL を分けて出力できる。
- 出力先ディレクトリが存在しない場合に作成される。
- Markdown レポートに対象週、ジャンル、主要トピックが含まれる。

## 実装後に追加するもの

- 実際の test runner
- lint / format コマンド
- fixture の追加ルール
- SQLite テスト DB の扱い
