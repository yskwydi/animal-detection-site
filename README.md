# animal-detection — 技術提案 ＆ PoC設計（公開サマリ）

スマートフォン × AWS で専用トレイルカメラを置き換える、アノテーション不要の野生動物観測プラットフォームの技術提案を 1 ページにまとめた公開サマリです。

🔗 **公開サイト**: https://yskwydi.github.io/animal-detection-site/

- 古い Android 端末をエッジに、Amazon Bedrock（Claude）のマルチモーダル生成 AI をクラウドに
- 動体検知 → Haiku 一次分類 → Sonnet エスカレーション → DynamoDB 記録 → Web 閲覧
- 段階導入（PoC は Direct-to-S3、本番で IoT Core / PIR・BLE を後付け）、IaC は Terraform

## ページ構成

| ページ | 内容 |
|---|---|
| `index.html` | 技術提案 ＆ PoC 設計のサマリ |
| `eval.html` | **Phase 1 検証の記録** — 実際に投げたプロンプト、評価画像、AI の回答、9 run 分の実測値と Go/No-Go 判定 |

検証ページの画像は iNaturalist の CC BY 写真です（撮影者クレジットと観察 URL をページ内および各画像下に明記）。

> 設計の本体（仕様書・実装コード）は別リポジトリでプライベート管理しています。本リポジトリは公開用の静的サイトのみを含みます。
