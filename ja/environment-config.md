## Dev Tools > Pipeline > コンソール使用ガイド > Environment Configuration

### 環境設定

Pipelineは、アプリケーション配布フローを構成するとき、さまざまな外部システムを使用します。環境設定でPipelineが使用する外部システムを追加できます。

Pipelineに追加できる外部システムは次のとおりです。
- ソースリポジトリ
- イメージストア
- ビルドツール
- 配布対象

### ソースリポジトリ

ソースリポジトリを追加すると、NHN Cloudビルドツールを使用してソースコードをビルドできます。 GitHub、GitLab、GitHub Enterpriseなどのgitコマンドを使用してアクセスできるリポジトリを追加できます。

![env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-01.png)

**環境設定**で**ソースリポジトリ設定**をクリックすると、ソースリポジトリを管理する画面に移動します。**ソースリポジトリ追加**をクリックして新規ソースリポジトリを追加できます。

![env-config-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-10-29/env-config-guide-02.png)

ソースリポジトリ情報を入力し、**ソースリポジトリ接続確認**の**確認**をクリックします。接続確認後に**確認**をクリックします。
- GitHubソースリポジトリのトークン発行時、`repo`権限が必要です。
- GitLabソースリポジトリのトークン発行時、`read_user`、`api`、`read_api`権限が必要です。

![env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-03.png)

### イメージストア

イメージストアを追加すると、認証情報が必要なイメージストアにアクセスするときに使用できます。 NHN Cloudビルドツールでソースコードをビルドするコンテナを作成するときや、新たに作成したコンテナイメージをアップロードするときに使用できます。そしてパイプライン自動実行設定で自動実行を実行させるコンテナイメージを設定するときに使用できます。イメージストアにはNHN Cloud Container Registry、Docker Hubの他にプライベートイメージストアを追加できます。 Docker Hubを使用する場合はイメージストアURLを省略できます。

![env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-04.png)

**環境設定**で**イメージストア設定**をクリックすると、イメージストアを管理する画面に移動します。**イメージストア追加**をクリックして新規ソースリポジトリを追加できます。

![env-config-guide-05](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-05.png)

イメージストア情報を入力し、**イメージストア接続確認**の**確認**をクリックします。接続確認後に**確認**をクリックします。イメージストアURLを入力していない場合はDocker Hubとして動作します。

![env-config-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-06.png)

### ビルドツール

ビルドツールを追加すると、パイプラインでビルドツールに定義したさまざまなジョブを使用できます。ビルドツールにはJenkinsを追加できます。`NHN Cloudビルドツール`を使用する場合はビルドツールの追加作業を省略できます。

![env-config-guide-07](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-07.png)

**環境設定**で**ビルドツール設定**をクリックすると、ビルドツールを管理する画面に移動します。**ビルドツール追加**をクリックして新規ビルドツールを追加できます。

![env-config-guide-08](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-08.png)

ビルドツール情報を入力し、**ビルドツール接続確認**の**確認**をクリックします。接続確認後に**確認**をクリックします。

![env-config-guide-09](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-09.png)

### 配布対象

配布対象を追加すると、パイプラインで配布対象を管理できます。配布対象にコンテナイメージを配布したり、実行中のコンテナを変更できます。配布対象にはNHN Cloud Container、Kubernetesを追加できます。

![env-config-guide-10](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-10.png)

**環境設定**で**配布対象設定**をクリックすると、配布対象を管理する画面に移動します。**配布対象追加**をクリックして新規配布対象を追加できます。

![env-config-guide-11](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-11.png)

配布対象の名前と説明を入力し、Kubeconfigファイルを選択して**配布対象接続確認**の **確認**をクリックします。接続確認後に**確認**をクリックします。

![env-config-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-12.png)

### チャートリポジトリ

チャートリポジトリを追加すると、**ビルド - Bake (Manifest)**ステージを使用してHelmチャートをビルドできます。[チャートリポジトリガイド](https://helm.sh/docs/topics/chart_repository/)でチャートリポジトリの構成方法を確認できます。

![env-config-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-13.png)

**環境設定**で**チャートリポジトリ設定**をクリックすると、チャートリポジトリを管理する画面に移動します。**チャートリポジトリ追加**をクリックして新規チャートリポジトリを追加できます。

![env-config-guide-14](http://static.toastoven.net/prod_pipeline/2024-04-23/env-config-guide-14.png)

チャートリポジトリ情報を入力した後、**チャートリポジトリ接続確認**の**確認**をクリックします。接続確認後、**確認**をクリックします。

![env-config-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-15.png)

### NHN Cloudセキュリティ設定

#### User Access Key ID, Secret Access Key作成

コンソール右上のID領域をクリックすると、次のような**APIセキュリティ設定**メニューを確認できます。

![env-config-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-16.png)

**APIセキュリティ設定**で**User Access Key ID**作成をクリックして、NHN Cloudセキュリティ設定を登録する際に入力が必要な**User Access Key ID**と**Secret Access Key**を作成できます。

![env-config-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-17.png)

![env-config-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-18.png)

**User Access Key ID**、**Secret Access Key**を作成すると、次のような**秘密鍵発行完了**画面が表示されます。秘密鍵はポップアップ画面で1度しか表示されないため、忘れないよう記録して使用します。

![env-config-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-19.png)

セキュリティ設定を登録する際に必要な**User Access Key ID**は、秘密鍵発行完了ポップアップを閉じると確認できます。

#### NHN Cloudセキュリティ設定登録
NHN Cloudセキュリティ設定を追加すると**機能 - NHN Cloud Deployサービス**ステージを使用し、NHN Cloud Deployサービスを通じて配布できます。

![env-config-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-20.png)

**環境設定** > **NHN Cloudセキュリティ設定**画面で**+セキュリティ設定追加**をクリックして新規セキュリティ設定を追加できます。

![env-config-guide-21](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-21.png)

NHN Cloudセキュリティ設定情報を入力し、**API正常呼び出し確認**の**確認**をクリックします。接続確認後**確認**をクリックします。

![env-config-guide-22](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/env-config-guide-22.png)

### Pipeline IP
Pipelineと連動したシステムが正常に動作しない場合はACLを確認してください。Pipelineが使用するIPアドレスは**211.56.1.0/27**です。

| サービス | CIDR            |
|---|-----------------|
| Pipeline | 211.56.1.0/27<br/>101.79.92.0/24 |
