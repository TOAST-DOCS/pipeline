## Dev Tools > Pipeline > APIガイド

## Pipeline API 공통 정보

### API 엔드포인트

| 리전 | 엔드포인트                                        |
| --- |----------------------------------------------|
| KR1 | https://kr1-pipeline.api.nhncloudservice.com |

### 인증 및 권한
Pipeline APIを使用するには、User Access Keyが必要です。User Access Keyは、NHN CloudアカウントまたはIAMアカウントに基づいて発行される認証キーであり、Secret Access Keyと共に使用してAPIリクエストに対する認証手段として利用されます。

User Access KeyとSecret Access Keyは、コンソールのAPIセキュリティ設定で発行できます。User Access Keyの発行及び使用に関する詳細は、[User Access Key](docs.nhncloud.com/ja/nhncloud/ja/public-api/user-access-key)を参照してください。

## Pipeline手動実行

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
| X-NHN-REGION | Region | KR1 |
| X-NHN-APPKEY | PipelineサービスのAppkey | {appkey} |
| X-TC-AUTHENTICATION-ID | APIセキュリティ設定メニューのUser Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | APIセキュリティ設定メニューのSecret Access Key | {secret} |

### Request Body
```text
없음
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

### Sample Request For cUrl

``` java
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-TC-AUTHENTICATION-ID:{id}" \
   -H "X-TC-AUTHENTICATION-SECRET:{secret}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute'
```
