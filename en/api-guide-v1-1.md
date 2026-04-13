## Dev Tools > Pipeline > API Guide > API v1.1 Guide

## Pipeline API v1.1 Common Information

### API Endpoint

| Region | Endpoint                                        |
| --- |----------------------------------------------|
| Korea (Pangyo) Region | https://kr1-pipeline.api.nhncloudservice.com |
| Korea (Gwangju) region | https://kr3-pipeline.api.nhncloudservice.com |

### Authentication and Authorization
Pipeline uses User Access Key tokens for authentication and authorization when making API calls.
The User Access Key token is a temporary, Bearer-type access token issued from a User Access Key.
For more information on issuing and using User Access Key tokens, refer to the [User Access Key Token](/nhncloud/ko/public-api/user-access-key-token).

## Manual Pipeline Execution
```text
POST /api/anchor/v1.1/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-NHN-Authorization: Bearer {token}
```

### Request Header
| Name | Description              | Value    |
| ---- |--------------------------|----------|
| X-NHN-REGION | Region                   | KR1      |
| X-NHN-APPKEY | Appkey for the Pipeline service     | {appkey} |
| X-NHN-Authorization | Issued User Access Key token | {token}  |

### Request Body
```text
None
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

``` bash
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-NHN-Authorization: Bearer {token}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.1/pipelines/{pipeline-name}/execute'
```
