<!-- pre-align:aligned sig=be2ea142981c -->

## Dev Tools > Pipeline > APIガイド > API v1.1ガイド

<a id="pipeline-api-v11-common-information"></a>

## Pipeline API v1.1 共通情報

<a id="api-endpoint"></a>

### API エンドポイント

| リージョン | エンドポイント |
| --- |----------------------------------------------|
| 韓国(パンギョ)リージョン | https://kr1-pipeline.api.nhncloudservice.com |
| 韓国(光州)リージョン | https://kr3-pipeline.api.nhncloudservice.com |

<a id="authentication-and-authorization"></a>

### 認証及び権限
Pipelineは、API呼び出し時の認証/認可にUser Access Keyトークンを使用します。
User Access Keyトークンは、User Access Keyをもとに発行されるBearerタイプの一時的なアクセストークンです。
User Access Keyトークンの発行手順や使用方法の詳細は、[User Access Keyトークン](/nhncloud/ja/public-api/user-access-key-token)をご参照ください。

<a id="manual-pipeline-execution"></a>

## Pipeline 手動実行
```text
POST /api/anchor/v1.1/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-NHN-Authorization: Bearer {token}
```

<a id="request-header"></a>

### Request Header
| Name | Description              | Value    |
| ---- |--------------------------|----------|
| X-NHN-REGION | Region                   | KR1      |
| X-NHN-APPKEY | PipelineサービスのAppkey | {appkey} |
| X-NHN-Authorization | 発行されたUser Access Keyトークン | {token} |

<a id="request-body"></a>

### Request Body
```text
なし
```

<a id="response-body"></a>

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

<a id="sample-request-for-curl"></a>

### Sample Request For cURL

``` bash
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-NHN-Authorization: Bearer {token}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.1/pipelines/{pipeline-name}/execute'
```
