## Dev Tools > Pipeline > APIガイド > API v1.0ガイド

## Pipeline API v1.0 共通情報

### API エンドポイント

| リージョン | エンドポイント                                        |
|-----------|----------------------------------------------|
| 韓国(パンギョ)リージョン | https://kr1-pipeline.api.nhncloudservice.com |
| 韓国(光州)リージョン | https://kr3-pipeline.api.nhncloudservice.com |

### 認証及び権限
Pipeline APIを使用するには、User Access Keyが必要です。User Access Keyは、NHN CloudアカウントまたはIAMアカウントに紐づいて発行される認証キーであり、Secret Access Keyと併用してAPIリクエストの認証手段として活用されます。

User Access KeyとSecret Access Keyは、コンソールのAPIセキュリティ設定で発行できます。User Access Keyの発行及び使用に関する詳細は、[User Access Key](docs.nhncloud.com/ja/nhncloud/ja/public-api/user-access-key)をご参照ください。

## Pipeline 手動実行
```text
POST /api/anchor/v1.0/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-TC-AUTHENTICATION-ID: {id}
X-TC-AUTHENTICATION-SECRET: {secret}
```

### Request Header
| Name | Description | Value |
| ---- | ----------- | ----- |
| X-NHN-REGION | Region | KR1, KR3 |
| X-NHN-APPKEY | PipelineサービスのAppkey | {appkey} |
| X-TC-AUTHENTICATION-ID | APIセキュリティ設定メニューのUser Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | APIセキュリティ設定メニューのSecret Access Key | {secret} |

### Request Body
```text
なし
```

### Response Body
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

### Sample Request For cURL

``` java
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-TC-AUTHENTICATION-ID:{id}" \
   -H "X-TC-AUTHENTICATION-SECRET:{secret}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute'
```
