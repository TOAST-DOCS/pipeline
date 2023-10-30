## Dev Tools > Pipeline > 콘솔 사용 가이드 > 템플릿 가이드
템플릿 가이드에서는 템플릿 파일을 이용하여 파이프라인 생성하는 방법을 설명합니다.

## 기존 파이프라인과 동일한 파이프라인 생성
기존에 구성되어 있는 파이프라인에서 JSON 파일을 다운로드한 후 동일한 형태의 신규 파이프라인을 생성하는 방법입니다.

### 1. 기존 파이프라인 JSON 파일 다운로드
기존 파이프라인을 선택하여 기본 정보의 **JSON 보기** > **파이프라인 템플릿 다운로드**를 통해 JSON 파일을 다운로드할 수 있습니다.
![template-guide-01](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-01.png)

### 2. 템플릿 파일로 파이프라인 생성
2.1 **파이프라인 관리**에서 **파이프라인 생성**을 클릭합니다. 다운로드한 JSON 파일을 업로드합니다. 업로드 후 **다음**을 클릭하게 되면 바로 **최종 검토** 단계로 넘어가게 됩니다.
![template-guide-02](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-02.png)

2.2 **최종 검토** 단계에서 등록된 파일명 확인이 가능하며 **생성**을 클릭하면 파이프라인이 생성됩니다.
![template-guide-03](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-03.png)
![template-guide-04](http://static.toastoven.net/prod_pipeline/2023-09-26/template-guide-04.png)

## 샘플 시나리오 템플릿으로 파이프라인 생성
시나리오마다 샘플 템플릿 파일을 제공하여 손쉽게 파이프라인을 생성할 수 있습니다.

원하는 시나리오에 있는 JSON 파일을 다운로드한 뒤 중괄호(`{}`)로 요구하는 데이터 전체를 입력하여 사용할 수 있습니다. 특히 `[환경 설정]` 접두사가 붙은 데이터의 경우 **Pipeline > 환경 설정**에 있는 데이터를 사용하므로 데이터가 등록되어 있어야 합니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/environment-config/#_1)에서 등록 방법을 확인할 수 있습니다.

Bake Stage 사용에 대한 샘플 시나리오 템플릿의 경우 기능 변경이 필요하여 추후 제공될 예정입니다.

### 1. 소스 - 빌드 - 배포 단계의 기본적인 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-01.json)

Github에서 소스코드를 가져와 NHN Cloud 빌드 도구로 빌드 후 대상 서버에 Manifest 정보로 배포하는 시나리오입니다.

![template-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-08.png)

등록되어 있는 JSON 파일을 다운로드 후 중괄호로 표시된 데이터에 대한 정보 입력이 필요합니다.

#### 소스 스테이지
소스 스테이지 중 Github을 기준으로 가이드가 작성되었습니다. [Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_1)에서 스테이지 상세 가이드는 확인 가능합니다.

``` json
{
    "type": "githubSource",
    "name": "source",
    "refId": "1",
    "requisiteStageRefIds": [],
    "sourceRepo": "{[환경 설정] 소스 저장소 설정에 저장된 소스 저장소 이름}",   //환경 설정에 등록한 소스 저장소 이름 입력이 필요합니다. 
    "branch": "{배포 대상 브랜치}"  //배포 대상 소스 브랜치에 해당하는 값 입력이 필요합니다(예. main).
},
```

`"sourceRepo": "{소스 저장소 설정에 저장된 소스 저장소 이름}"`으로 입력값을 요구하고 있으며 **환경 설정** 내 소스 저장소 설정에 등록한 정보 중 사용할 소스 저장소 이름을 확인 후 `"sourceRepo": "github-pipeline"`과 같이 수정이 필요합니다.

![template-guide-05](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-05.png)

**이미지 저장소 설정**, **배포 대상 설정**도 동일하게 설정된 이름 확인 후 수정이 필요합니다.

#### 빌드 스테이지
빌드 스테이지 중 NHN Cloud 빌드 도구를 기준으로 가이드가 작성되었습니다. [Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_2)에서 스테이지 상세 가이드는 확인 가능합니다.

``` json
{
    "type": "imageBuild",
    "name": "build",
    "refId": "2",
    "requisiteStageRefIds": [
        "1"
    ],
    "buildImageRegistry": "{[환경 설정] 이미지 저장소 설정에 저장된 이미지 저장소 이름}",    //환경 설정에 등록한 이미지 저장소 이름 입력이 필요합니다(예. buildImageRegistry-pipeline).
    "buildImageName": "{이미지 이름}",  //이미지 이름 입력이 필요합니다(예. maven).
    "buildImageTag": "{이미지 태그}",   //이미지 태그 정보가 필요합니다(예. 1.0.0).
    "buildCommand": "{빌드 명령어}",    //빌드 명령어가 필요합니다(예. mvn package).
    "dockerfilePath": "{Dockerfile 경로}",  //Dockerfile의 경로 입력이 필요합니다(예. Dockerfile).
    "buildWorkDir": "",   //선택항목으로 Dockerfile의 실행 경로를 입력합니다.
    "pushImageRegistry": "{[환경 설정] 빌드 결과가 업로드 될 이미지 저장소 설정에 저장된 이미지 저장소 이름}",  //환경 설정에 등록한 이미지 저장소 이름 입력이 필요합니다(예. pushImageRegistry-pipeline).
    "pushImageName": "{빌드 결과 이미지 이름}", //빌드 결과에 대한 이미지 이름 입력이 필요합니다(예. result-image).
    "pushImageTag": "{빌드 결과 이미지 태그}",  //빌드 결과 이미지의 태그가 필요합니다(예. latest).
    "buildFlavorName": "c2m4",  //기본값이 c2m4이며, c4m8 성능으로도 제공됩니다.
    "buildTimeout": 30, //기본값이 30분입니다. 1부터 600까지 입력할 수 있습니다.
    "startArtifacts": null,
    "expectedArtifacts": null
},
```

#### 배포 스테이지
배포 스테이지는 Deploy 스테이지로 가이드가 작성되었습니다. [Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_3)에서 스테이지 상세 가이드는 확인 가능합니다.

``` json
{
    "type": "deployManifest",
    "name": "deploy",
    "refId": "3",
    "requisiteStageRefIds": [
        "2"
    ],
    "deployTarget": "{[환경 설정] 배포 대상 설정에 저장된 배포 대상 이름}",  //환경 설정에 등록한 배포 대상 이름 입력이 필요합니다(예. deploy-pipeline).
    "manifests": [
        // Deployment Manifest 정보 입력이 필요합니다.
        // 아래 예시를 참고하여 작성 후 등록하여 사용 가능합니다.
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

Deploy 스테이지에서 사용하는 Manifest 정보는 배포 환경에 맞도록 변경이 필요합니다.
YAML 파일을 JSON 형태로 변경이 필요합니다(스테이지 변경을 통해 콘솔 UI에서 작업하는 것을 권장합니다.).

이후 시나리오도 해당 시나리오를 바탕으로 작성되어 있습니다.

### 2. 파이프라인 완료 알림 추가된 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-02.json)

배포 후 Webhook을 통해 알림을 받는 시나리오입니다. Webhook을 받을 URL과 Payload, Method에 해당하는 데이터를 입력 후 사용 가능합니다.

![template-guide-09.png](..%2Fimages%2F2023-10-31%2Ftemplate-guide-09.png)

[Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)에서 Webhook 스테이지 상세 가이드는 확인 가능합니다.
``` json
{
    "type": "webhook",
    "name": "webhook",
    "refId": "4",
    "requisiteStageRefIds": [
        "3"
    ],
    "url": "{Webhook 보낼 URL}",
    "payload": null, // http request body
    "customHeaders": {}, // http request header
    "failFastStatusCodes": [
        500  // 403,500,503
    ],
    "method": "{}" // GET, POST, PUT, DELETE, PATCH, HEAD
}
```

### 3. Github(GitLab, 이미지 저장소) 이벤트 발생 시 파이프라인 자동 실행 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-03.json)

템플릿의 Trigger 영역을 설정하면 Github(GitLab, 이미지 저장소) 자동 실행 설정을 할 수 있습니다.
[Pipeline 콘솔 사용 가이드](/Dev%20Tools/Pipeline/ko/pipeline-management/#_9)의 자동 실행 부분에 입력값에 대한 추가 가이드가 있습니다.
![template-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-08.png)
``` json
"triggers": [
    {
        "type": "git",
        "branch": "{브랜치}",
        "organization": "{조직명 혹은 사용자 이름}",
        "secret": "{시크릿 정보}",
        "project": "{프로젝트 이름}",
        "source": "github"
    }
],
```

### 4. 하나의 파이프라인으로 개발 환경, 리얼 환경을 구분해서 배포하는 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-04.json)

하나의 파이프라인으로 사용자의 선택에 따라 분기처리를 하도록 배포할 수 있습니다.
해당 시나리오는 개발 환경, 리얼 환경같이 구분되어 있는 환경에 배포하는 경우 활용할 수 있습니다.
![template-guide-10.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-10.png)
예시로 작성된 파이프라인처럼 `develop`, `real`을 선택하여 원하는 환경에 배포를 진행할 수 있습니다.
다른 값으로 변경하여 사용 가능하며 이때 뒤에 있는 Precondition Stage의 값도 동일하게 수정이 필요합니다.

[Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)에서 Judgement(실행 관리), Precondition(실행 조건) 스테이지 상세 가이드는 확인 가능합니다.

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
    "instructions": "개발 환경, 리얼 환경 분기 처리",
    "judgmentInputs": [
      {
        "value": "develop" // preconditions와 같은 값이어야 합니다.
      },
      {
        "value": "real" // preconditions와 같은 값이어야 합니다.
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
          "targetExecutionValue": "develop", // 원하는 임의의 값으로 변경 가능합니다.
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
          "targetExecutionValue": "real", // 원하는 임의의 값으로 변경 가능합니다.
          "expression": null,
          "failureMessage": null
        }
      }
    ]
  },
]
```

### 5. 리얼 환경에 배포 전 승인 절차를 추가하여 배포하는 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-05.json)
![template-guide-11.png](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-11.png)
4번 시나리오에서 리얼 환경에 배포하기 전 승인 단계를 추가하여 승인 후 배포가 되도록 구성할 수 있습니다.

[Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)에서 승인 관리 스테이지 상세 가이드는 확인 가능합니다.

```json
{
    "type": "manualJudgment",
    "name": "approve",
    "refId": "8",
    "requisiteStageRefIds": [
        "6"
    ],
    "instructions": "승인 관리 스테이지입니다.",
    "judgmentInputs": [],
    "approval": true
}
```

### 6. 다수의 파이프라인으로 개발 환경, 리얼 환경을 구분해서 배포하는 시나리오
[템플릿 파일 다운로드](http://static.toastoven.net/prod_pipeline/template/template-scenario-06.json)

파이프라인이 환경별로 분리되어 구성되어 있을 때 파이프라인 자체를 선택해서 배포 가능합니다.
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
    "pipeline": "{실행하고자 하는 파이프라인 ID}",
    "waitForCompletion": true
  },
  {
    "type": "pipeline",
    "name": "execute-pipeline",
    "refId": "5",
    "requisiteStageRefIds": [
      "3"
    ],
    "pipeline": "{실행하고자 하는 파이프라인 ID}",
    "waitForCompletion": true
  }
]
```

파이프라인 ID는 **파이프라인 버전 > JSON 보기**를 클릭하여 확인 가능합니다.
![template-guide-06](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-06.png)
![template-guide-07](http://static.toastoven.net/prod_pipeline/2023-10-31/template-guide-07.png)
