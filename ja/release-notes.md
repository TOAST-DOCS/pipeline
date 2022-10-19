## Dev Tools > Pipeline > リリースノート

### 2022. 10. 25.
* 配布対象kubernetes接続テストが非同期方式に変更されました。

### 2022. 08. 23.
* ステージがないPipelineを[API](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/api-guide/#pipeline)で実行したとき、失敗レスポンスを返すように修正しました。

### 2022. 07. 26.
* 機能 - Webhookステージが追加されました。
* APIエンドポイントのドメインがapi-pipeline.cloud.toast.comからkr1-pipeline.api.nhncloudservice.comに変更されました。

### 2022. 05. 24
* ソースリポジトリ、イメージストア、ビルドツール、配布対象に接続確認機能が追加されました。 [Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ko/console-guide)で使い方を確認できます。 
* CloudTrailに詳細内容が追加されました。
  * 設定の削除時に詳細内容を追加。
  * パイプライン実行関連の詳細内容を追加。

### 2022. 02. 22
* ソースリポジトリにGitLabが追加されました。 [Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/console-guide/#_1)で使い方を確認できます。

### 2022. 01. 25.
* Pipeline実行APIが追加されました。 [Pipeline APIガイド](/Dev%20Tools/Pipeline/ja/api-guide/#pipeline)で使い方を確認できます。
* 発見されたイシュー(原因分析後に改善予定です。)
  * 開発環境の作成時に開発環境の制約事項に値を指定すると、作成に失敗する現象があります。

### 2021. 05. 25.
* CloudTrailと連動します。 Pipelineで発生したイベントをCloudTrailで確認できます。

### 2021. 04. 27.

#### 新規サービスリリース
* ソースコードのビルド、コンテナイメージの作成、コンテナイメージの配布など、アプリケーション配布フローを管理することができる継続的な配布(continuous deployment)サービスです。
