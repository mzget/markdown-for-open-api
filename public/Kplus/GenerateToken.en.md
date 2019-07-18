# Generate Token

**Description**

For generating order token used as a reference of products order with details of Total Amount, Quantity, Item (Product) Name and other additional information

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/generate-token
```

**Request Parameters**

| Field                        | Data Type | Description                                                  | Example                                              | Mandatory |
| ---------------------------- | --------- | ------------------------------------------------------------ | ---------------------------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                          | application/json                                     |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string    | ID to uniquely define each request from partner              | RGH001030118001                                      |     Y     |
| partnerId                    | string    | Partner ID will be provided to each partner by KBank         | KP2XXX000033159                                      |     Y     |
| partnerSecret                | string    | Secret key to identify each partner                          | S1AyQ0ZCMDAwMDMzMTU5LWtwbHVzLXNpdC0yYzJwLWZhY2Vib29r |     Y     |
| requestDt                    | long      | Timestamp in unix                                            | 1519630776                                           |     Y     |
| reference1                   | string    | Reference1                                                   |                                                      |     Y     |
| reference2                   | string    | Reference2                                                   |                                                      |     N     |
| totalAmount                  | string    | Summary amount of items and shipping fee                     | 000000005000 = 50.00THB                              |     Y     |
| shopImageUrl                 | string    | An image url                                                 |                                                      |     Y     |
| partnerIconUrl               | string    | An image url                                                 |                                                      |     N     |
| shopName                     | string    | Name of shop                                                 |                                                      |     Y     |
| shippingFee                  | string    | Order shipping fee                                           | 000000005000 = 50.00THB                              |     Y     |
| osPlatform                   | string    | OS platform                                                  | IOS / ANDROID                                        |     Y     |
| items                        | array     | Array of item that customer bought                           |                                                      |     N     |
| items.itemName               | string    | Name of item                                                 |                                                      |     N     |
| items.quantity               | number    | Quantity of item                                             | 1                                                    |     N     |
| items.amount                 | string    | Amount                                                       | 000000005000 = 50.00THB                              |     Y     |
| currencyCode                 | string    | Currency Code                                                | THB                                                  |     Y     |
| currencyExponent             | string    | Currency Exponent                                            | 2                                                    |     Y     |
| buyerName                    | string    | Name of buyer                                                |                                                      |     N     |
| partnerToken                 | string    | Token to validate txn from partner with AES256-cbc encrypted |                                                      |     N     |
| promotionCode                | string    | Key-in promotion code from customer                          |                                                      |     N     |
| additionalInfo1              | string    | Reserve for additional information                           |                                                      |     N     |
| additionalInfo2              | string    | Reserve for additional information                           |                                                      |     N     |
| additionalInfo3              | string    | Reserve for additional information                           |                                                      |     N     |

**Response Message**

| Field          | Data Type | Description                                                           |
| -------------- | --------- | --------------------------------------------------------------------- |
| partnerTxnUid  | string    | ID to uniquely define each request from partner                       |
| partnerId      | string    | Partner identifier. This ID will be provided to each partner by KBank |
| statusCode     | string    | Status code                                                           |
| errorCode      | string    | Code to identify the error                                            |
| errorDesc      | string    | Description of the error                                              |
| callBackAppUrl | string    | Url use to switch to kplus application                                |
| tokenId        | string    | Order reference id generated by kplus                                 |
| expiryDate     | long      | Timestamp in unix                                                     |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://203.146.225.57:12002/kplus/payment/generate-token \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid": "transIrtses192",
    "partnerId":"PTR1902369",
    "partnerSecret":"7da57c4eb242435fa3e91bb7a69e2a28",
    "requestDt": "2019-07-18T17:06:42.411",
    "reference1": "KS1234567",
    "reference2": "",
    "totalAmount": "500",
    "shopImageUrl": "data:image/jpeg;base64,/9j/4AAQSkZJRgABvVfyx86RWKmCY8QTV W9/fEtZf/2Q==",
    "shopName": "KaiJonJeng",
    "shippingFee": "1000",
    "osPlatform": "IOS",
    "currencyCode": "THB",
    "currencyExponent": "2",
    "buyerName": "THB"
}'
---[JS/javascript]---
$.ajax({
  method: 'POST',
  url: 'https://203.146.225.57:12002/kplus/payment/generate-token',
  headers:
   { 'Content-Type': 'application/json' },
  body:
   { partnerTxnUid: 'transIrtses192',
     partnerId: 'PTR1902369',
     partnerSecret: '7da57c4eb242435fa3e91bb7a69e2a28',
     requestDt: '2019-07-18T17:06:42.411',
     reference1: 'KS1234567',
     reference2: '',
     totalAmount: '500',
     shopImageUrl: 'data:image/jpeg;base64,/9j/4AAQSkZJRgABvVfyx86RWKmCY8QTV W9/fEtZf/2Q==',
     shopName: 'KaiJonJeng',
     shippingFee: '1000',
     osPlatform: 'IOS',
     currencyCode: 'THB',
     currencyExponent: '2',
     buyerName: 'THB' }
});
```

**Example Response**

```json
{
    "partnerId": "PTR1902369",
    "partnerTxnUid": "7da57c4eb242435fa3e91bb7a69e2a28",
    "errorCode": null,
    "errorDesc": null,
    "statusCode": "00",
    "callBackAppUrl": "https://google.com",
    "tokenId": "KMCMPTmhfsegnzyfuzroygydfibuxjtyjxjibogmbnz276dPMT",
    "expiryDate": "2019-07-18T17:36:42.411"
}
```
