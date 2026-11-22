# 共通開発ルール移行一覧（2026-11-22）
共通ルール revision: 2026-11-22.1。各PRは指示書の変更のみ。実装・設定・配布・バージョンは変更していない。マージ前にCI・配布トリガー・既存固有ルールとの整合を確認する。
## 全リポジトリ共通
- [ ] Squash Merge、直接push禁止、必要なCIと承認、作業ブランチ削除を設定（プラン・権限制約を確認）。
- [ ] 対象アプリのみ、最新ベースでSemVer/Android versionCode+1、PR起点・prタグ・PRノート・CHANGELOGを整備。文書のみは配布しない。
- [ ] RunnerはSelf-hostedを既定とし RUNNER_LABELS を使用。OS/シェル/SDK/Docker/秘密値後処理、所要時間、並列実行・配布の直列化を検証。
- [ ] Secrets/Variablesは名称のみ統一し、値と署名鍵、既存applicationId、Firebase/GCPプロジェクトを維持。旧名からの移行・新名再登録・CI/配布確認後に旧名を削除。
- [ ] AndroidはGitHub ReleasesとFirebase App Distributionの同一ノート、版表示、配布結果を検証。
- [ ] 共通ルール同期の正本を専用リポジトリへ移す場合は所有者が作成し、同期運用を整備。
## Organization
| リポジトリ | PR | 個別作業（要確認を含む） |
|---|---|---|
| tabinokio | [#131](https://github.com/tetsukazu-lab/tabinokio/pull/131) | CI_RUNNER→RUNNER_LABELS、KEYSTORE_BASE64/PASSWORD・KEY_ALIAS/PASSWORD→ANDROID_接頭辞、FIREBASE_SERVICE_ACCOUNT→FIREBASE_SERVICE_ACCOUNT_JSON、TABINOKIO_STORAGE_API_URL→STORAGE_API_URL、公開Firebase設定の標準名。既存link.iwa.gpslogger維持。PR配布・CHANGELOG・採番確認。 |
| tabinoshiori | [#75](https://github.com/tetsukazu-lab/tabinoshiori/pull/75) | Ubuntu→セルフホスト、vタグ・docs/releases→PR起点、PRノート・CHANGELOG、VITE_設定のマッピング、FIREBASE_SERVICE_ACCOUNT_JSON。 |
| toremichi | [#27](https://github.com/tetsukazu-lab/toremichi/pull/27) | Ubuntu→セルフホスト、TOREMICHI_API_BASE_URL→API_BASE_URL、GOOGLE_SERVICES_JSONの形式、MAPS_API_KEY→GOOGLE_MAPS_API_KEY、FIREBASE_SERVICE_ACCOUNT_JSON、APP_DISTRIBUTION_GROUPS→FIREBASE_TESTER_GROUPS、CLOUD_RUN_RUNTIME_SERVICE_ACCOUNT→GCP_RUNTIME_SERVICE_ACCOUNT、PR配布/両ノート/採番。 |
| mealnote | [#52](https://github.com/tetsukazu-lab/mealnote/pull/52) | Ubuntu→セルフホスト、WIF_PROVIDER/ WIF_SERVICE_ACCOUNT/ RUN_SERVICE_ACCOUNT/ AR_REPOSITORY/TESTER_GROUPSの標準化。既存WIF・Secret Manager維持、android/CHANGELOGとPRノートの同期、GitHub Releases/採番。 |
| shirotsuzuri | [#82](https://github.com/tetsukazu-lab/shirotsuzuri/pull/82) | Ubuntu→セルフホスト、FIREBASE_APP_ID→FIREBASE_ANDROID_APP_ID、GCP_DEPLOYER_SA/GCP_RUNTIME_SA/GCP_AR_REPOの標準化。WIF維持、PR配布・両ノート・採番確認。 |
| kaikatuseatwatch | [#71](https://github.com/tetsukazu-lab/kaikatuseatwatch/pull/71) | FIREBASE_APP_ID Secret→FIREBASE_ANDROID_APP_ID Variable、Conventional Commits、CHANGELOG、Squash、再実行・採番競合。既存RunnerとPR起点は維持。 |
| kagikura | [#93](https://github.com/tetsukazu-lab/kagikura/pull/93) | USE_HOSTED_RUNNERS→RUNNER_LABELS、FIREBASE_SERVICE_ACCOUNT_JSON、vタグ・CHANGELOG起点→PR起点、Android/Windows配布・部分成功検証。暗号・復旧仕様維持。 |
| fieldcanvas | [#44](https://github.com/tetsukazu-lab/fieldcanvas/pull/44) | 11月暫定ローカル運用を維持。12月以降セルフホストCI、Firebase配布、版管理・両ノート整備。 |
| kagikura-site | [#1](https://github.com/tetsukazu-lab/kagikura-site/pull/1) | Webサイト用途の既存配信を維持、必要に応じセルフホストCI・版表示・リリース整備。 |
## 個人リポジトリ
以下は既存技術・用途を維持し、継続開発する場合に必要項目だけ適用する。旧式リポジトリのCIや配布は詳細未検証。
| リポジトリ | PR | 個別作業 |
|---|---|---|
| common | [#1](https://github.com/tetsukazu/common/pull/1) | 共通正本の暫定保管、将来の同期運用。既存Java構成維持。 |
| datacatalog | [#1](https://github.com/tetsukazu/datacatalog/pull/1) | 文書専用、DB読み取り専用、日付CHANGELOGを維持。アプリ採番/配布対象外。 |
| stock-investment-agent | [#1](https://github.com/tetsukazu/stock-investment-agent/pull/1) | 現行CI/外部API/実行要件確認、必要なセルフホスト検証。実取引なし。 |
| Sublime-BHT-BASIC | [#1](https://github.com/tetsukazu/Sublime-BHT-BASIC/pull/1) | プラグイン/配布互換性、必要なCI・採番。 |
| sublime-setting | [#1](https://github.com/tetsukazu/sublime-setting/pull/1) | 設定・秘密値管理、アプリ配布不要。 |
| todomvc | [#1](https://github.com/tetsukazu/todomvc/pull/1) | 既存サンプル・上流構成とテストを維持。 |
| magicsuggest | [#1](https://github.com/tetsukazu/magicsuggest/pull/1) | JSライブラリAPI互換性・採番・テスト。 |
| docker-upsource | [#1](https://github.com/tetsukazu/docker-upsource/pull/1) | Docker検証・環境変数・秘密値。 |
| knowledge | [#1](https://github.com/tetsukazu/knowledge/pull/1) | 文書の正本・履歴、アプリ配布不要。 |
| web | [#1](https://github.com/tetsukazu/web/pull/1) | Web構成・版表示・公開設定・CI確認。 |
| docker-knowledge | [#1](https://github.com/tetsukazu/docker-knowledge/pull/1) | 文書管理、必要に応じDocker検証。 |
| helloworld-go | [#1](https://github.com/tetsukazu/helloworld-go/pull/1) | Go標準命名・テスト・CI。 |
| nfc-felica | [#1](https://github.com/tetsukazu/nfc-felica/pull/1) | 機器/SDK依存、実機確認・Runner要件。 |
| docker-nginx | [#1](https://github.com/tetsukazu/docker-nginx/pull/1) | Docker/Nginx構成検証・秘密値分離。 |
| generator-jhipster | [#1](https://github.com/tetsukazu/generator-jhipster/pull/1) | 上流互換性・テンプレート生成テスト。 |
| redmine-java-api | [#1](https://github.com/tetsukazu/redmine-java-api/pull/1) | JDK/ビルド・Java公開API互換性・配布。 |
