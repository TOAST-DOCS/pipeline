## Dev Tools > Pipeline > コンソール使用ガイド > Pipeline Management

パイプラインは、1つ以上のステージで構成されたアプリケーション配布フローを定義します。

### パイプラインの構成

#### パイプラインの作成

**パイプラインの作成**をクリックしてパイプラインを作成することができ、パイプラインテンプレートファイルをアップロードしてパイプラインを作成することもできます。
![pipeline-management-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-01.png)


**パイプライン管理**で**+パイプライン作成**をクリックします。

![pipeline-management-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-02.png)

**パイプライン作成**モーダルウィンドウで**パイプライン名**と**パイプラインの説明**を入力し、**確認**をクリックします。

または、パイプラインテンプレートファイルでパイプラインを作成することもできます(パイプラインテンプレートはJSONファイルを使用します)。

![pipeline-management-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-03.png)

パイプラインテンプレートファイルをアップロードした後、**確認**をクリックします。

#### パイプラインスタジオ

パイプラインスタジオは、ユーザーがパイプラインの基本情報を管理したり、パイプラインを構成するステージを追加、変更、削除することができるページです。

![pipeline-studio-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-1.png)

パイプラインスタジオの上部には、パイプラインの名前、説明、最終修正日、コンストラクタの基本情報が表示されます。

パイプラインスタジオパネルでは、そのパイプラインを構成するステージを確認できます。

#### 編集モード
![pipeline-studio-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-2.png)

右上の**編集モード**トグルをクリックして編集モードに入ることができます。編集モードでは、ステージの追加、変更、削除、位置変更を行うことができます。

#### ステージの追加
![pipeline-studio-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-3.png)

**編集モード**を有効にすると、左側にアプリケーション配布フローを構成する際に使用できる様々なステージで構成された**ソース**、**ビルド**、**配布**、**機能**のグループが表示されます。

4つのグループから追加するステージを選択し、ドラッグ＆ドロップで画面に追加できます。

![pipeline-studio-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-4.png)

ステージが追加されたら、そのステージを選択して必要な情報を入力します。

![pipeline-studio-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-5.png)

以前に実行するステージと追加するステージを接続して実行順序を設定します。

![pipeline-studio-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-6.png)

右上の**パイプライン保存**をクリックしてステージの追加を完了できます。

#### ステージの編集
![pipeline-studio-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-7.png)

**編集モード**を有効にした後、編集したいステージをクリックしてステージを編集できます。

![pipeline-studio-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-9.png)

編集を完了した後、右上の**パイプラインを保存**をクリックしてステージの編集を完了できます。

#### ステージの削除
![pipeline-studio-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-10.png)

![pipeline-studio-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-11.png)

**編集モード**を有効にした後、削除したいステージの右上の**X**をクリックしてステージを削除できます。

![pipeline-studio-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-12.png)

削除後、右上の**パイプライン保存**をクリックしてステージの削除を完了できます。

### パイプラインの実行

パイプラインは手動または自動で実行できます。

#### 手動実行

手動実行を使用すると、ユーザーが好きな時にパイプラインを実行できます。

![pipeline-management-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-12.png)

**パイプライン管理**で**▶︎実行**をクリックし、**パイプライン実行**モーダルウィンドウが表示されたら内容を確認し、**確認**をクリックします。

#### 自動実行

自動実行を使うと、GitHubまたはGitLabリポジトリにイベントが発生したり、イメージストアのコンテナイメージを更新すると、パイプラインを自動で実行するように設定できます。

![management-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-04.png)
![management-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-05.png)

**自動実行設定**をクリックした後、**自動実行設定**モーダルウィンドウで**追加**をクリックします。


* GitHub自動実行設定
![management-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-06.png)



GitHub Webフックを使用してGitHubまたはGitHub Enterpriseのリポジトリにイベントが発生すると、パイプラインを自動で実行するように設定できます。**自動実行タイプ**を **GitHub**に設定し、リポジトリの**組織名またはユーザー名**、**プロジェクト名**、**ブランチまたはタグ**、**シークレット**を入力して**確認**をクリックします。

タグで自動実行を設定するには、**ブランチまたはタグ**項目に`refs/tags/タグ名`のようにタグ名を入力します。`タグ名`部分にはJAVA正規表現を使用できます。

タグで自動実行を設定した後、NHN Cloudビルドツール使用時に設定されたタグでビルドを実行します。ビルド - Jenkinsステージでタグでビルドを実行するためには次のように設定する必要があります。

Jenkinsで次のようにパラメータを設定します。
![pipeline-guide-39.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-39.png)
![pipeline-guide-40.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-40.png)


Pipelineのビルドツール設定で**ビルドジョブパラメータ**に次のように入力します。

![management-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-10.png)

* GitHub Webフック設定値

![pipeline-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-16.png)


| 項目 | 設定値 |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | パイプライン自動実行設定のシークレットに入力した値 |
| event | push event, create event(タグを使用する場合) |

特定のファイルがPushされた時だけ自動実行するように設定できます(最大5つまで)。

![management-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-13.png)

**ソースリポジトリ名**は環境設定で登録したソースリポジトリを選択します。
**GitHubファイルパス**は、選択したソースリポジトリのファイルを含むパスを入力します。

* GitLab自動実行設定

![management-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-07.png)

GitLab Webフックを使用して、GitLabリポジトリにイベントが発生するとパイプラインを自動で実行するように設定できます。**自動実行タイプ**を**GitLab**に設定し、リポジトリの**組織名またはユーザー名**、**プロジェクト名**、**ブランチまたはタグ**を入力して**確認**をクリックします。GitLabシークレット設定は後日サポートする予定です。

* GitLab Webフック設定値

![pipeline-guide-18](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-18.png)


| 項目 | 設定値 |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push eventsチェック |
| Secret | 設定しない |
| SSL verification | Enable SSL verificationチェック |

* GitLab Webフック設定時の注意事項

GitLabのユーザー名で自動実行を設定する場合、ユーザー名をGitLabのユーザー名と同じに設定する必要があります。ユーザー名が違う場合、自動実行が動作しない場合があります。

![pipeline-guide-19](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-19.png)

* イメージストア自動実行設定

![management-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-08.png)

コンテナイメージを更新した時、パイプラインを自動で実行するには、**自動実行タイプ**を **イメージストア**に設定します。
**イメージリポジトリ**を**環境設定**で登録した項目として選択し、**イメージ名**を入力します。イメージ名はNHN Cloud Container Registryの場合`registry名/イメージ名`の形で入力します。
Docker Hubの場合`Docker Hubアカウント/イメージ名`の形式で入力します。 **タグ**はJAVA正規表現を使用することができ、入力したタグとマッチングするタグがpushされた場合、自動実行されます。
タグを入力しない場合、latestを除く新規タグがpushされた場合、自動実行されます。
入力が終わったら**確認**をクリックします。

![management-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-09.png)

パイプラインを新規作成すると、**自動実行**のトグルスイッチがオフの状態で適用されます。パイプラインを自動で実行するには、**自動実行**のトグルスイッチをクリックして有効にする必要があります。

### パイプライン管理

ユーザーはパイプラインの基本情報を修正できます。
![pipeline-studio-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-13.png)

パイプライン名の横にある修正アイコンをクリックして、パイプラインの名前と説明を修正できます。

情報を修正した後、**確認**をクリックして修正を完了できます。

![pipeline-studio-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-14.png)

**▶手動実行**をクリックして該当パイプラインを実行することができ、**■実行停止**をクリックして実行中のパイプラインを停止できます。


#### 最近の実行情報を確認

パイプラインの最近の実行に関する各ステージの基本情報と実行状態を確認するには、**最近の実行情報**をクリックします。

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-16.png)

#### パイプラインJSONダウンロード

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-03-25/guide-17.png)

**パイプラインバージョン**をクリックしてJSON形式でパイプラインを確認できます。

左上のパイプライン修正日が表示されたドロップダウンボタンをクリックして修正日別に確認できます。

右上の**パイプラインテンプレートのダウンロード**をクリックしてJSONファイルとして保存できます。

#### パイプライン通知
パイプラインの開始、完了、失敗に対するEmail、SMS通知を管理する機能です。

![pipeline-management-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-03-25/pipeline-management-guide-13.png)

**パイプライン通知**をクリックして通知を設定できます。

**プロジェクト設定** > **通知管理**で通知受信者の管理が可能です。

通知受信対象及び通知方法(Email, SMS)の設定は[通知管理ガイド](https://docs.nhncloud.com/ja/nhncloud/ja/console-guide/#_31)を参照してください。
