## Dev Tools > Pipeline > コンソール使用ガイド

コンソール使用ガイドではPipelineを使用するために必要な基本的な内容を説明します。
- **環境設定**
- **パイプラインの作成**
- **パイプラインの実行**
- **パイプラインの管理**
- **開発環境設定**

### 環境設定

Pipelineは、アプリケーション配布フローを構成するとき、さまざまな外部システムを使用します。環境設定でPipelineが使用する外部システムを追加できます。

Pipelineに追加できる外部システムは次のとおりです。
- ソースリポジトリ
- イメージストア
- ビルドツール
- 配布対象

#### ソースリポジトリ

ソースリポジトリを追加すると、NHN Cloudビルドツールを使用してソースコードをビルドできます。 GitHub、GitLab、GitHub Enterpriseなどのgitコマンドを使用してアクセスできるリポジトリを追加できます。

![console-guide-01](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-01.png)

**環境設定**で**ソースリポジトリ設定**をクリックすると、ソースリポジトリを管理する画面に移動します。**ソースリポジトリ追加**をクリックしてソースリポジトリを追加できます。

![console-guide-02](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-01.png)

ソースリポジトリ情報を入力し、**ソースリポジトリ接続確認**の**確認**をクリックします。GitLabソースリポジトリのトークン発行時に`read_user`、`api`、`read_api`権限が必ず必要です。接続確認後に**確認**をクリックします。

![console-guide-03](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-03.png)

#### イメージストア

イメージストアを追加すると、認証情報が必要なイメージストアにアクセスするときに使用できます。 NHN Cloudビルドツールでソースコードをビルドするコンテナを作成するときや、新たに作成したコンテナイメージをアップロードするときに使用できます。そしてパイプライン自動実行設定で自動実行を実行させるコンテナイメージを設定するときに使用できます。イメージストアにはNHN Cloud Container Registry、Docker Hubの他にPrivate Docker Registryを追加できます。

![console-guide-04](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-04.png)

**環境設定**で**イメージストア設定**をクリックすると、イメージストアを管理する画面に移動します。 **イメージストア追加**をクリックしてソースリポジトリを追加できます。

![console-guide-05](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-02.png)

イメージストア情報を入力し、**イメージストア接続確認**の**確認**をクリックします。接続確認後に**確認**をクリックします。イメージストアURLを入力していない場合はDocker Hubとして動作します。

![console-guide-06](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-06.png)

#### ビルドツール

ビルドツールを追加すると、パイプラインでビルドツールに定義したさまざまな作業を使用できます。ビルドツールにはJenkinsを追加できます。

![console-guide-07](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-07.png)

**環境設定**で**ビルドツール設定**をクリックすると、ビルドツールを管理する画面に移動します。 **ビルドツール追加**をクリックしてビルドツールを追加できます。

![console-guide-08](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-03.png)

ビルドツール情報を入力し、**ビルドツール接続確認**の**確認**をクリックします。接続確認後に**確認**をクリックします。

![console-guide-09](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-09.png)

#### 配布対象

配布対象を追加すると、パイプラインで配布対象を管理できます。配布対象にコンテナイメージを配布したり、実行中のコンテナを変更できます。配布対象にはNHN Cloud Container、Kubernetesを追加できます。

![console-guide-10](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-10.png)

**環境設定**で**配布対象設定**をクリックすると、配布対象を管理する画面に移動します。 **配布対象追加**をクリックして配布対象を追加できます。

![console-guide-11](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-04.png)

配布対象の名前と説明を入力し、Kubeconfigファイルを選択して**配布対象接続確認**の **確認**をクリックします。接続確認後に**確認**をクリックします。

![console-guide-12](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-12.png)


#### Pipeline IP
Pipelineと連動したシステムが正常に動作しない場合はACLを確認してください。Pipelineが使用するIPアドレスは **211.56.1.0/27**です。

| サービス | CIDR |
|---|---|
| Pipeline | 211.56.1.0/27 |

### パイプラインの作成

Pipelineはアプリケーション配布フローを1つ以上のステージで構成したパイプラインとして保存します。パイプライン作成では**ソースコードのビルド** > **コンテナイメージの作成** > **コンテナイメージのアップロード**、**コンテナイメージの配布**の順序で動作する基本的なパイプラインを作成できます。

![console-guide-13](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-13.png)

**パイプライン管理**で**パイプライン作成**をクリックします。パイプラインの作成は、次の手順で進めます。
- パイプライン情報の入力
- ソース設定
- ビルド設定
- 配布設定
- 最終検討およびパイプラインの作成

#### パイプライン情報の入力

パイプラインの基本情報を入力します。

![console-guide-14](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-14.png)

パイプライン名、パイプラインの説明を入力し、 **次へ**をクリックします。

#### ソース設定

NHN Cloudビルドツールでソースコードをビルドするときに使用するソースリポジトリを設定します。 NHN Cloudビルドツールを使用しない場合や、NHN Cloudビルドツールでソースコードをビルドしない場合は省略できます。

![console-guide-15](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-15.png)

ステージ名、環境設定で登録したソースリポジトリ、ソースコードをビルドするブランチを入力し、 **次へ**をクリックします。

#### ビルド設定

ビルド設定では、NHN Cloudビルドツールや、環境設定で登録したビルドツールを使用できます。ステージ名を入力し、**ビルドツール**で使用するビルドツールを選択します。

![console-guide-16](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-01.png)

NHN Cloudビルドツールを使用すると、別途ソフトウェアをインストールせずにソースリポジトリに保存したアプリケーションソースコードをビルドし、ビルドしたアプリケーションでコンテナイメージを作成し、作成したコンテナイメージをイメージストアにアップロードできます。
**ビルド環境設定**には**ソース設定**で設定したソースコードを使用してアプリケーションをビルドする方法を入力します。ソースコードのビルドに使用するコンテナイメージ、ビルドマシンの性能、ビルドに使用するコマンドを入力できます。
**ビルド結果設定**にはビルドしたアプリケーションでコンテナイメージを作成する方法を入力します。コンテナイメージを作成するときに使用するDockerfile、作成したコンテナイメージをアップロードするイメージストア、アップロードするコンテナイメージの名前とタグを入力できます。
**タグフォーマット使用**チェックボックスをクリックするとイメージタグフォーマットを使用できます。イメージタグフォーマットを使用すると、作成されたイメージのタグをNHN Cloudビルドツールで付与するビルド番号として使用します。作成されるタグは`_{BUILD_NUMBER}`形式で、BUILD_NUMBERがビルド番号です。
ビルド番号はビルドごとに増加する数字型のデータです。イメージタグフォーマット使用時にはタグが`_{BUILD_NUMBER}`形式で固定されます。

![console-guide-39](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)
NHN Cloudビルドツールで**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。

NHN Cloudビルドツールで設定可能な**アーティファクト**

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクトの種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                      |
|------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path} <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                        |
| Dockerイメージ | 開始、終了 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                        |
| HTTPファイル  | 開始 | アクセス可能なURL                                                                                                                                                                                              |


![console-guide-17](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-17.png)

環境設定で追加したビルドツールを使用すると、ビルドツールのビルドジョブを実行できます。実行するビルドジョブを選択すると、ビルドジョブのパラメータを追加で入力できます。

![console-guide-40](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-03.png)
**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。

ビルドツールで設定可能な**アーティファクト**

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクトの種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                       |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}  <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                         |
| Dockerイメージ | 開始    | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                         |
| HTTPファイル  | 開始、終了 | アクセス可能なURL                                                                                                                                                                                               |

ビルド設定が完了したら**次へ**をクリックします。

#### 配布設定

配布設定は、環境設定で追加した配布対象にコンテナイメージを配布する方法を設定します。

![console-guide-18](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-04.png)

ステージ名、配布対象、配布に使用するManifestを入力し、**次へ**をクリックします。 Manifestを作成する方法は[Kubernetes文書](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )を参照してください。

![console-guide-38](http://static.toastoven.net/prod_pipeline/2023-01-13/console-guide-02.png)

ビルド設定でタグフォーマットを使用した場合、ドッカー(Docker)イメージ入力部分にタグを上記のように`_{BUILD_NUMBER}`に入力します。イメージのタグに`_{BUILD_NUMBER}`が入力されている場合、最新の番号で入力されて配布されます。
タグフォーマットを使用するにはビルドステージおよびNHN Cloudビルドツールを設定する必要があります。

![console-guide-41](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-05.png)
NHN Cloudビルドツールで**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。
入力したマニフェストに**終了条件**と一致するKubernetsオブジェクトがないため、ステージが失敗した場合でも、マニフェストがKubernetesクラスタに適用される可能性があります。

配布設定で設定可能な**アーティファクト**

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクト種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                        |
|------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}   <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                          |
| Dockerイメージ | 開始 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                          |
| HTTPファイル  | 開始 | アクセス可能なURL                                                                                                                                                                                                |
| kubernetesオブジェクト | 終了 | オブジェクトの名前                                                                                                                                                                                                |

#### 最終検討とパイプラインの作成

最終検討ではパイプラインに設定した全ての入力内容を確認できます。

![console-guide-19](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-19.png)

入力した内容を確認し、**作成**をクリックします。

![console-guide-20](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-20.png)

### パイプラインの実行

パイプラインを実行する方法には手動実行と自動実行があります。

#### 手動実行

手動実行を使用した場合、ユーザーが望むときにパイプラインを実行できます。

![console-guide-21](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-21.png)

**パイプライン管理**で▶(手動実行)をクリックし、ダイアログボックスが表示されたら**確認**をクリックします。

#### 自動実行

自動実行を使用すると、GitHub Repositoryにイベントが発生したりイメージストアのコンテナイメージを更新した場合にパイプラインを自動的に実行するように設定できます。

![console-guide-22](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-22.png)

**自動実行設定**をクリックし、**自動実行設定**ダイアログボックスで**追加**をクリックします。

![console-guide-23](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-23.png)

GitHub Webフックを使用して、GitHubまたはGitHub EnterpriseのRepositoryにイベントが発生した場合にパイプラインを自動的に実行するように設定できます。自動実行タイプをGitHubに設定し、Repositoryの組織またはユーザー名、プロジェクト名、ブランチ、シークレットを入力し、**確認**をクリックします。

![console-guide-24](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-24.png)

GitHubまたはGitHub EnterpriseのRepositoryでWebフックを設定します。

| 項目 | 設定値 |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | パイプライン自動実行設定のシークレットに入力した値 |

![console-guide-35](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-02.png)

GitLab Webフックを使用して、GitLab Repositoryにイベントが発生した場合にパイプラインを自動的に実行するように設定できます。自動実行タイプをGitLabに設定し、Repositoryの組織またはユーザー名、プロジェクト名、ブランチを入力し、**確認**をクリックします。 GitLabシークレット設定は今後サポートする予定です。

![console-guide-36](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-03.png)
GitLab RepositoryでWebフックを設定します。

| 項目 | 設定値 |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push eventsチェック |
| Secret | 設定しない |
| SSL verification | Enable SSL verificationチェック |


![console-guide-37](http://static.toastoven.net/prod_pipeline/2022-07-26/console-guide-01.png)
GitLabのユーザー名で自動実行を設定したとき、GitLabのユーザー名とFull nameが異なる場合、自動実行が動作しない可能性がありますので、同じ値に設定する必要があります。


![console-guide-25](http://static.toastoven.net/prod_pipeline/2023-01-13/console-guide-03.png)

コンテナイメージを更新したときにパイプラインを自動的に実行するには、**自動実行タイプ**を**イメージストア**に設定します。
**イメージストア**を**環境設定**で登録した項目に選択したした後、**イメージ名**を入力します。イメージ名はNHN Cloud Container Registryの場合`registry名/イメージ名`の形式で入力します。
DockerHubの場合、`ドッカーハブアカウント/イメージ名`形式で入力します。**タグ**はJAVA正規表現式を使用でき、入力したタグとマッチするタグがpushされた場合に自動実行されます。
タグを入力しない場合、latestを除く新規タグがpushされる場合に自動実行されます。
入力が終わったら**確認**をクリックします。

![console-guide-26](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-26.png)

パイプラインを新しく作成したら、**自動実行防止**を **使用**に設定します。パイプラインを自動的に実行するには**自動実行防止**を**未使用**に変更する必要があります。パイプラインを選択した後、下部の基本情報の自動実行防止で**変更**をクリックします。自動実行防止設定ダイアログボックスで**未使用**を選択した後、**確認**をクリックします。

![console-guide-27](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-27.png)

実行中のパイプラインの詳細情報を確認するには、実行中のパイプラインを選択した後、下部の基本情報の最近の実行状態で**詳細情報**をクリックします。

### パイプライン管理

ユーザーはパイプラインを構成するステージを追加、変更、削除できます。

![console-guide-28](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-28.png)

パイプラインを選択した後、下部の**ステージ**をクリックすると、ステージ管理画面が表示されます。**ステージ追加**をクリックすると**ステージ追加**ダイアログボックスが表示されます。

![console-guide-29](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-29.png)

ステージ名、ステージタイプ、ステージタイプ別の入力値、以前の段階を設定した後、**ステージ追加**をクリックしてパイプラインにステージを追加できます。 Pipelineはアプリケーション配布フローを構成するときに使用できるさまざまなステージタイプを提供します。

![console-guide-30](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-30.png)

以前のステージを選択する方式に基づいてステージを並列に実行できます。並列構成したステージのうち1つが失敗すると、残りのステージは実行がキャンセルされ、パイプラインの実行は失敗します。

### 開発環境設定

開発環境設定を使用すると、Kubernetesの使用方法を知らないユーザーもKubernetesにコンテナイメージを配布できます。

![console-guide-31](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-31.png)

**開発環境設定**で**開発環境の作成**をクリックします。 

![console-guide-32](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-32.png)

開発環境名と開発環境の説明を入力し、基本イメージから配布するコンテナイメージを選択します。コンテナイメージのアクセスに必要な情報はイメージストアに設定します。配布対象はコンテナイメージを配布するKubernetesを選択します。サービスポートはコンテナが提供するサービスのポートを入力します。サービスポートを入力すると、コンテナサービスにアクセスできるサービスIPを自動的に割り当て(KubernetesがLoadBalancerタイプのサービスを提供する場合)ます。最後に開発環境の制約事項を入力して**作成**をクリックすると開発環境を作成します。

![console-guide-33](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-33.png)

開発環境の作成中は**開発環境の状態**は**作成中**と表示されます。

![console-guide-34](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-34.png)

開発環境の作成が完了すると、**開発環境の状態**が**実行中**に変更されます。サービスIPとサービスポートを使用してコンテナサービスにアクセスできます。
