# Testing

## 必須チェック

- lint
- typecheck
- unit test
- サンプルデータでの normalize 確認
- JSONL が1行1JSONとして壊れていないこと

## テスト観点

- sourceごとに raw データが欠損しても落ちない。
- normalized schema の required 項目が埋まる。
- genre 複数指定が動く。
- 出力先ディレクトリが存在しない場合に作成される。
- CSV出力で配列・objectが壊れた列にならない。

## 実装後に明記するもの

実際の技術スタックが決まったら、`AGENTS.md` に検証コマンドを追記する。
