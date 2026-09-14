<!-- pre-align:aligned sig=33145a4b8721 -->

<a id="dev-tools-pipeline-api-guide-api-v11-guide"></a>
## Dev Tools > Pipeline > API 가이드 > API v1.1 가이드 { #dev-tools-pipeline-api-guide-api-v11-guide }

<a id="pipeline-api-v11-common-information"></a>
## Pipeline API v1.1 공통 정보 { #pipeline-api-v11-common-information }

<a id="api-endpoint"></a>
### API 엔드포인트 { #api-endpoint }

| 리전 | 엔드포인트                                        |
| --- |----------------------------------------------|
| 한국(판교) 리전 | https://kr1-pipeline.api.nhncloudservice.com |
| 한국(광주) 리전 | https://kr3-pipeline.api.nhncloudservice.com |

<a id="authentication-and-authorization"></a>
### 인증 및 권한 { #authentication-and-authorization }
Pipeline은 API 호출 시 인증/인가를 위해 User Access Key 토큰을 사용합니다.
User Access Key 토큰은 User Access Key를 기반으로 발급되는 Bearer 타입의 일시적 액세스 토큰입니다.
User Access Key 토큰 발급 및 사용에 대한 자세한 내용은 [User Access Key 토큰](/nhncloud/ko/public-api/user-access-key-token)을 참고하세요.

<a id="manual-pipeline-execution"></a>
## Pipeline 수동 실행 { #manual-pipeline-execution }
```text
POST /api/anchor/v1.1/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-NHN-Authorization: Bearer {token}
```

<a id="request-header"></a>
### Request Header { #request-header }
| Name | Description              | Value    |
| ---- |--------------------------|----------|
| X-NHN-REGION | Region                   | KR1      |
| X-NHN-APPKEY | Pipeline 서비스의 Appkey     | {appkey} |
| X-NHN-Authorization | 발급받은 User Access Key 토큰 | {token}  |

<a id="request-body"></a>
### Request Body { #request-body }
```text
없음
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

``` bash
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-NHN-Authorization: Bearer {token}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.1/pipelines/{pipeline-name}/execute'
```
