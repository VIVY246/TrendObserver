# Requirements

## 現時点で開発するもの

- TikTok トレンド CSV 取り込み
- ジャンル設定 YAML の読み込み
- TikTok CSV から共通フォーマットへの正規化
- 正規化済みデータの SQLite 保存
- ジャンル別 AI 分析用 JSONL 出力
- AI 分析結果 JSONL の取り込み
- AI 分析結果をもとにした Markdown 週次レポート生成

## 前提

- TikTok のデータは TikTok Creative Center などで人が確認し、手動で CSV 化する。
- 初期 MVP はローカル CLI として動かす。
- SQLite は Python 標準ライブラリの `sqlite3` を使う。
- サービス固有の値は `source_specific` と `raw` に保持する。
- AI が横断分析しやすいよう、共通スキーマのトップレベル項目を安定させる。

## 非目標

- TikTok の完全自動取得
- TikTok スクレイピング
- Instagram / X の自動取得
- Web サービス化
- SaaS 化
- 課金機能
- 本格的な機械学習
- Steam / YouTube / Reddit adapter の初期実装

## 将来的に追加するもの

- YouTube、Steam、Google Trends、GitHub などの追加データソース
- Web UI
- スケジューラー
- ダッシュボード
