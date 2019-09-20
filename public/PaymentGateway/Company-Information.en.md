# Get information of company

| ENV           | Prod                                                                                                          | Dev/Test                                                                                                      |
| ------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Endpoint URL  | https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getDetails/{companyId} | https://uat-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getDetails/{companyId} |  | application/json | Bearer : xxxxxxxxxxxxxxxx (TBC) |
| HTTP Method   | GET                                                                                                           | GET                                                                                                           |
| Content-Type  | application/json                                                                                              | application/json                                                                                              |
| Authorization | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                               | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                               |

**Sample request message**

```javascript
curl -X POST \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getDetails/{companyId}
```

**Request Attributes**

| Attitude Name | Data type | Required | Description |
| ------------- | --------- | -------- | ----------- |
|               |           |          |             |

**Sample request message**

**Response Attributes**

| Attitude Name | Data type | Can Null (Fail) | Description |
| ------------- | --------- | --------------- | ----------- |
|               |           |                 |             |

**Results for API**

| Status Code | Status Message |
| ----------- | -------------- |
|             |                |
