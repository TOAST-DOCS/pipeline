## Dev Tools > Pipeline > API 가이드

## Pipeline API 공통 정보

### API 엔드포인트

| 리전 | 엔드포인트                                        |
| --- |----------------------------------------------|
| KR1 | https://kr1-pipeline.api.nhncloudservice.com |

### 인증 및 권한
Pipeline API를 사용하려면 User Access Key가 필요합니다. User Access Key는 NHN Cloud 계정 또는 IAM 계정을 기반으로 발급되는 인증 키로, Secret Access Key와 함께 사용하여 API 요청에 대한 인증 수단으로 활용됩니다.

User Access Key와 Secret Access Key는 콘솔의 API 보안 설정에서 발급할 수 있습니다. User Access Key 발급 및 사용에 대한 자세한 내용은 [User Access Key](docs.nhncloud.com/ko/nhncloud/ko/public-api/user-access-key)를 참고하세요

## Pipeline 수동 실행
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
| X-NHN-APPKEY | Pipeline 서비스의 Appkey | {appkey} |
| X-TC-AUTHENTICATION-ID | API 보안 설정 메뉴의 User Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | API 보안 설정 메뉴의 Secret Access Key | {secret} |

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
