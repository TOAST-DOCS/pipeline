## Dev Tools > Pipeline > ステージガイド

ステージガイドではPipelineのステージについて基本的な内容を説明します。
**パイプライン管理** > **+パイプライン作成**をクリックしてパイプラインを作成します。作成したパイプラインを選択したら、下部の**ステージ**タブで **+ステージ追加**をクリックしてステージを追加できます。

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-01.png)

ステージは以下のグループに分かれています。
- **ソース**
- **ビルド**
- **配布**
- **機能**

### ソース
ビルドするソースコードを取得するステージです。

#### ソース - GitHub
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_2)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### ソース - GitLab
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_2)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### ビルド
ビルドを行うステージです。

#### ビルド - Jenkins
ユーザーが直接構成したJenkinsを利用してビルドできます。**ビルドツール**は**環境設定**の**ビルドツール設定**で追加した[ビルドツール](/Dev%20Tools/Pipeline/ja/environment-config/#_4)を選択できます。**ビルドジョブ**を選択し、**ビルドジョブパラメータ**を入力できます。
**アーティファクト**の**開始条件**と**終了条件**を設定できます。**開始条件**を設定してステージを開始するかどうかを決定できます。 **終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-01.png)
![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-04.png)

#### ビルド - NHN Cloudビルドツール
NHN Cloudで提供するビルドツールを使用できます。
- ビルド環境設定
  - **環境設定**の**イメージストア設定**で追加した[イメージストア](/Dev%20Tools/Pipeline/ja/environment-config/#_3)を選択できます。
  - ビルドする環境の**イメージ名**を選択し、**ビルドツール性能**と**ビルド時間制限(分)**、**ビルドコマンド**を設定します。
  
- ビルド結果設定
  - ビルド結果物の**Dockerfileパス**を設定し、**Dockerfile実行パス**を設定します。
  - **イメージストア**を選択し、**イメージ名**を決定したらそのリポジトリに結果物をpushします。
  - **タグフォーマット使用**を選択すると、タグフォーマットでタグが固定され、`_{BUILD_NUMBER}`形式の動的に作成されるタグでイメージが作成されます。

'- アーティファクト設定
  - **開始条件**を設定してステージを開始するかどうかを決定できます。
  - **終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-02.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)

#### ビルド - Bake (Manifest)
ユーザーが直接構成したHelm package fileまたは[チャートリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_6)を利用してビルドできます。 
'- チャート名はHelmエンジンで構成した結果物の名前を設定します。
'- NamespaceはHelmエンジで構成した結果物のNamespaceを設定します。
'- テンプレート
  - リポジトリタイプは**環境設定**の[ソースリポジトリ設定](/Dev%20Tools/Pipeline/ja/environment-config/#_2)または[チャートリポジトリ設定](/Dev%20Tools/Pipeline/ja/environment-config/#_6)で追加したリポジトリを選択できます。
  - リポジトリタイプを**GitHubファイル**または**GitLabファイル**に指定した場合
    - パスはHelm package fileのパスを入力する必要があります。
    - ブランチ名はGithubまたはGitlabのブランチを入力します。
  - リポジトリタイプを**Helmチャート**と指定した場合
    - チャートリポジトリの名前は[チャートリポジトリ設定](/Dev%20Tools/Pipeline/ja/environment-config/#_6)で設定したリポジトリの中から1つを選択できます。
    - チャート名はチャートリポジトリの構成で使用できるチャート名を選択できます。
    - チャートバージョンはチャートリポジトリの構成で使用できるチャートバージョンを選択できます。
'- オーバーライド
  - リポジトリ情報
    - テンプレートと同じ方式で選択できます。
    - テンプレートを基本にしてオーバーライドで指定した内容に置き換えてビルド結果物を作成します。
  - キー(Key) / 値(Value)
    - key、valueで構成された値を入力して特定値を置換してビルド結果物を作成します。
  - 基本タイプ置換
    - このオプションをチェックすると、オーバーライド値を注入する時、--set-stringの代わりに--setを使用します。--setを使用して注入された値はHelmによって基本データ型に変換されます。
'- アーティファクト
  - **アーティファクト**の**開始条件**と**終了条件**を設定できます。**開始条件**を設定してステージを開始するかどうかを決定できます。**終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-12.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-13.png)

### 配布
Kubernetes環境に配布を行うステージです。

#### 配布 - Deploy
'- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**ステージ名**、**配布対象**、配布に使用する**Manifest**を入力します。
ビルドステージでタグフォーマットを使用した場合、**Manifest**のドッカーイメージタグ部分を`_{BUILD_NUMBER}`と入力すると、タグフォーマットでビルドされたイメージのうち最新の番号のイメージで配布できます。
**Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )を参照してください。
- **Manifestソース**をアーティファクトとして選択できます。選択したアーティファクトはManifest形式で作成する必要があります。
  - パイプラインで作成したアーティファクトを選択できます。
  - リポジトリから特定ファイルをアーティファクトとして選択できます。 
- **アーティファクト**の**開始条件**および**終了条件**を設定できます。**開始条件**を設定してステージを開始するかどうかを決定できます。**終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-06.png)
![stage-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-15.png)
![stage-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-16.png)
![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-05.png)

#### 配布 - Patch
**環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、配布に使用する**Manifest**を入力します。 Patchで既存リソースの情報を修正できます。
**Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)を参照してください。

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-07.png)

#### 配布 - Scale
**環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、**Replicas**を入力します。 ScaleでReplicasを修正できます。

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-08.png)

#### 配布 - Rollout undo
**環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、**Revision Back**を入力します。指定したRevisionにロールバックできます。

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### 配布 - Delete
**環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**を入力します。そのリソースを削除できます。

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-10.png)

### 機能
追加機能を提供するステージです。

#### 機能 - Webhook
**URL**にHTTPメソッドとURLを入力します。必要に応じて**リクエストヘッダ**と**リクエストデータ**を追加できます。
Webhookのレスポンス値が**Fail Fast HTTPステータスコード**に入力した値の1つである場合は、すぐにそのそのステージを終了します。

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)

#### 機能 - Judgement(実行管理)
必要に応じて実行管理ステージの**説明**、**実行設定**の値を入力できます。

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-12.png)

**実行設定**の有無に関係なく、次のステージに対する**実行管理(実行、実行停止**)ができ、**実行設定**を追加して次のステージの実行を選択する場合、次に説明するステージであるPrecondition(実行条件)に設定値を渡して分岐処理を行うことができます。

![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-13.png)

#### 機能 - Precondition(実行条件)
前の段階で設定されたJudgement(実行管理)ステージで渡された値を**実行条件**によって後のステージの実行を決定します。
Judgement(実行管理)ステージで渡された設定値と**実行条件の条件値**に対して**実行条件一致/実行条件不一致**の中から選択して以降のステージの実行を決定します。

![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-14.png)
