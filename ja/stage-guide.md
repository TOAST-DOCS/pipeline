## Dev Tools > Pipeline > ステージガイド

ステージガイドではPipelineのステージについて基本的な内容を説明します。
**パイプライン管理** > **+パイプライン作成**をクリックしてパイプラインを作成します。作成したパイプラインを選択したら、下部の**ステージ**タブで **+ステージ追加**をクリックしてステージを追加できます。

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-01.png)

ステージは以下のグループに分かれています。
- **ソース**
- **ビルド**
- **配布**
- **機能**

### ソース
ビルドするソースコードを取得するステージです。

#### ソース - GitHub
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### ソース - GitLab
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### ビルド
ビルドを行うステージです。

#### ビルド - Jenkins
ユーザーが直接構成したJenkinsを利用してビルドできます。**ビルドツール**は**環境設定**の**ビルドツール設定**で追加した[ビルドツール](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。**ビルドジョブ**を選択し、**ビルドジョブパラメータ**を入力できます。

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-04.png)

#### ビルド - NHN Cloudビルドツール
NHN Cloudで提供するビルドツールを使用できます。
- ビルド環境設定
  - **環境設定**の**イメージストア設定**で追加した[イメージストア](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
  - ビルドする環境の**イメージ名**を選択し、**ビルドツール性能**と**ビルド時間制限(分)**、**ビルドコマンド**を設定します。
  
- ビルド結果設定
  - ビルド結果物の**Dockerfileパス**を設定し、**Dockerfile実行パス**を設定します。
  - **イメージストア**を選択し、**イメージ名**を決定したらそのリポジトリに結果物をpushします。
  - **タグフォーマット使用**を選択すると、タグフォーマットでタグが固定され、`_{BUILD_NUMBER}`形式の動的に作成されるタグでイメージが作成されます。

![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-01-13/stage-guide-01.png)

### 配布
Kubernetes環境に配布を行うステージです。

#### 配布 - Deploy
**環境設定**の**配布対象設定**で追加した[配布対象](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
**ステージ名**、**配布対象**、配布に使用する**Manifest**を入力します。
ビルドステージでタグフォーマットを使用した場合、**Manifest**のドッカーイメージタグ部分を`_{BUILD_NUMBER}`と入力すると、タグフォーマットでビルドされたイメージのうち最新の番号のイメージで配布できます。
**Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )を参照してください。

![stage-guide-06](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-06.png)

#### 配布 - Patch
**環境設定**の**配布対象設定**で追加した[配布対象](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、配布に使用する**Manifest**を入力します。 Patchで既存リソースの情報を修正できます。
**Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)を参照してください。

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-07.png)

#### 配布 - Scale
**環境設定**の**配布対象設定**で追加した[配布対象](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、**Replicas**を入力します。 ScaleでReplicasを修正できます。

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-08.png)

#### 配布 - Rollout undo
**環境設定**の**配布対象設定**で追加した[配布対象](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、**Revision Back**を入力します。指定したRevisionにロールバックできます。

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### 配布 - Delete
**環境設定**の**配布対象設定**で追加した[配布対象](https://docs.toast.com/ja/Dev%20Tools/Pipeline/ja/console-guide/#_1)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**を入力します。そのリソースを削除できます。

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-10.png)

### 機能
追加機能を提供するステージです。

#### 機能 - Webhook
**URL**にHTTPメソッドとURLを入力します。必要に応じて**リクエストヘッダ**と**リクエストデータ**を追加できます。
Webhookのレスポンス値が**Fail Fast HTTPステータスコード**に入力した値の1つである場合は、すぐにそのそのステージを終了します。

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)
