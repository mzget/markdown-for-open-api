# Get Address information with postcode

| ENV           | Prod                                                                                                           | Dev/Test                                                                                                   |
| ------------- | -------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Endpoint URL  | https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getPostcodes/{postCode} | https://uat-kpaymentgateway-services.new-kpgw.com/KPGW-Profile-Webapi/api/register/getPostcodes/{postcode} |  | application/json | Bearer : xxxxxxxxxxxxxxxx (TBC) |
| HTTP Method   | GET                                                                                                            | GET                                                                                                        |
| Content-Type  | application/json                                                                                               | application/json                                                                                           |
| Authorization | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                                | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                                            |

**Sample request message**

```javascript
curl -X GET \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register/getPostcodes/{postCode}
```

**Request Attributes**

| Attitude Name | Data type  | Required | Description                                                        |
| ------------- | ---------- | -------- | ------------------------------------------------------------------ |
| postcode      | varchar(5) | Y        | Thai Postcode. Can be “ALL” or Thai Postcode is 10230, 10600, etc. |

**Sample response message**

_Example in success case:
_

```json
{
  "statusCode": "success",
  "statusMessage": "Result is list of Thai post code and address information.",
  "postcodes": [
    {
      "poistcodeId": 171,
      "postcode": 10600,
      "districCode": 154,
      "districtName": "สมเด็จเจ้าพระยา",
      "amphurCode": 43,
      "amphurName": "คลองสาน",
      "amphurNameEn": "Khlong San",
      "provinceCode": 1,
      "provinceName": "กทม.",
      "provinceNameEn": "Bangkok"
    },
    {
      "poistcodeId": 161,
      "postcode": 10600,
      "districCode": 144,
      "districtName": "คลองต้นไทร",
      "amphurCode": 43,
      "amphurName": "คลองสาน",
      "amphurNameEn": "Khlong San",
      "provinceCode": 1,
      "provinceName": "กทม.",
      "provinceNameEn": "Bangkok"
    }
  ]
}
```

_Example in fail case:_

```json
{
  "statusCode": "fail",
  "statusMessage": " invalid request, your post code is not found."
}
```

**Response Attributes**

| Attitude Name            | Data type    | Can Null (Fail) | Description                |
| ------------------------ | ------------ | --------------- | -------------------------- |
| statusCode               | varchar(255) | N               | Status code success / fail |
| statusMessage            | varchar(255) | N               | Result message             |
| postcodes/postcodeId     | Integer      | Y               | Postcode ID                |
| postcodes/postcode       | Integer      | Y               | Postcode                   |
| postcodes/districtCode   | Integer      | Y               | District code              |
| postcodes/destrictName   | varchar(255) | Y               | District name (TH)         |
| postcodes/destrictNameEN | varchar(255) | Y               | District name (EN)         |
| postcodes/amphurCode     | Integer      | Y               | Amphur code                |
| postcodes/amphurName     | varchar(255) | Y               | Amphur name (TH)           |
| postcodes/amphurNameEn   | varchar(255) | Y               | Amphur name (EN)           |
| postcodes/provinceCode   | Integer      | Y               | Province code              |
| postcodes/provinceName   | varchar(255) | Y               | Province name (TH)         |
| postcodes/provinceNameEn | varchar(255) | Y               | Province name (EN)         |

**Results for APl**

| Status Code | Status Message                                            |
| ----------- | --------------------------------------------------------- |
| success     | Result is list of Thai post code and address information. |
| fail        | Your post code is not found.                              |
