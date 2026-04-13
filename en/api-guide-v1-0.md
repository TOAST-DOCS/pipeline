## Dev Tools > Pipeline > API Guide > API v1.0 Guide

## Pipeline API v1.0 Common Information

### API Endpoint

| Region | Endpoint                                        |
| --- |----------------------------------------------|
| Korea (Pangyo) region | https://kr1-pipeline.api.nhncloudservice.com |
| Korea (Gwangju) Region | https://kr3-pipeline.api.nhncloudservice.com |

### Authentication and Authorization
User Access Key is required to use the Pipeline API. A User Access Key is an authentication key issued based on an NHN Cloud or IAM account. It is used in conjunction with a Secret Access Key to authenticate API requests.

User Access Keys and Secret Access Keys can be issued in the console's API Security Setting. For more information on issuing and using User Access Key, please refer to the [User Access Key](docs.nhncloud.com/en/nhncloud/en/public-api/user-access-key).

## Pipeline Manual Run
```text
POST /api/anchor/v1.0/pipelines/{pipeline-name}/execute
X-NHN-REGION: {Region}
X-NHN-APPKEY: {appkey}
X-TC-AUTHENTICATION-ID: {id}
X-TC-AUTHENTICATION-SECRET: {secret}
```

### Request Header
| Name | Description | Value    |
| ---- | ----------- |----------|
| X-NHN-REGION | Region | KR1, KR3 |
| X-NHN-APPKEY | Appkey for the Pipeline service | {appkey} |
| X-TC-AUTHENTICATION-ID | User Access Key ID in API Security Settings menu | {id}     |
| X-TC-AUTHENTICATION-SECRET | Secret Access Key in API Security Settings menu | {secret} |

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

``` java
curl -i -X POST \
   -H "Content-Type:application/json" \
   -H "X-NHN-REGION:KR1" \
   -H "X-TC-AUTHENTICATION-ID:{id}" \
   -H "X-TC-AUTHENTICATION-SECRET:{secret}" \
   -H "X-NHN-APPKEY:{appkey}" \
 'https://kr1-pipeline.api.nhncloudservice.com/api/anchor/v1.0/pipelines/{pipeline-name}/execute'
```
