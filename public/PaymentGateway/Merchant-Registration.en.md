# Merchant Registration

| ENV           | Prod                                                                                   | Dev/Test                                                                               |
| ------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Endpoint URL  | https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register | https://uat-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register |  | application/json | Bearer : xxxxxxxxxxxxxxxx (TBC) |
| HTTP Method   | POST                                                                                   | POST                                                                                   |
| Content-Type  | application/json                                                                       | application/json                                                                       |
| Authorization | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                        | Bearer : xxxxxxxxxxxxxxxx (TBC)                                                        |

**Sample request message**

```javascript
curl -X POST \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer 1bd227f9d892a7f4581b998c21e353b1686a6bdad5940e7bb6aa596c96e0a6ec' \
-d '{ "companyCode":"End Coperation",
"companyTradeName":"End Coperation",
"companyNameTH":"เอ็น คอร์ป",
"companyNameEN":"End Coperataion",
"firstName":"การะเกด",
"lastName":"ดารา",
"email":"test@endcorp.co.th",
"password":"Password@1",
"addressStr":"20/2 EN",
"postCodeId":161,
"homePhoneNo":"01222222222",
"officePhoneNo":"025635678",
"mobilePhoneNo":"0983833333",
"faxNo":"0899999994",
"emailCompany":"test@endcorp.co.th",
"businessTypeId":15 }' \
https://dev-kpaymentgateway-services.kasikornbank.com/KPGW-Profile-Webapi/api/register
```

**Request Attributes**

| Attitude Name    | Data type    | Required | Description                                     |
| ---------------- | ------------ | -------- | ----------------------------------------------- |
| companyCode      | varchar(255) | Y        | The unique name of company                      |
| companyTradeName | varchar(255) | Y        | Company trade name                              |
| companyNameTH    | varchar(255) | Y        | Company name (TH)                               |
| companyNameEN    | varchar(255) | Y        | Company name (EN)                               |
| firstName        | varchar(255) | Y        | Firstname                                       |
| lastName         | varchar(255) | Y        | Lastname                                        |
| email            | varchar(50)  | Y        | Email (use for merchant login)                  |
| password         | varchar(15)  | Y        | Password (use for merchant login)               |
| addressStr       | varchar(255) | N        | address                                         |
| postCodeId       | Integer      | Y        | Postcode ID (Ref : getPostCodes method)         |
| homePhoneNo      | varchar(20)  | N        | Home phone number                               |
| officePhoneNo    | varchar(20)  | N        | Office phone number                             |
| mobilePhoneNo    | varchar(20)  | Y        | Mobile phone number                             |
| faxNo            | varchar(20)  | N        | Fax number                                      |
| emailCompany     | varchar(50)  | N        | Email of company                                |
| businessTypeId   | Integer      | Y        | Business type ID (Ref : getBusinessType method) |

**Sample response message**

_Example in success case:_

```json
{
  "statusCode": "success",
  "statusMessage": "Successfully created a merchant account.",
  "companyId": "0000000001",
  "companyCode": "KBANK",
  "approveStatus": "PENDING"
}
```

_Example in fail case:_

```json
{
  "statusCode": "fail",
  "statusMessage": "Your merchant can not register. Please verify request parameters."
}
```

**Response Attributes**

| Attitude Name | Data type    | Can Null (Fail) | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| statusCode    | varchar(255) | N               | Status code (success or fail)                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| statusMessage | varchar(255) | N               | Result Messages                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| companyId     | Integer      | Y               | Company Id (Auto generated from KPGW systems)                                                                                                                                                                                                                                                                                                                                                                                                                         |
| companyCode   | varchar(255) | Y               | The unique name of company                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| approveStatus | varchar(10)  | Y               | Status of Registration <br/> **PENDING** - Wait for approve and checking an information’s to integrate test with K-Payment Sandbox system. <br/> **REJECTED** - Not approve, after reviewed by Business team. <br/> **APPROVED** - Approved, after reviewed by Business team. KPGW will successfully a result by email. <br/> **COMPLETED** - Completely test with Sandbox K-Payment system. Waiting for business team and Merchant launch to Production Environment. |

**Results for APl**

| Status Code | Status Message                                                              |
| ----------- | --------------------------------------------------------------------------- |
| success     | Successfully created your merchant account.                                 |
| fail        | Your email is already resisted in sandbox systems.                          |
| fail        | Your postcode or business type parameters don’t exist in K-Payment systems. |
| fail        | Your input parameter is invalid such as email, phone number and others.     |
