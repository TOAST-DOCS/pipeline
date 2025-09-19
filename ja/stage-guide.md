## Dev Tools > Pipeline > ステージガイド

ステージガイドではPipelineのステージについて基本的な内容を説明します。

ステージは、パイプラインスタジオ画面で右上の**編集モード**のトグルをクリックして編集モードを有効にした後 
左側の**ステージの追加**パネルでツリーメニューをクリックして、表示されたステージをドラッグ＆ドロップで追加できます。

右側の**ステージ設定**パネルでステージの詳細情報を照会したり、編集できます。

![stage-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-01_new.png)

ステージは以下のグループに分かれています。

- **ソース**
- **ビルド**
- **配布**
- **機能**

## ソース
ビルドするソースコードを取得するステージです。

### ソース - GitHub
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_2)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-02_new.png)

### ソース - GitLab
**ソースリポジトリ**は**環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_2)を選択できます。**ブランチ**にはビルドする対象のソースブランチを入力します。

![stage-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-03_new.png)

## ビルド
ビルドを行うステージです。

### ビルド - Jenkins
ユーザーが直接構成したJenkinsを利用してビルドできます。**ビルドツール**は**環境設定**の**ビルドツール設定**で追加した[ビルドツール](/Dev%20Tools/Pipeline/ja/environment-config/#_4)を選択できます。**ビルドジョブ**を選択できます。
**アーティファクト**の**開始条件**と**終了条件**を設定できます。**開始条件**を設定してステージを開始するかどうかを決定できます。 **終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-04_new.png)


### ビルド - Bake (Manifest)
ユーザーが直接構成したHelm package fileまたは[チャートリポジトリ](/Dev%20Tools/Pipeline/ja/environment-config/#_6)を使ってビルドできます。

- チャート名はHelmエンジンで構成した結果物の名前を設定します。
- NamespaceはHelmエンジンで構成した成果物のNamespaceを設定します。
- テンプレート
    - リポジトリタイプは**環境設定**の[ソースリポジトリ設定](/Dev%20Tools/Pipeline/ja/environment-config/#_2)または[チャートリポジトリ設定](/Dev%20Tools/Pipeline/ja/environment-config/#_6)で追加したリポジトリを選択できます。
    - リポジトリタイプを**GitHubファイル**または**GitLabファイル**に指定した場合
        - パスはHelm package fileのパスを入力する必要があります。
        - ブランチ名はGitHubまたはGitLabのブランチを入力します。
    - リポジトリタイプを **Helmチャート**と指定した場合
        - チャートリポジトリの名前は[チャートリポジトリの設定](/Dev%20Tools/Pipeline/ja/environment-config/#_6)で設定したリポジトリのいずれかを選択できます。
        - チャート名は、チャートリポジトリの構成で使用可能なチャート名を選択できます。
        - チャートバージョンは、チャートリポジトリの構成で使用可能なチャートのバージョンを選択できます。
- オーバーライド
    - リポジトリ情報
        - テンプレートと同じ方式で選択できます。
        - テンプレートを基本として、オーバーライドで指定した内容に置き換えてビルド結果物を作成します。
    - キー(Key) / 値(Value)
        - key,valueで構成された値を入力して特定の値を置換してビルド結果物を作成します。
    - 基本タイプ置換
        -このオプションをチェックすると、オーバーライド値を注入する時、--set-stringの代わりに--setを使用します。 --setを使用して注入された値はHelmによって基本データ型に変換されます。
- アーティファクト
    - **アーティファクト**の**開始条件**と **終了条件**を設定できます。 **開始条件**を設定してステージを開始するかどうかを決定できます。 **終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-10-29/stage-guide-05-1.png)

### ビルド - NHN Cloudビルドツールv2
NHN Cloudで提供するビルドツールを使用できます。

- ビルド環境設定
    - ビルドツールの性能と制限時間を設定できます。
- ソースビルド設定
    - **環境設定**の**イメージストア設定**で追加した[イメージストア](/Dev%20Tools/Pipeline/ja/environment-config/#_3)を選択できます。
    - ビルドする環境の**イメージ名**及び**タグ**を入力し、**ビルドコマンド**を設定します。

- ドッカーイメージビルド設定
    - **Dockerfileパス**はDockefileが存在するパスを入力します。
    - **Dockerfile実行パス**はDockerfileをビルドするパスを入力します。
    - **イメージストア**を選択し、**イメージ名**を決定したら、そこに結果物をpushします。
    - **タグ**にはイメージのタグを入力します。タグフォーマットを含めて入力すると、入力したタグフォーマット部分が動的に置換されます。

- アーティファクト設定
    - **開始条件**を設定してステージを開始するかどうかを決定できます。
    - **終了条件**を設定してステージの作成物をアーティファクトとして設定できます。


|イメージタグフォーマット | 置換される形式 | 説明                                |
| ----------- | ---------- |------------------------------------|
|{BUILD_DATE_TIME}| yyyy-MM-dd_HH_mm_ss|  年-月-日-日-時-分-秒の形式でビルド実行時刻に置換されます。 |

![stage-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-06_new.png)

## 配布
Kubernetes環境に配布を行うステージです。

### 配布 - Deploy
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**ステージ名**、**配布対象**、配布に使用する**Manifest**を入力します。
ビルドステージでタグフォーマットを使用した場合、**Manifest**のドッカーイメージタグ部分を`_{BUILD_NUMBER}`と入力すると、タグフォーマットでビルドされたイメージのうち最新の番号のイメージで配布できます。
**Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )を参照してください。

- **Manifestソース**をアーティファクトとして選択できます。選択したアーティファクトはManifest形式で作成する必要があります。
    - パイプラインで作成したアーティファクトを選択できます。
    - リポジトリから特定ファイルをアーティファクトとして選択できます。 
- **アーティファクト**の**開始条件**および**終了条件**を設定できます。**開始条件**を設定してステージを開始するかどうかを決定できます。**終了条件**を設定してステージの作成物をアーティファクトに設定できます。

![stage-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-07_new.png)

### 配布 - Patch
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
- **Namespace**, **リソースタイプ**、**選択方法**、**リソース名**、配布に使用する**Manifest**を入力します。 Patchで既存リソースの情報を修正できます。
- **Manifest**を作成する方法は[Kubernetes文書](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)を参考してください。
- **選択方法**を**動的な方法で選択**に設定する場合、**クラスタ**と**選択戦略**を入力します。
- クラスタ
    - replicaSetの場合、Pipeline内部でバージョンを指定して配布し、**動的な方法で選択**を選択すると、特定のバージョンを選択するのではなく、選択戦略によって対象を選択します。
- 選択戦略
    - Newest:当該ステージが開始された時、最も最近に配布されたリソースを選択します。
    - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
    - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
    - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
    - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![stage-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-08_new.png)

### 配布 - Scale
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
- **Namespace**, **リソースタイプ**、**選択方法**、**リソース名**、**Replicas**を入力します。 ScaleでReplicasを修正できます。
- **選択方法**を**動的な方法で選択**に設定する場合、**クラスタ**と**選択戦略**を入力します。
'- クラスタ
    - replicaSetの場合、Pipeline内部でバージョンを指定して配布し、**動的な方法で選択**を選択すると、特定のバージョンを選択するのではなく、選択戦略によって対象を選択します。
'- 選択戦略
    - Newest:当該ステージが開始された時、最も最近に配布されたリソースを選択します。
    - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
    - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
    - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
    - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![stage-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-09_new.png)

### 配布 - Rollout undo
**環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
**Namespace**、**リソースタイプ**、**リソース名**、**Revision Back**を入力します。指定したRevisionにロールバックできます。

![stage-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-10_new.png)

### 配布 - Delete
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
- **Namespace**, **リソースタイプ**、**選択方法**、***リソース名**を入力します。そのリソースを削除できます。
- **選択方法**を**動的な方法で選択**に設定する場合、**クラスタ**と**選択戦略**を入力します。
- クラスタ
    - replicaSetの場合、Pipeline内部でバージョンを指定して配布し、**動的な方法で選択**を選択すると、特定のバージョンを選択するのではなく、選択戦略によって対象を選択します。
- 選択戦略
    - Newest:当該ステージが開始された時、最も最近に配布されたリソースを選択します。
    - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
    - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
    - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
    - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![stage-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-11_new.png)

### 配布 - NHN Container Service
NCSワークロードのテンプレートを交換できるステージです。 
**NCSアプリキー**を入力すると、**NCSロール**、テンプレートリスト、ワークロードのリストが表示されます。 
変更するテンプレートをリストから選択できます。 
テンプレートを変更するワークロードをリストから選択できます。

![stage-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-12_new.png)


### 配布 - Enable
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
- **Namespace**、**リソースタイプ**、**選択方法**、**リソース名**を入力します。該当リソースを有効にできます。
    - 有効化：該当リソースをPipelineで管理し、リソースにトラフィックを送るように設定します。
- **選択方法**を**動的な方法で選択**に設定する場合、**クラスタ**と**選択戦略**を入力します。
    - クラスタ
        - replicaSetの場合、Pipeline内部でバージョンを指定して配布し、**動的な方法で選択**を選択すると、特定のバージョンを選択するのではなく、選択戦略によって対象を選択します。
    - 選択戦略
        - Newest:当該ステージが開始された時、最も最近に配布されたリソースを選択します。
        - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
        - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
        - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
        - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![stage-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-13_new.png)

### 配布 - Disable
- **環境設定**の**配布対象設定**で追加した[配布対象](/Dev%20Tools/Pipeline/ja/environment-config/#_5)を選択できます。
- **Namespace**、**リソースタイプ**、**選択方法**、**リソース名**を入力します。該当リソースを無効にできます。
    - 無効化：リソースを削除するわけではありませんが、そのリソースにトラフィックを送らないように設定します。
- **選択方法**を**動的な方法で選択**に設定する場合、**クラスタ**と**選択戦略**を入力します。
    - クラスタ
        - replicaSetの場合、Pipeline内部でバージョンを指定して配布し、**動的な方法で選択**を選択すると、特定のバージョンを選択するのではなく、選択戦略によって対象を選択します。
    - 選択戦略
        - Newest:当該ステージが開始された時、最も最近に配布されたリソースを選択します。
        - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
        - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
        - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
        - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![stage-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-14_new.png)

## 機能
追加機能を提供するステージです。

### 機能 - 承認管理
**機能 - 承認管理** ステージ以降のステージに対する**実行管理(実行、実行停止)**を承認権者が管理できます。

ステージにリクエスト内容について作成することができ、承認管理ステージの**実行管理(実行、実行停止)**機能は該当プロジェクトの **Pipeline APPROVAL ADMIN**ロールを持つユーザーだけが行うことができます。

![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-15_new.png)

**Pipeline APPROVAL ADMIN**ロールは、プロジェクトのメンバー管理、役割グループ管理で付与できます。

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)


### 機能 - Judgement(実行管理)
必要に応じて実行管理ステージの**説明**、**実行設定**の値を入力できます。

**実行設定**の有無に関係なく、次のステージに対する**実行管理(実行、実行停止**)ができ、**実行設定**を追加して次のステージの実行を選択する場合、次に説明するステージであるPrecondition(実行条件)に設定値を渡して分岐処理を行うことができます。

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-16_new.png)

### 機能 - Precondition(ステージ状態条件)
前のステージのステージ名と実行結果を選択して条件を設定できます。
指定した全ての条件が満たされなければ、次のステージが実行されます。

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-17_new.png)

### 機能 - Precondition(実行条件)
前の段階で設定されたJudgement(実行管理)ステージで渡された値を**実行条件**によって後のステージの実行を決定します。
Judgement(実行管理)ステージで渡された設定値と**実行条件の条件値**に対して**実行条件一致/実行条件不一致**の中から選択して以降のステージの実行を決定します。

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-18_new.png)

### 機能 - Webフック
**URL**にHTTPメソッドとURLを入力します。必要に応じて**リクエストヘッダ** **リクエストデータ**を追加できます。
Webフックのレスポンス値が**Fail Fast HTTPステータスコード**に入力した値のいずれかであれば、すぐに該当ステージを終了します。

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-19_new.png)

### 機能 - 他のパイプラインの実行
ステージで他のパイプライン全体を実行できます。
実行したい**パイプライン名**を選択します。

もし**実行条件**を選択解除した場合、選択したパイプラインの実行状態を待たずに、次のステージが実行されます。

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-20_new.png)

### 機能 - NHN Cloud Deployサービス配布実行
ステージでNHN Cloud Deployサービスを使用して配布を実行できます。
- 配布を実行するアーティファクトの**Command Type**が**SSH**である場合、**NHN Cloud Deployサービス配布実行**機能をサポートしておらず、**Cloud Agent**である場合にのみサポートします。関連する内容については[Deploy使用ガイド](/Dev%20Tools/Deploy/ja/console-guide/#_8)を参照してください。

**環境設定** > **NHN Cloudセキュリティ設定**で追加したセキュリティ設定を選択し、**AppKey**にはNHN Cloud Deployサービスを使用するAppkeyを入力します。

情報を入力して**確認**をクリックすると、入力したセキュリティ設定とAppkeyに合うNHN Cloud Deployの配布関連情報が表示されます。

その後、NHN Cloud Deployサービスを通じて配布する**アーティファクト**、**サーバーグループ**、**シナリオ**を選択できます。


**配布制限時間**には該当ステージの実行完了待機時間を指定します。(最短1分、最長600分)
**配布詳細設定**では、配布する対象に条件を追加できます。

**サーバー選択**で配布するサーバーを選択できます。**全体サーバー**を選択すると、全体サーバーを対象に配布を実行でき、**サーバー選択**をクリックすると、配布するサーバーを選択できます。

**同時サーバー実行数**でNHN Cloud Deployサービスが同時にいくつのサーバーを実行するか選択できます。(デフォルト値は1、最大サーバー数)

**配布ノート**には配布実行情報を入力できます。

詳しい説明については[Deploy使用ガイド](/Dev%20Tools/Deploy/ja/reference/#_1)を参照してください。

![stage-guide-21](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-21_new.png)

### 機能 - ユーザー変数を提供
パイプライン内で、後続のステージで再利用する変数を定義します。このステージで作成した変数は、接続されている全ての後続ステージで使用でき、最大5つまで作成できます。

**変数の使用方法**

- パイプライン式として参照します。
- (例) 変数名が`myImage`の場合：

```
${myImage}
```
> 実際に使用する際は、変数名をステージで指定した値に書き換えてください。(例: `${buildTag}`, `${buildImage}`)
**変数のタイプ別の説明と例**

| 変数タイプ                | 説明                                                                                                                        | 変数の値例                                                                                                                                                                                       |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 自動実行時のイメージ情報 | パイプラインが**イメージリポジトリ**タイプとして自動実行された際に、イメージ情報を利用できます。<br/>デフォルト値を設定し、自動実行（イメージリポジトリタイプ）で開始されなかった場合に使用する代替値を設定できます。 | フルイメージ名: `dd530b18-kr1-registry.container.nhncloud.com/pipeline-test/image-name:tag`<br/>イメージ名: `dd530b18-kr1-registry.container.nhncloud.com/pipeline-test/image-name`<br/>イメージタグ: `tag` |
| Judgement(実行管理)の選択値 | 接続された**機能 - Judgement(実行管理)**ステージで選択した値を、変数として作成します。                            | `Judgement(実行管理)`ステージの`選択値`                                                                                                                                                                | 
| 生成タイプの日付文字列            | **機能 - ユーザー変数を提供**ステージが実行された時点を基準に、日付文字列を生成します。<br/>日付フォーマットは、`java.text.SimpleDateFormat`の規則に従います。                    | フォーマット: `yyyyMMddHHmmss` -> 変数値: `20250903113846`<br/>フォーマット: `yyyy-MM-dd HH:mm:ss Z` -> 変数値: `2025-09-04 16:58:44 +0900`                                                                            |
| ランダムUUID           | 8-4-4-4-12のハイフン表記（計36文字）の標準文字列を持つバージョン4（UUID v4）を生成します。                                                                | `550e8400-e29b-41d4-a716-446655440000`                                                                                                                                                       |
| ユーザー入力値             | 直接入力した値を、変数として使用できます。                                                                                                  | `入力値`                                                                                                                                                                                       |

![stage-guide-22](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-22.png)

### 機能 - イメージの脆弱性分析
イメージを対象に脆弱性分析を実行するステージです。

- イメージリポジトリ
    - **環境設定**の**イメージリポジトリ設定**で追加した[イメージリポジトリ](/Dev%20Tools/Pipeline/ko/environment-config/#_3)を選択できます。
- **イメージ名**と**タグ**を入力し、分析するイメージを指定します。

![stage-guide-23](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-23.png)

イメージの脆弱性分析の結果はステージの実行結果で確認でき、脆弱性が発見された場合は、分析結果に詳細情報が表示されます。

![stage-guide-24](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-24.png)

### 機能 - ソースコードの脆弱性分析

ソースコードを対象に脆弱性分析を実行するステージです。

- ソースリポジトリ
  - **環境設定**の**ソースリポジトリ設定**で追加した[ソースリポジトリ](/Dev%20Tools/Pipeline/ko/environment-config/#_2)を選択できます。
- **ブランチ**を選択し、分析するソースコードを指定します。

![stage-guide-25](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-25.png)

ソースコードの脆弱性分析の結果はステージの実行結果で確認でき、脆弱性が発見された場合は、分析結果に詳細情報が表示されます。

![stage-guide-26](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-09-23/stage-guide-26.png)

## ステージ共通機能
### ステージ失敗時

ステージが失敗した時のパイプライン実行に関する設定を選択できます。


- 全てのパイプライン終了
    - 該当ステージが失敗すると、パイプライン全体が終了します。
- 該当ブランチのみ終了
    - 該当ステージが属するブランチだけ終了し、他のブランチのパイプラインは続行されます。
- 該当ブランチが終了し、他のブランチの終了時に失敗
    - そのステージが属するブランチだけが終了し、他のブランチのパイプラインは続行されます。しかし、そのパイプラインの結果は失敗として残ります。
- 失敗を無視して進行
    - 該当ステージが失敗しても、次のステージが進行します。

![stage-guide-27](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-05-28/stage-guide-27.png)
