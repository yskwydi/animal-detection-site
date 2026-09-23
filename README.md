# animal-detection — 技術提案 ＆ PoC設計（公開サマリ）

スマートフォン × クラウド生成 AI で専用トレイルカメラを置き換える、アノテーション不要の野生動物観測プラットフォームの技術提案と、Phase 1 の検証結果をまとめた公開サイトです。

🔗 **公開サイト**: https://yskwydi.github.io/animal-detection-site/

- 古い Android 端末をエッジに、マルチモーダル生成 AI をクラウドに
- 動体検知 → 生成 AI で種同定 → DynamoDB 記録 → Web 閲覧
- 段階導入（PoC は Direct-to-S3、本番で IoT Core / PIR・BLE を後付け）、IaC は Terraform
- 推論先は環境変数で差し替え可能。Phase 1 の実測を経て Vertex AI（Gemini 3.8 Flash）を既定にし、OSS の SpeciesNet（Google、Apache-2.0）を第二の判定器として併用しています（2026-09-23、Phase 1 GO）

## ページ構成

| ページ | 内容 |
|---|---|
| `index.html` | 技術提案 ＆ PoC 設計のサマリ |
| `eval.html` | **Phase 1 検証の記録** — 実際に投げたプロンプト、評価画像、AI の回答、17 run 分の実測値、SpeciesNet 併用の結果、Go/No-Go 判定（8/8 GO）と Phase 2 の提案 |
| `gallery.html` | **判定結果 全 716 枚**（run fusion2） — 評価に使った画像 1 枚ずつと、Gemini / SpeciesNet それぞれの答え、最終判定、決め方（融合規則）、確信度、判断根拠。正解 / 誤認 / 棄権・昼 / 夜・規則で絞り込めます |

`assets/eval/` は `eval.html` の実例画像、`assets/gallery/` は `gallery.html` のサムネイル（716 枚。ラベル誤りで除外した 3 枚のサムネイルが未参照のまま残っています）です。

## 画像のライセンス

評価画像は iNaturalist の CC0 / CC BY 写真です。CC BY 分は撮影者クレジットを各画像に明記し、画像をクリックすると出典の観察ページが開きます。

> 設計の本体（仕様書・実装コード）は別リポジトリでプライベート管理しています。本リポジトリは公開用の静的サイトのみを含みます。
