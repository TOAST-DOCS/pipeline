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

#### 配布 - NCS
NCSテンプレートとワークロードを作成できるステージです。 
**NCS Appkey**にはNCS商品のappkeyを入力します。 
**NCS実行メンバー**は現在ステージ編集中のメンバーに設定され、設定されたメンバーはNCSを利用できる権限が必要です。 
**ネットワーク**は**Subnet**のリストが表示され、必ず一つを選択する必要があります。 
**イメージURL**はイメージレジストリアドレスとイメージ名およびタグを入力します。
 - 例  
`example-kr1-registry.container.nhncloud.com/registry/ubuntu:18.04`

イメージのタグに`_{BUILD_NUMBER}`と入力すると、タグフォーマットでビルドされたイメージの中で最も新しい番号のイメージで配布できます。  
**コンテナ設定**では一つ以上のコンテナを**追加**する必要があり、詳しい説明は[NCSガイド](/Container/NCS/ja/user-guide)を参考してください。  
**ワークロード設定**の詳しい説明は[NCSガイド](/Container/NCS/ja/user-guide)を参照してください。

![stage-guide-21.png](https://static.toastoven.net/prod_pipeline/2024-01-23/stage-guide-21.png)
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

#### 機能 - 他のパイプラインの実行
ステージで他のパイプライン全体を実行できます。
実行したい**パイプライン名**を選択します。
![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-15.png)

**実行条件**を選択解除すると、選択したパイプラインの実行状態を待たずに、次のステージが実行されます。

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-16.png)

#### 機能 - 承認管理
**機能 - 承認管理**ステージ以降のステージに対する**実行管理(実行、実行停止)**を承認権者が管理できます。

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-17.png)

ステージにリクエスト内容に対して作成でき、承認管理ステージの**実行管理(実行、実行停止)**は、プロジェクトロールで**Pipeline APPROVAL ADMIN**ロールを持つユーザーのみ行うことができます。

**Pipeline APPROVAL ADMIN**ロールは、プロジェクトのメンバー管理、ロールグループ管理で付与できます。

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

#### 機能 - NHN Cloud Deployサービス配布実行
ステージでNHN Cloud Deployサービスを使用して配布を実行できます。
- 配布を実行するアーティファクトの**Command Type**が**SSH**である場合、**NHN Cloud Deployサービス配布実行**機能をサポートしておらず、**Cloud Agent**である場合にのみサポートします。関連する内容については[Deploy使用ガイド](https://docs.nhncloud.com/ja/Dev%20Tools/Deploy/ja/console-guide/#_8)を参照してください。

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-19.png)

**環境設定** > **NHN Cloudセキュリティ設定**で追加したセキュリティ設定を選択し、**AppKey**にはNHN Cloud Deployサービスを使用するAppkeyを入力します。

情報を入力し**検索**をクリックすると、入力したセキュリティ設定とAppkeyに合うNHN Cloud Deployの配布関連情報が表示されます。

その後、NHN Cloud Deployサービスを通じて配布する**アーティファクト**、**サーバーグループ**、**シナリオ**を選択できます。


**配布制限時間**には該当ステージの実行完了待機時間を指定します。(最短1分、最長600分)

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-20.png)

**配布詳細設定**では、配布する対象に条件を追加できます。

**サーバー選択**で配布するサーバーを選択できます。**全体サーバー**を選択すると、全体サーバーを対象に配布を実行でき、**サーバー選択**をクリックすると、配布するサーバーを選択できます。

**同時サーバー実行数**でNHN Cloud Deployサービスが同時にいくつのサーバーを実行するか選択できます。(デフォルト値は1、最大サーバー数)

**配布ノート**には配布実行情報を入力できます。

詳しい説明については[Deploy使用ガイド](https://docs.nhncloud.com/ja/Dev%20Tools/Deploy/ja/reference/#_1)を参照してください。
