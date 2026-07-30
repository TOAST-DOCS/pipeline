<!-- pre-align:aligned sig=188fdbf35804 -->

<a id="dev-tools-pipeline-overview"></a>
## Dev Tools > Pipeline > 概要 { #dev-tools-pipeline-overview }
Pipelineは、ソースコードのビルド、コンテナイメージの作成、コンテナイメージの配布など、アプリケーション配布フローを管理することができる継続的な配布(continuous deployment)サービスです。

<a id="main-features"></a>
### 主な機能 { #main-features }
* NHN Cloudビルドツール
* Jenkins連動
* Kubernetes連動
* アプリケーション配布フロー管理
* アプリケーション配布の自動化
* 承認機能

<a id="feature-description"></a>
### 機能説明 { #feature-description }
Pipelineは、ユーザーがアプリケーションの配布に使用することができるさまざまな機能を提供します。

<a id="feature-description-nhn-cloud-build-tool"></a>
#### NHN Cloudビルドツール
Pipelineは、ソースコードのビルドとコンテナイメージの作成に使用することができるNHN Cloudビルドツールを提供します。 NHN Cloudビルドツールを使用すると、別途のソフトウェアをインストールせずにソースリポジトリに保存したアプリケーションソースコードをビルドし、ビルドしたアプリケーションでコンテナイメージを作成し、作成したコンテナイメージをイメージストアにアップロードできます。

<a id="feature-description-jenkins-integration"></a>
#### Jenkins連動

PipelineにJenkinsを連動してJenkinsジョブを追加できます。ユーザーが定義したさまざまなJenkinsジョブをアプリケーションの配布に活用できます。

<a id="feature-description-kubernetes-integration"></a>
#### Kubernetes連動

PipelineにKubernetesを連動してKubernetesジョブを追加できます。コンテナイメージの配布、 Podレプリカ数の変更、Kubernetesオブジェクトの削除など、さまざまな機能を提供します。

<a id="feature-description-application-deployment-flow-management"></a>
#### アプリケーション配布フローの管理

ソースコードのビルド、コンテナイメージの作成、コンテナイメージのアップロード、コンテナイメージの配布など、アプリケーションの配布に必要な複数のステップ(ステージ)を自由に定義してパイプラインとして保存できます。保存されたパイプラインはいつでも再実行できます。

<a id="feature-description-application-deployment-automation"></a>
#### アプリケーション配布の自動化

パイプラインに自動実行を設定できます。ソースリポジトリのソースコードを変更するか、イメージストアのコンテナイメージを更新するとパイプラインを自動的に実行します。

<a id="feature-description-approval-feature"></a>
#### 承認機能

パイプラインの承認管理ステージを通じて、承認権者の承認なしで以降のステージが実行されないように管理します。

<a id="feature-description-artifact"></a>
#### アーティファクト

アーティファクト(artifact)はDockerコンテナイメージ、設定ファイルなど外部のリソースをパイプライン構成で扱う時に使用する概念です。パイプラインで使用する外部リソースをアーティファクトに指定してステージの開始/終了条件として使用できます。

<a id="feature-description-artifact-type"></a>
#### アーティファクト種類
| 種類      | 説明              |
|-----------|-------------------|
| GitHubファイル | GitHubリポジトリにあるファイル |
| GitLabファイル | GitLabリポジトリにあるファイル |
| HTTPファイル | URLにアクセスできるファイル |
| Dockerイメージ | イメージストアにあるイメージ |
|Kubernetesオブジェクト| Kubernetesクラスタに作成されたオブジェクト|

<a id="glossary"></a>
### 用語説明 { #glossary }
| 用語 | 説明 |
|---|---|
| Pipeline | NHN Cloudの継続的な配布サービス |
| パイプライン | アプリケーション配布フローを保存するオブジェクト |
| ステージ | パイプラインを構成する各配布ステップ |
| NHN Cloudビルドツール | Pipelineが基本提供するビルドツール |
