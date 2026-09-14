<!-- pre-align:aligned sig=de181c4eae23 -->

<a id="dev-tools-pipeline-api-guide-api-v10-guide"></a>
## Dev Tools > Pipeline > APIガイド > API v1.0ガイド { #dev-tools-pipeline-api-guide-api-v10-guide }

<a id="pipeline-api-v10-common-information"></a>
## Pipeline API v1.0 共通情報 { #pipeline-api-v10-common-information }

<a id="api-endpoint"></a>
### API エンドポイント { #api-endpoint }

| リージョン | エンドポイント                                        |
|-----------|----------------------------------------------|
| 韓国(パンギョ)リージョン | https://kr1-pipeline.api.nhncloudservice.com |
| 韓国(光州)リージョン | https://kr3-pipeline.api.nhncloudservice.com |

<a id="authentication-and-authorization"></a>
### 認証及び権限 { #authentication-and-authorization }
Pipeline APIを使用するには、User Access Keyが必要です。User Access Keyは、NHN CloudアカウントまたはIAMアカウントに紐づいて発行される認証キーであり、Secret Access Keyと併用してAPIリクエストの認証手段として活用されます。

User Access KeyとSecret Access Keyは、コンソールのAPIセキュリティ設定で発行できます。User Access Keyの発行及び使用に関する詳細は、[User Access Key](/nhncloud/ja/public-api/user-access-key)をご参照ください。

<a id="pipeline-manual-run"></a>
## Pipeline 手動実行 { #pipeline-manual-run }
```text
POST /api/anchor/v1.0/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-TC-AUTHENTICATION-ID: {id}
X-TC-AUTHENTICATION-SECRET: {secret}
```

<a id="request-header"></a>
### Request Header { #request-header }
| Name | Description | Value |
| ---- | ----------- | ----- |
| X-NHN-REGION | Region | KR1, KR3 |
| X-NHN-APPKEY | PipelineサービスのAppkey | {appkey} |
| X-TC-AUTHENTICATION-ID | APIセキュリティ設定メニューのUser Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | APIセキュリティ設定メニューのSecret Access Key | {secret} |

<a id="request-body"></a>
### Request Body { #request-body }
```text
なし
```

<a id="response-body"></a>
### Response Body { #response-body }
```json
{
  "header":{
    "resultCode":0,
    "resultMessage":"success",
    "isSuccessful":true
  },
  "paging":null,
  "body": {
    "appkey":"appkey",
    "region":"KR1",
    "pipelineName":"pipeline",
    "reason":null,
    "lastExecutionId":"executionId"
  }
}
```

<a id="sample-request-for-curl"></a>
### Sample Request For cURL { #sample-request-for-curl }

``` java
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-TC-AUTHENTICATION-ID:{id}" \
   -H "X-TC-AUTHENTICATION-SECRET:{secret}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute'
```
