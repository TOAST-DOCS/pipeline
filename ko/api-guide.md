## Dev Tools > Pipeline > API 가이드

사용자가 HTTP Request를 직접 구성하여 Pipeline을 실행할 수 있는 API를 제공합니다.

## Pipeline 수동 실행

| Http Method | POST |
| ----------- | ---- |
| Request URL | https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute |

### Header
| Name | Description | Value |
| ---- | ----------- | ----- |
| X-NHN-REGION | Region | KR1 |
| X-NHN-APPKEY | Pipeline 서비스의 Appkey | {appkey} |
| X-TC-AUTHENTICATION-ID | API 보안 설정 메뉴의 User Access Key ID | {id} |
| X-TC-AUTHENTICATION-SECRET | API 보안 설정 메뉴의 Secret Access Key | {secret} |

**회원 정보 > API 보안 설정**에서 생성할 수 있습니다.

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
