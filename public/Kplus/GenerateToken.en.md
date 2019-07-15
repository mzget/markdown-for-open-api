# Generate Token

**Description**

For generating order token used as a reference of products order with details of Total Amount, Quantity, Item (Product) Name and other additional information

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://kbankapi.tech/v1/kplus/payment/generate-token
```

**Request Parameters**

| Field                        | Data Type | Description                                                  | Example                                              | Mandatory |
| ---------------------------- | --------- | ------------------------------------------------------------ | ---------------------------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                          | application/json                                     |     Y     |
| Partner-Id                   | string    | Partner-Id                                                   |                                                      |     Y     |
| Partner-Secret               | string    | Partner-Secret                                               |                                                      |     Y     |
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
| itemName                     | string    | Name of item                                                 |                                                      |     N     |
| quantity                     | number    | Quantity of item                                             | 1                                                    |     N     |
| amount                       | string    | Amount                                                       | 000000005000 = 50.00THB                              |     Y     |
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
