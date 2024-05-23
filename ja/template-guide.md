## Dev Tools > Pipeline > コンソール使用ガイド > テンプレートガイド
テンプレートガイドでは、テンプレートファイルを利用してパイプラインを作成する方法を説明します。

## 既存のパイプラインと同じパイプラインの作成
すでに構成されているパイプラインからJSONファイルをダウンロードした後、同じ形式の新規パイプラインを作成する方法です。

### 1. 既存のパイプラインJSONファイルをダウンロード
既存のパイプラインを選択して基本情報の**JSONを表示**>**パイプラインテンプレートをダウンロード**の手順でJSONファイルをダウンロードできます。
![template-guide-01](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-01.png)

### 2. テンプレートファイルでパイプラインを作成
##### 2.1パイプライン管理でパイプライン作成をクリックします。ダウンロードしたJSONファイルをアップロードします。アップロード後、「次へ」をクリックすると、すぐに最終確認段階に進みます。
![template-guide-02](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-02.png)

##### 2.2最終確認段階で登録されたファイル名の確認が可能で、作成をクリックするとパイプラインが作成されます。
![template-guide-03](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-03.png)
![template-guide-04](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-04.png)

## サンプルシナリオテンプレートでパイプラインを作成
シナリオごとにサンプルテンプレートファイルを提供して、簡単にパイプラインを作成できます。

希望するシナリオにあるJSONファイルをダウンロードすると、中括弧(`{}`)で要求するデータ全体を入力して使用できます。特に`[環境設定]`の接頭辞が付くデータの場合、**Pipeline > 環境設定**にあるデータを使用するため、データが登録されている必要があります。[Pipelineユーザーガイド](/Dev%20Tools/Pipeline/ko/environment-config/#_1)で登録方法を確認できます。

Bake Stageの使用に関するサンプルシナリオテンプレートは、機能変更が必要であり、後日提供される予定です。

### 1. ソース - ビルド - 配布段階の基本的なシナリオ
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-01.json)

Githubからソースコードを取得してNHN Cloudビルドツールでビルド後、対象サーバーにManifest情報で配布するシナリオです。

![template-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-08.png)

登録されているJSONファイルをダウンロード後、中括弧で表示されたデータに対する情報を入力する必要があります。

#### ソースステージ
ソースステージのうちGithubを基準にガイドが作成されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_1)でステージの詳細ガイドが確認できます。

``` json
{
    "type": "githubSource",
    "name": "source",
    "refId": "1",
    "requisiteStageRefIds": [],
    "sourceRepo": "{[環境設定]ソースリポジトリ設定に保存されたソースリポジトリ名}",   
    "branch": "{配布対象ブランチ}"  
},
```

`"sourceRepo": "{ソースリポジトリ設定に保存されたソースリポジトリ名}"`で入力値を要求しており、**環境設定**内のソースリポジトリ設定に登録した情報の中で使用するソースリポジトリ名を確認し、`"sourceRepo": "github-pipeline"`のように修正が必要です。

![template-guide-05](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-05.png)

**イメージストア設定**、**配布対象設定**と同じように設定された名前の確認後、修正が必要です。

#### ビルドステージ
ビルドステージのうちNHN Cloudビルドツールを基準にガイドが作成されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_2)でステージの詳細ガイドが確認できます。

``` json
{
    "type": "imageBuild",
    "name": "build",
    "refId": "2",
    "requisiteStageRefIds": [
        "1"
    ],
    "buildImageRegistry": "{[環境設定]イメージストア設定に保存されたイメージストア名}",    
    "buildImageName": "{イメージ名}",  
    "buildImageTag": "{イメージタグ}",   
    "buildCommand": "{ビルドコマンド}",    
    "dockerfilePath": "{Dockerfileパス}",  
    "buildWorkDir": "",   
    "pushImageRegistry": "{[環境設定]ビルド結果がアップロードされるイメージストア設定に保存されたイメージストア名}",  
    "pushImageName": "{ビルド結果イメージ名}", 
    "pushImageTag": "{ビルド結果イメージタグ}",  
    "buildFlavorName": "c2m4",  
    "buildTimeout": 30, 
    "startArtifacts": null,
    "expectedArtifacts": null
},
```

#### 配布ステージ
配布ステージはDeployステージでガイドが作成されました。[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_3)でステージの詳細ガイドが確認できます。

``` json
{
    "type": "deployManifest",
    "name": "deploy",
    "refId": "3",
    "requisiteStageRefIds": [
        "2"
    ],
    "deployTarget": "{[環境設定]配布対象設定に保存された配布対象名}",  
    "manifests": [


        {
            "apiVersion": "apps/v1",
            "kind": "Deployment",
            "metadata": {
                "labels": {
                    "app": "pipeline-test"
                },
                "name": "pipeline-test"
            },
            "spec": {
                "replicas": 2,
                "revisionHistoryLimit": 3,
                "selector": {
                    "matchLabels": {
                        "app": "pipeline-test-example"
                    }
                },
                "template": {
                    "metadata": {
                        "labels": {
                            "app": "pipeline-test-example"
                        },
                        "name": "pipeline-test-example"
                    },
                    "spec": {
                        "containers": [
                            {
                                "image": "example.registry.container.nhncloud.com/test/pipelineImage:latest",
                                "imagePullPolicy": "Always",
                                "name": "pipeline-test",
                                "ports": [
                                    {
                                        "containerPort": 8080
                                    }
                                ]
                            }
                        ]
                    }
                }
            }
        }
    ],
    "namespaceOverride": "",
    "startArtifacts": null,
    "expectedArtifacts": null,
    "manifestArtifactId": null,
    "manifestSource": "text",
    "manifestArtifact": null
}
```

Deployステージで使用するManifest情報は配布環境に合わせて変更する必要があります。
YAMLファイルをJSON形式に変更する必要があります(ステージの変更によりコンソールUIでの作業を推奨します)。

以降のシナリオもこのシナリオを基に作成されています。

### 2. パイプライン完了通知を追加するシナリオ
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-02.json)

配布後、Webhookで通知を受け取るシナリオです。Webhookを受け取るURLとPayload、Methodに該当するデータを入力後、使用可能です。

![template-guide-09.png](..%2Fimages%2F2023-10-31%2Ftemplate-guide-09.png)

[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)でWebhookステージの詳細ガイドが確認できます。
``` json
{
    "type": "webhook",
    "name": "webhook",
    "refId": "4",
    "requisiteStageRefIds": [
        "3"
    ],
    "url": "{Webhookを送るURL}",
    "payload": null, // http request body
    "customHeaders": {}, // http request header
    "failFastStatusCodes": [
        500  // 403,500,503
    ],
    "method": "{}" // GET, POST, PUT, DELETE, PATCH, HEAD
}
```

### 3. Github(GitLab、イメージストア)イベント発生時のPipeline自動実行シナリオ
[Pipelineコンソール使用ガイド](http://static.toastoven.net/prod_pipeline/template/template-scenario-03.json)

テンプレートのTrigger領域を設定すると、Github(GitLab、イメージストア)自動実行設定ができます。
[コンソール使用ガイド](/Dev%20Tools/Pipeline/ko/pipeline-management/#_9)の自動実行部分に入力値に関する追加ガイドがあります。
![template-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-08.png)
``` json
triggers: [
    {
        "type": "git",
        "branch": "{ブランチ}",
        "organization": "{組織名またはユーザー名}",
        "secret": "{シークレット情報}",
        "project": "{プロジェクト名}",
        "source": "github"
    }
],
```

### 4. 1つのパイプラインで開発環境とリアル環境を分けて配布するシナリオ
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-04.json)

1つのパイプラインでユーザーの選択に応じて分岐処理を行うように配布できます。
このシナリオは開発環境、リアル環境のように区分された環境に配布する場合に活用できます。
![template-guide-10.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-10.png)
例で作成されたパイプラインのように `develop`, `real` を選択して好きな環境に配布できます。
異なる値に変更して使用でき、この時、後ろにあるPrecondition Stageの値も同様に修正する必要があります。

[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)でJudgement(実行管理)、Precondition(実行条件)ステージの詳細ガイドが確認できます。

```json
[
  {
    "type": "manualJudgment",
    "name": "judgement",
    "refId": "4",
    "requisiteStageRefIds": [
      "2"
    ],
    "failPipeline": false,
    "completeOtherBranchesThenFail": false,
    "continuePipeline": false,
    "instructions": "開発環境、リアル環境の分岐処理",
    "judgmentInputs": [
      {
        "value": "develop" // preconditionsと同じ値である必要があります。
      },
      {
        "value": "real" // preconditionsと同じ値である必要があります。
      }
    ],
    "notifications": []
  },
  {
    "type": "checkPreconditions",
    "name": "precondition-develop",
    "refId": "5",
    "requisiteStageRefIds": [
      "4"
    ],
    "preconditions": [
      {
        "failPipeline": false,
        "type": "expression",
        "context": {
          "equals": true,
          "targetExecutionValue": "develop", // 希望する任意の値に変更可能です。
          "expression": null,
          "failureMessage": null
        }
      }
    ]
  },
  {
    "type": "checkPreconditions",
    "name": "precondition-real",
    "refId": "6",
    "requisiteStageRefIds": [
      "4"
    ],
    "preconditions": [
      {
        "failPipeline": false,
        "type": "expression",
        "context": {
          "equals": true,
          "targetExecutionValue": "real", // 希望する任意の値に変更可能です。
          "expression": null,
          "failureMessage": null
        }
      }
    ]
  },
]
```

### 5. リアル環境への配布前に承認手続きを追加して配布するシナリオ
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-05.json)
![template-guide-11.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-11.png)
4番シナリオでリアル環境に配布する前に承認段階を追加し、承認後に配布されるように構成できます。

[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)で承認管理ステージの詳細ガイドが確認できます。

```json
{
    "type": "manualJudgment",
    "name": "approve",
    "refId": "8",
    "requisiteStageRefIds": [
        "6"
    ],
    "instructions": "承認管理ステージです。",
    "judgmentInputs": [],
    "approval": true
}
```

### 6. 多数のパイプラインで開発環境、リアル環境を分けて配布するシナリオ
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-06.json)

パイプラインが環境ごとに分離して構成されている場合、パイプライン自体を選択して配布できます。
![template-guide-12.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-12.png)
```json
[
  {
    "type": "pipeline",
    "name": "execute-pipeline",
    "refId": "4",
    "requisiteStageRefIds": [
      "2"
    ],
    "pipeline": "{実行したいパイプラインID}",
    "waitForCompletion": true
  },
  {
    "type": "pipeline",
    "name": "execute-pipeline",
    "refId": "5",
    "requisiteStageRefIds": [
      "3"
    ],
    "pipeline": "{実行したいパイプラインID}",
    "waitForCompletion": true
  }
]
```

パイプラインIDは**パイプラインバージョン > JSON表示**をクリックして確認できます。
![template-guide-06](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-06.png)
![template-guide-07](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-07.png)

### 7. Blue/Green配布
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-07.json)

![deploy-strategy-guide-03.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-03.png)

Blue/Green配布のためのパイプラインを構成できます。Blue/Green配布は[配布戦略ガイド](/Dev%20Tools/Pipeline/ja/deploy-strategy-guide/)で詳細を確認できます。
```json
{
    "type": "disableManifest",
    "name": "disable old app",
    "refId": "2",
    "requisiteStageRefIds": [
        "1"
    ],
    "deployTarget": "{[環境設定]配布対象設定に保存された配布対象名}", //環境設定に登録した配布対象名を入力する必要があります(例：deploy-pipeline)。
    "namespace": "{namespace名}",
    "mode": "dynamic",
    "kind": "replicaSet",
    "cluster": "replicaSet {1番ステージで作成したReplicaSetの名前}",
    "criteria": "Second Newest"
}
```

[Pipelineステージガイド](/Dev%20Tools/Pipeline/ko/stage-guide/#_3)で**配布 - Disableステージ**詳細ガイドを確認できます。

---

Blue/Green配布のため、PipelineでServiceを先に作成する必要があります。

[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-07-2.json)

![deploy-strategy-guide-01.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-01.png)

### 8. Blue/Green配布(サービスモニタリング追加)
[テンプレートファイルダウンロード](http://static.toastoven.net/prod_pipeline/template/template-scenario-08.json)

![deploy-strategy-guide-10.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-10.png)

Blue/Green配布のためのパイプラインを構成できます。Blue/Green配布は[配布戦略ガイド](/Dev%20Tools/Pipeline/ja/deploy-strategy-guide/)で詳細を確認できます。

7番のシナリオとほぼ同じで、サービスモニタリングのための**機能 - Webhookステージ**が追加されました。
```json
{
    "type": "webhook",
    "name": "Monitoring Application",
    "refId": "3",
    "requisiteStageRefIds": [
    "1"
    ],
    "ifStageFailType": "IGNORE_THE_FAILURE",
    "url": "{Serviceの状態を確認できるURL}", // サービスの状態を確認できるURLを追加します。
    "payload": null,
    "customHeaders": {},
    "failFastStatusCodes": [
500
    ],
    "method": "GET"
}
```
