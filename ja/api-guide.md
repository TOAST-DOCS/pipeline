## Dev Tools > Pipeline > APIガイド

ユーザーがHTTP Requestを直接構成してPipelineを実行できるAPIを提供します。

## Pipeline手動実行

| Http Method | POST |
| ----------- | ---- |
| Request URL | https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute |

### Header
| Name | Description | Value |
| ---- | ----------- | ----- |
| X-NHN-REGION | Region | KR1 |
| X-NHN-APPKEY | PipelineサービスのAppkey | {appkey} |
| X-TC-AUTHENTICATION-ID | APIセキュリティ設定メニューのUser Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | APIセキュリティ設定メニューのSecret Access Key | {secret} |

**会員情報 > APIセキュリティ設定**で作成できます。

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
