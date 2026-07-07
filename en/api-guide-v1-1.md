<!-- pre-align:aligned sig=be2ea142981c -->

## Dev Tools > Pipeline > API Guide > API v1.1 Guide

<a id="pipeline-api-v11-common-information"></a>

## Pipeline API v1.1 Common Information

<a id="api-endpoint"></a>

### API Endpoint

| Region | Endpoint                                        |
| --- |----------------------------------------------|
| Korea (Pangyo) Region | https://kr1-pipeline.api.nhncloudservice.com |
| Korea (Gwangju) region | https://kr3-pipeline.api.nhncloudservice.com |

<a id="authentication-and-authorization"></a>

### Authentication and Authorization
Pipeline uses User Access Key tokens for authentication and authorization when making API calls.
The User Access Key token is a temporary, Bearer-type access token issued from a User Access Key.
For more information on issuing and using User Access Key tokens, refer to the [User Access Key Token](/nhncloud/en/public-api/user-access-key-token).

<a id="manual-pipeline-execution"></a>

## Manual Pipeline Execution
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
| X-NHN-APPKEY | Appkey for the Pipeline service     | {appkey} |
| X-NHN-Authorization | Issued User Access Key token | {token}  |

<a id="request-body"></a>

### Request Body
```text
None
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
