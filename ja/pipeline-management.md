## Dev Tools > Pipeline > コンソール使用ガイド > Pipeline Management

### パイプラインの作成

Pipelineはアプリケーション配布フローを1つ以上のステージで構成したパイプラインとして保存します。パイプライン作成では**ソースコードのビルド** > **コンテナイメージの作成** > **コンテナイメージのアップロード**、**コンテナイメージの配布**の順序で動作する基本的なパイプラインを作成でき、パイプラインテンプレートファイルをアップロードしてパイプラインを作成することも可能です。

![pipeline-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-01.png)

**パイプライン管理**で**パイプライン作成**をクリックします。パイプラインの作成は、次の手順で進めます。
- パイプライン情報の入力
- ソース設定
- ビルド設定
- 配布設定
- 最終検討およびパイプラインの作成

#### パイプライン情報の入力

パイプラインの基本情報を入力します。

![pipeline-guide-33](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-33.png)

パイプライン名、パイプラインの説明を入力し、 **次へ**をクリックします。

追加でパイプラインテンプレートファイルでパイプラインを作成することも可能です(パイプラインテンプレートファイルはJSONファイルを使用します)。

![pipeline-guide-34](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-34.png)

パイプライン名、パイプラインの説明を入力し、パイプラインテンプレートファイルをアップロードして**次へ**をクリックします。

#### ソース設定

NHN Cloudビルドツールでソースコードをビルドするときに使用するソースリポジトリを設定します。 NHN Cloudビルドツールを使用しない場合や、NHN Cloudビルドツールでソースコードをビルドしない場合は省略できます。

![pipeline-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-03.png)

ステージ名、環境設定で登録したソースリポジトリ、ソースコードをビルドする対象ブランチ(git branch)を入力し、**次へ**をクリックします。

#### ビルド設定

ビルド設定では、NHN Cloudビルドツールや、環境設定で登録したビルドツールを使用できます。ステージ名を入力し、**ビルドツール**で使用するビルドツールを選択します。

![pipeline-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-04.png)

NHN Cloudビルドツールを使用すると、別途ソフトウェアをインストールせずにソースリポジトリに保存したアプリケーションソースコードをビルドし、ビルドしたアプリケーションでコンテナイメージを作成し、作成したコンテナイメージをイメージストアにアップロードできます。
**ビルド環境設定**には**ソース設定**で設定したソースコードを使用してアプリケーションをビルドする方法を入力します。ソースコードのビルドに使用するコンテナイメージ、ビルドマシンの性能、ビルドに使用するコマンドを入力できます。
**ビルド結果設定**にはビルドしたアプリケーションでコンテナイメージを作成する方法を入力します。コンテナイメージを作成するときに使用するDockerfile、作成したコンテナイメージをアップロードするイメージストア、アップロードするコンテナイメージの名前とタグを入力できます。
**タグフォーマット使用**チェックボックスをクリックするとイメージタグフォーマットを使用できます。イメージタグフォーマットを使用すると、作成されたイメージのタグをNHN Cloudビルドツールで付与するビルド番号として使用します。作成されるタグは`_{BUILD_NUMBER}`形式で、BUILD_NUMBERがビルド番号です。
ビルド番号はビルドごとに増加する数字型のデータです。イメージタグフォーマット使用時にはタグが`_{BUILD_NUMBER}`形式で固定されます。

![pipeline-guide-05](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-05.png)
NHN Cloudビルドツールで**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。

#### NHN Cloudビルドツールで設定可能なアーティファクト

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクトの種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                      |
|------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path} <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                        |
| Dockerイメージ | 開始、終了 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                        |
| HTTPファイル  | 開始 | アクセス可能なURL                                                                                                                                                                                              |


![pipeline-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-06.png)

環境設定で追加したビルドツールを使用すると、ビルドツールのビルドジョブを実行できます。実行するビルドジョブを選択すると、ビルドジョブのパラメータを追加で入力できます。

![pipeline-guide-07](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-07.png)
**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。

#### ビルドツールで設定可能なアーティファクト

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクトの種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                       |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}  <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                         |
| Dockerコンテナイメージ | 開始  | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                         |
| HTTPファイル  | 開始、終了 | アクセス可能なURL                                                                                                                                                                                               |

ビルド設定が完了したら**次へ**をクリックします。

#### 配布設定

環境設定で追加した配布対象にコンテナイメージを配布する方法を設定します。<br>
**Manifestソース**は**text**または**artifact**を選択できます。<br>
設定方法は次のとおりです。

![pipeline-guide-08](http://static.toastoven.net/prod_pipeline/2024-01-23/pipeline-guide-08.png)

"text"を選択する場合：ステージ名、配布対象、配布に使用するKubernetes Manifestを入力し、**次へ**をクリックします。Manifestを作成する方法は[Kubernetes文書](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )を参照してください。

![pipeline-guide-09-01](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-09.png)

"artifact"を選択する場合："アーティファクト定義"にあるリポジトリタイプ、ソースリポジトリ、パス、ブランチ名を入力し、**次へ**をクリックします。

![pipeline-guide-09-02](https://static.toastoven.net/prod_pipeline/2024-01-23/pipeline-guide-09-02.png)

ビルド設定でタグフォーマットを使用した場合、ドッカー(Docker)イメージ入力部分にタグを上記のように`_{BUILD_NUMBER}`に入力します。イメージのタグに`_{BUILD_NUMBER}`が入力されている場合、最新の番号で入力されて配布されます。
タグフォーマットを使用するにはビルドステージおよびNHN Cloudビルドツールを設定する必要があります。

![pipeline-guide-10](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-10.png)
NHN Cloudビルドツールで**アーティファクト**設定を使用して**開始条件**と**終了条件**を設定できます。
開始条件として設定された**アーティファクト**はステージ開始時に存在有無を確認してステージの進行を決定します。
終了条件として設定された**アーティファクト**はステージの生産物を**アーティファクト**に設定します。
入力したマニフェストに**終了条件**と一致するKubernetesオブジェクトがないため、ステージが失敗した場合でも、マニフェストがKubernetesクラスタに適用される可能性があります。

#### 配布設定で設定可能なアーティファクト

GitHubおよびGitLabはブランチを入力しない場合、masterブランチをデフォルト値として使用します。

| アーティファクト種類  | 使用条件 | パスまたはリファレンス設定例                                                                                                                                                                                        |
|------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHubファイル | 開始    | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}   <br/> GitHub Enterpriseの場合の例：https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLabファイル | 開始    | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                          |
| Dockerコンテナイメージ | 開始 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                          |
| HTTPファイル  | 開始 | アクセス可能なURL                                                                                                                                                                                                |
| kubernetesオブジェクト | 終了 | オブジェクトの名前                                                                                                                                                                                                |

#### 最終検討とパイプラインの作成

最終検討ではパイプラインに設定した全ての入力内容を確認できます。

![pipeline-guide-11](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-11.png)

パイプラインテンプレートファイルで作成した場合は、アップロードしたファイル名を確認できます。

![pipeline-guide-35](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-35.png)


入力した内容を確認し、**作成**をクリックします。

![pipeline-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-12.png)

### パイプラインの実行

パイプラインを実行する方法には手動実行と自動実行があります。

#### 手動実行

手動実行を使用した場合、ユーザーが望むときにパイプラインを実行できます。

![pipeline-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-13.png)

**パイプライン管理**で▶(手動実行)をクリックし、ダイアログボックスが表示されたら**確認**をクリックします。

#### 自動実行

自動実行を使用すると、GitHubまたはGitLabリポジトリにイベントが発生したりイメージストアのコンテナイメージを更新した場合にパイプラインを自動的に実行するように設定できます。

![pipeline-guide-14](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-14.png)

**自動実行設定**をクリックし、**自動実行設定**ダイアログボックスで**追加**をクリックします。


#### GitHub自動実行設定
![pipeline-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-15.png)

GitHub Webフックを使用してGitHubまたはGitHub Enterpriseのリポジトリにイベントが発生した場合にパイプラインを自動的に実行するように設定できます。自動実行タイプをGitHubに設定し、リポジトリの組織またはユーザー名、プロジェクト名、ブランチ、シークレットを入力し、**確認**をクリックします。
タグで自動実行を設定するには、**ブランチまたはタグ**項目に「refs/tags/タグ名」のようにタグ名を入力します。「タグ名」部分にはJAVA正規表現を使用できます。
タグで自動実行を設定したらNHN Cloudビルドツールを使用する際に設定されたタグでビルドを実行します。ビルド-Jenkinsステージでタグでビルドを実行したい場合は、次のような設定が必要です。

Jenkinsで次のようにパラメータを設定します。
![pipeline-guide-39.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-39.png)
![pipeline-guide-40.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-40.png)
Pipelineのビルドツール設定で**ビルドジョブパラメータ**に次のように入力します。
![pipeline-guide-41.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-41.png)

#### GitHub Webフック設定値

![pipeline-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-16.png)


| 項目 | 設定値 |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | パイプライン自動実行設定のシークレットに入力した値 |
| event | push event、create event(タグ使用時) |


**特定ファイル**が**Push**された場合のみ自動実行されるように設定できます。(最大5個)

![pipeline-guide-33](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/pipeline-guide-33.png)

**ソースリポジトリ名**は環境設定で登録したソースリポジトリを選択します。
**ファイルパス**は選択したソースリポジトリからファイルが含まれるパスを入力します。

#### GitLab自動実行設定

![pipeline-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-03-28/pipeline-guide-17.png)

GitLab Webフックを使用してGitLaリポジトリにイベントが発生した場合にパイプラインを自動的に実行するように設定できます。自動実行タイプをGitLabに設定し、リポジトリの組織またはユーザー名、プロジェクト名、ブランチを入力し、**確認**をクリックします。GitLabシークレット設定は今後サポートする予定です。

#### GitLab Webフック設定値

![pipeline-guide-18](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-18.png)


| 項目 | 設定値 |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push eventsチェック |
| Secret | 設定しない |
| SSL verification | Enable SSL verificationチェック |

#### GitLab Webフック設定時の注意事項

GitLabのユーザー名で自動実行を設定する場合、ユーザー名をGitLabのユーザー名と同じに設定する必要があります。ユーザー名が異なる場合、自動実行が動作しない場合があります。

![pipeline-guide-19](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-19.png)

#### イメージストア自動実行設定

![pipeline-guide-20](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-20.png)

コンテナイメージを更新したときにパイプラインを自動的に実行するには、**自動実行タイプ**を**イメージストア**に設定します。
**イメージストア**を**環境設定**で登録した項目に選択したした後、**イメージ名**を入力します。イメージ名はNHN Cloud Container Registryの場合`registry名/イメージ名`の形式で入力します。
Docker Hubの場合、`Docker Hubアカウント/イメージ名`の形式で入力します。**タグ**はJAVA正規表現を使用でき、入力したタグとマッチするタグがpushされた場合に自動実行されます。
タグを入力しない場合、latestを除く新規タグがpushされる場合に自動実行されます。
入力が終わったら**確認**をクリックします。

![pipeline-guide-21](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-21.png)

パイプラインを新しく作成したら、**自動実行防止**が基本的に適用されます。パイプラインを自動的に実行するには**自動実行防止**を**未使用**に変更する必要があります。パイプラインを選択した後、下部の基本情報の自動実行防止で**変更**をクリックします。自動実行防止設定ダイアログボックスで**未使用**を選択した後、**確認**をクリックします。

![pipeline-guide-22](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-22.png)

実行中のパイプラインの詳細情報を確認するには、実行中のパイプラインを選択した後、下部の基本情報の最近の実行状態で**詳細情報**をクリックします。

#### 実行履歴

パイプラインを手動実行、自動実行した場合は、実行履歴タブで実行履歴を確認できます。

![pipeline-guide-26](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-26.png)

### パイプライン管理

ユーザーはパイプラインを構成するステージを追加、変更、削除できます。

![pipeline-guide-23](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-23.png)

パイプラインを選択した後、下部の**ステージ**をクリックすると、ステージ管理画面が表示されます。**ステージ追加**をクリックすると**ステージ追加**ダイアログボックスが表示されます。

![pipeline-guide-24](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-24.png)

ステージ名、ステージタイプ、ステージタイプ別の入力値、以前の段階を設定した後、**ステージ追加**をクリックしてパイプラインにステージを追加できます。 Pipelineはアプリケーション配布フローを構成するときに使用できるさまざまなステージタイプを提供します。

![pipeline-guide-25](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-25.png)

以前のステージを選択する方式に基づいてステージを並列に実行できます。並列構成したステージのうち1つが失敗すると、残りのステージは実行がキャンセルされ、パイプラインの実行は失敗します。

#### パイプラインJSON修正およびダウンロード
JSON修正によりパイプラインを変更できます。 

![pipeline-guide-36](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-36.png)

**JSONを表示**をクリックして、JSON形式でパイプラインを確認できます。

![pipeline-guide-37](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-37.png)

**パイプラインテンプレートのダウンロード**をクリックして、JSONファイルで保存できます。

**編集**をクリックして、画面でJSONファイルを直接修正できます。

![pipeline-guide-38](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-38.png)

修正後**確認**をクリックすると、修正された内容がパイプラインに反映されます。ただし、入力値が誤っている場合、エラーメッセージが表示されます。

#### 実行履歴と作業

実行履歴で実行履歴の確認とJudgementステージの実行設定選択、ステージ実行停止/ステージ実行の決定を行います。

![pipeline-guide-26](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-26.png)

実行履歴で現在実行中のパイプライン履歴を選択すると、次のように実行中のステージ情報が表示されます。

![pipeline-guide-27](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-27.png)


実行中のパイプラインステージのうちJudgementステージが選択待機中の場合、**管理**ボタンが表示され、そのボタンを押すと次のようなポップアップが表示され、ステージ追加、変更時に入力した**説明**、**実行設定**の値と**ステージ実行停止/ステージ実行**を選択できます。

![pipeline-guide-28](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-28.png)
![pipeline-guide-29](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-29.png)
![pipeline-guide-30](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-30.png)

実行設定値を入力しなかった場合、実行設定選択せずに**ステージ実行停止/ステージ実行**だけを選択します。

![pipeline-guide-31](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-31.png)

ユーザーが選択したステージの設定通りに実行され、実行履歴は5秒ごとに更新されます。

![pipeline-guide-32](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-32.png)

ステージの実行停止を選択すると、該当ブランチの実行が停止され、実行中のステージのキャンセルは選択したパイプラインの実行全体がキャンセルされます。
