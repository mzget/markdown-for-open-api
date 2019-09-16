# **QR Payment API**

QR API is an API for merchant that want to accept payment via Thai QR. The QR code generated from QR API is dynamic QR which merchant can fill the amount of money but customer can't edit. QR last for 10 minutes.

<br />

# Request QR

**Description**

Generate dynamic QR Code for Thai QR Payment

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_request
```

**Parameters**

| Field                        | Data Type   | Description                                                                                          | Example                          | Mandatory |
| ---------------------------- | ----------- | ---------------------------------------------------------------------------------------------------- | -------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string      | Type of content as application/json                                                                  | application/json                 |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string(15)  | ID to uniquely define each request from partner                                                      | RGH001030118001                  |     Y     |
| partnerId                    | string(10)  | Partner identifier. This ID will be provided to each partner by KBank                                | POS001                           |     Y     |
| partnerSecret                | string(32)  | Secret key to identify each partner                                                                  | PPsaiu7890yyatcionmsp01ooYY46789 |     Y     |
| requestDt                    | string(33)  | Timestamp when partner send this request to KBank in ISO 8601 format                                 | 2018-04-05T12:30:00+07:00        |     Y     |
| merchantId                   | string(14)  | Shop's merchant ID in KBank's system                                                                 | BEV06000080200                   |     Y     |
| terminalId                   | string(8)   | Shop's terminal ID in KBank's system                                                                 | 09000107                         |     Y     |
| qrType                       | string(1)   | Type of QR payment. Please refer to Appendix for possible values                                     | 3                                |     Y     |
| txnAmount                    | number      | Amount of transaction. Must be positive number. Number of digits depends on each currency.           | 100.50                           |     Y     |
| txnCurrencyCode              | string(3)   | Currency code of transaction amount in ISO 4217. Currently support only "THB"                        | THB                              |     Y     |
| reference1                   | string(100) | Transaction reference 1                                                                              | INV001                           |     Y     |
| reference2                   | string(100) | Transaction reference 2                                                                              |                                  |     N     |
| reference3                   | string(100) | Transaction reference 3                                                                              |                                  |     N     |
| reference4                   | string(100) | Transaction reference 4                                                                              |                                  |     N     |
| metadata                     | string(500) | Item details in following format <item_1> <amount_1>, <item_2> <anount_2> . . ., <item_n> <amount_n> | ถุงผ้า 80.50 ,ดินสอ 20.00        |     N     |

<br />

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X POST \
  https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_request \
  -H 'cache-control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid":"{{YOUR TXN ID}}",
    "partnerId":"{{YOUR PARTNER ID}}",
    "partnerSecret":"{{YOUR PARTNER SECRET}}",
    "requestDt":"2018-01-03T12:30:00+07:00",
    "merchantId":"KB514287431738",
    "terminalId":"term1",
    "qrType":"3",
    "txnAmount":100.50,
    "txnCurrencyCode":"THB",
    "reference1":"INV001",
    "reference2":null,
    "reference3":null,
    "reference4":null,
    "metadata":"ถุงผ้า 80.50, ดินสอ 20.00"
  }'

---[Javascript/javascript]---
var request = require("request");

var options = { method: 'POST',
  url: 'https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_request',
  headers: {
    'cache-control': 'no-cache',
    'Content-Type': 'application/json',
  },
  body: {
    partnerTxnUid: '{{YOUR TXN ID}}',
    partnerId: '{{YOUR PARTNER ID}}',
    partnerSecret: '{{YOUR PARTNER SECRET}}',
    requestDt: '2018-01-03T12:30:00+07:00',
    merchantId: 'KB514287431738',
    terminalId: 'term1',
    qrType: '3',
    txnAmount: 100.5,
    txnCurrencyCode: 'THB',
    reference1: 'INV001',
    reference2: null,
    reference3: null,
    reference4: null,
    metadata: 'ถุงผ้า 80.50, ดินสอ 20.00'
  },
  json: true
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);
});
```

**Example Response**

```json
{
    "partnerTxnUid": "QRH001030118001",
    "partnerId": "POS001",
    "statusCode": "00",
    "errorCode": null,
    "errorDesc": null,
    "accountName": "นายสมชาย รักกสกิ ร",
    "qrCode":
    "00020101021230690016A000000677010112011301055580807780211LEX110000020313LE
    X026039306931590016A00000067701011301030040211LEX110000020413LEX02603930695
    303764540512.815802TH6304A2C1"
}
```
