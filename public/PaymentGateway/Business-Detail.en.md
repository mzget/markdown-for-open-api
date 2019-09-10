# Get Details of Business type

| ENV           | Prod                                                                                                    | Dev/Test                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Endpoint URL  | https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getBussinesTypes | https://uat-kpaymentgateway-services.new-kpgw.com/KPGW-Profile-Webapi/api/register/getBussinesTypes |  | application/json | Bearer : xxxxxxxxxxxxxxxx (TBC) |
| HTTP Method   | GET                                                                                                     | GET                                                                                                 |
| Content-Type  | application/json                                                                                        | application/json                                                                                    |
| Authorization | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                         | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                     |

**Sample request message**

```javascript
curl -X GET \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \ https://uat-kpaymentgateway-services.new-kpgw.com/KPGW-Profile- Webapi/api/register/getBussinesTypes
```

**Request Attributes**

| Attitude Name | Data type | Required | Description |
| ------------- | --------- | -------- | ----------- |
| -             | -         | -        | -           |

**Sample response message**
_Example in success case:_

```json
{
  "statusCode": "success",
  "statusMessage": "Results is list of business type",
  "businessTypes": [
    {
      "businessTypeId": 1,
      "businessTypeCode": 69,
      "businessTypeDesc": "สงั่ซอื้สินค้าทางอินเตอร์เน็ต",
      "businessTypeDescEn": "(PAYMENT GATEWAY (E-COMMERCE))"
    },
    {
      "businessTypeId": 2,
      "businessTypeCode": 11,
      "businessTypeDesc": "การบินไทย",
      "businessTypeDescEn": "3077(THAI AIRWAYS)"
    }
  ]
}
```

_Example in fail case:_

```json
{
  "statusCode": "fail",
  "statusMessage": "Your request has invalid parameters."
}
```

**Response Attributes**

| Attitude Name                    | Data type    | Can Null (Fail) | Description                             |
| -------------------------------- | ------------ | --------------- | --------------------------------------- |
| statusCode                       | varchar(255) | N               | Status code success / Otherwise is fail |
| statusMessage                    | varchar(255) | N               | Status message                          |
| businessTypes/businessTypeId     | Integer      | Y               | Business type ID                        |
| businessTypes/businessTypeCode   | Integer      | Y               | Business type code                      |
| businessTypes/businessTypeDesc   | varchar(255) | Y               | Business type description (TH)          |
| businessTypes/businessTypeDescEn | varchar(255) | Y               | Business type description (EN)          |

**Results for API**

| Status Code | Status Message                       |
| ----------- | ------------------------------------ |
| success     | Results is list of business type.    |
| fail        | Your request has invalid parameters. |
