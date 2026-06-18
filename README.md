# animal-detection — 技術提案 ＆ PoC設計（公開サマリ）

スマートフォン × AWS で専用トレイルカメラを置き換える、アノテーション不要の野生動物観測プラットフォームの技術提案を 1 ページにまとめた公開サマリです。

🔗 **公開サイト**: https://yskwydi.github.io/animal-detection-site/

- 古い Android 端末をエッジに、Amazon Bedrock（Claude）のマルチモーダル生成 AI をクラウドに
- 動体検知 → Haiku 一次分類 → Sonnet エスカレーション → DynamoDB 記録 → Web 閲覧
- 段階導入（PoC は Direct-to-S3、本番で IoT Core / PIR・BLE を後付け）、IaC は Terraform

> 設計の本体（仕様書・実装コード）は別リポジトリでプライベート管理しています。本リポジトリは公開用の静的サイトのみを含みます。
