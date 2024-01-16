## Dev Tools > Pipeline > リリースノート

### 2024. 01. 23.
*  NHN Container Service(NCS)のテンプレートとワークロードを作成できる**配布 - NCS** ステージが追加されました。
* NHN Cloud Deploy Serviceステージでシナリオ選択時にシナリオ確認ボタンが追加されました。
    * **シナリオ確認**をクリックすると、該当シナリオのタスク情報を確認できます。
* Pipeline実行履歴と配布対象作業履歴を確認できる**配布履歴管理**ページが追加されました。[配布履歴管理ガイド](/Dev%20Tools/Pipeline/ja/deploy-history-management)で使い方を確認できます。

### 2023. 12. 19.
* NHN Cloud Deployの配布シナリオを実行できる **機能 - NHN Cloud Deploy Service** ステージが追加されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ja/stage-guide/#-)で使い方を確認できます。
* Github自動実行設定に**アーティファクト**項目が追加されました。 特定のファイルをアーティファクトとして設定し、Git push eventが発生すると、そのファイルが含まれているかどうかによってパイプラインを実行します。

### 2023. 10. 31.
* 承認なしで以降のステージを実行できないように管理する**機能 - 承認管理**ステージが追加されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ja/stage-guide/#-)で詳細を確認できます。
* パイプラインテンプレートガイド内にサンプルシナリオが追加されました。[Pipelineテンプレートガイド](/Dev%20Tools/Pipeline/ja/pipeline-management/#_2)から使用方法およびテンプレートファイルをダウンロードできます。

### 2023. 09. 26.
* パイプラインテンプレート機能が追加されました。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/pipeline-management/#_1)で使い方を確認できます。
    * パイプライン作成時にテンプレートファイル(JSON形式)をアップロードして作成できます。
    * **JSON表示**>**パイプラインテンプレートをダウンロード**でパイプラインテンプレートファイルをダウンロードできます。
* Github自動実行設定の**ブランチまたはタグ**項目でタグを使用できるようになりました。タグで自動実行するとタグを使用してビルドを実行します。

### 2023. 08. 29.
* 他のパイプライン全体を実行できる**機能 - 他パイプライン実行**ステージが追加されました。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/stage-guide/#_4)で使用方法を確認できます。
* Pipelineサービスで提供していた開発環境機能は提供されません。開発環境機能はAI EasyMakerサービスのノートパソコンで利用できます。詳細は[AI EasyMakerユーザーガイド](https://docs.nhncloud.com/ja/Machine%20Learning/AI%20EasyMaker/ja/console-guide/#_2)で確認できます。
* **配布対象モニタリング**の名称が**配布対象管理**に変更されます。
* **配布対象管理**にPipelineを通じてクラスタに配布されたワークロードを管理し、履歴を確認できる機能が追加されました。

### 2023. 06. 27.
* 配布 - Deployステージで配布した結果物を確認できる配布ターゲットモニタリング機能が追加されました。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/deploy-target-monitoring)で使用方法を確認できます。
    *配布対象モニタリングでは、Kubernetesのワークロードやサービスを確認できます。
* Pipeline分岐処理ができる機能 - Judgement(実行管理)、機能 - Precondition(実行条件)ステージが追加されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ja/stage-guide/#_4)でステージの説明を[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/pipeline-management/#_14)で使用方法を確認できます。

### 2023. 03. 28.
* Helmチャートを利用して配布する結果物を作ることができるビルド - Bake (Manifest)ステージが追加されました。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/stage-guide/#_2)で使い方を確認できます。
* ビルド - Bake (Manifest)ステージで使用できるチャートリポジトリ設定が追加されました。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/environment-config/#_6)で使い方を確認できます。
* 配布 - DeployステージでManifestをアーティファクトとして選択できる機能が追加されました。

### 2023. 02. 28.
* 外部リポジトリのリソースをパイプラインステージの開始または終了条件として使用できるアーティファクト機能が追加されました。 [Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/pipeline-management/#_1)で使い方を確認できます。

### 2023. 01. 31.
* ビルドステージでイメージタグフォーマットを使用して動的に作成されるタグを付与できる機能が追加されました。
* 配布ステージでイメージタグフォーマットを使用して動的に作成されたタグのうち最新のタグで配布できる機能が追加されました。
* イメージ自動実行の動作方式が次のように変更されました。
    * 自動実行設定のうち、タグ値が必須値から除外されました。
    * 入力されたタグと正規表現式でマッチしたタグがpushされる時、自動実行されるように変更されました。  
    * タグを入力しない場合、latestを除くタグでpushされる時に自動実行されるように変更されました。

### 2022. 12. 27.
* Pipeline作成時、ソース設定段階でソースリポジトリを選択した時のみ以前の段階に行くことができる問題を修正しました。

### 2022. 10. 25.
* 配布対象Kubernetes接続テストの時間が超過した時にも案内メッセージを表示するように修正しました。

### 2022. 08. 23.
* ステージがないPipelineを[API](/Dev%20Tools/Pipeline/ja/api-guide/#pipeline)で実行したとき、失敗レスポンスを返すように修正しました。

### 2022. 07. 26.
* 機能 - Webhookステージが追加されました。
* APIエンドポイントのドメインがapi-pipeline.cloud.toast.comからkr1-pipeline.api.nhncloudservice.comに変更されました。

### 2022. 05. 24
* ソースリポジトリ、イメージストア、ビルドツール、配布対象に接続確認機能が追加されました。 [Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/environment-config)で使い方を確認できます。 
* CloudTrailに詳細内容が追加されました。
    * 設定の削除時に詳細内容を追加。
    * パイプライン実行関連の詳細内容を追加。

### 2022. 02. 22
* ソースリポジトリにGitLabが追加されました。 [Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ja/environment-config/#_2)で使い方を確認できます。

### 2022. 01. 25.
* Pipeline実行APIが追加されました。 [Pipeline APIガイド](/Dev%20Tools/Pipeline/ja/api-guide/#pipeline)で使い方を確認できます。
* 発見されたイシュー(原因分析後に改善予定です。)
    * 開発環境の作成時に開発環境の制約事項に値を指定すると、作成に失敗する現象があります。

### 2021. 05. 25.
* CloudTrailと連動します。 Pipelineで発生したイベントをCloudTrailで確認できます。

### 2021. 04. 27.

#### 新規サービスリリース
* ソースコードのビルド、コンテナイメージの作成、コンテナイメージの配布など、アプリケーション配布フローを管理することができる継続的な配布(continuous deployment)サービスです。
