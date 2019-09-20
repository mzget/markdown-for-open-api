# **QR Payment API**

QR API is an API for merchant that want to accept payment via Thai QR. The QR code generated from QR API is dynamic QR which merchant can fill the amount of money but customer can't edit. QR last for 10 minutes.

<br />

# Void Payment (Cancel Transaction)

**Description**

Void transaction on the QR Code that is paid

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/pos/void_payment
```

**Parameters**

| Field                        | Data Type  | Description                                                           | Example                          | Mandatory |
| ---------------------------- | ---------- | --------------------------------------------------------------------- | -------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string     | Type of content as application/json                                   | application/json                 |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string(15) | ID to uniquely define each request from partner                       | RGH001030118001                  |     Y     |
| partnerId                    | string(10) | Partner identifier. This ID will be provided to each partner by KBank | POS001                           |     Y     |
| partnerSecret                | string(32) | Secret key to identify each partner                                   | PPsaiu7890yyatcionmsp01ooYY46789 |     Y     |
| requestDt                    | string(33) | Timestamp when partner send this request to KBank in ISO 8601 format  | 2018-04-05T12:30:00+07:00        |     Y     |
| merchantId                   | string(14) | Shop's merchant ID in KBank's system                                  | BEV06000080200                   |     Y     |
| terminalId                   | string(8)  | Shop's terminal ID in KBank's system                                  | 09000107                         |     Y     |
| qrType                       | string(1)  | Type of QR payment. Please refer to Appendix for possible values      | 3                                |     Y     |
| origPartnerTxnUid            | string(15) | Original partnerTxnUid of QR request to inquire the payment status    | QRH001030118001                  |     Y     |

<br />

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X POST \
  https://APIPORTAL.kasikornbank.com:12002/pos/void_payment \
  -H 'cache-control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid":"{{YOUR TXN ID}}",
    "partnerId":"{{YOUR PARTNER ID}}",
    "partnerSecret":"{{YOUR PARTNER SECRET}}",
    "requestDt": "2018-11-15T13:56:38+07:00",
    "merchantId": "KB000000264544",
    "terminalId": "",
    "qrType": "3",
    "origPartnerTxnUid": "{{YOUR QR TXN ID}}"
}'

---[Javascript/javascript]---
var request = require("request");

var options = {
  method: 'POST',
  url: 'https://APIPORTAL.kasikornbank.com:12002/pos/void_payment',
  headers: {
    'cache-control': 'no-cache',
    'Content-Type': 'application/json',
  },
  body: {
    partnerTxnUid: '{{YOUR TXN ID}}',
    partnerId: '{{YOUR PARTNER ID}}',
    partnerSecret: '{{YOUR PARTNER SECRET}}',
    requestDt: '2018-11-15T13:56:38+07:00',
    merchantId: 'KB000000264544',
    terminalId: '',
    qrType: '3',
    origPartnerTxnUid: '{{YOUR QR TXN ID}}'
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
    "partnerTxnUid": "INQ001030118001",
    "partnerId": "POS001",
    "partnerSecret": "PPsaiu7890yyatcionmsp01ooYY46789",
    "requestDt": "2018-01-03T12:30:00+07:00",
    "merchantId": "BEV06000080200",
    "terminalId": "09000107",
    "qrType": "3",
    "origPartnerTxnUid": "QRH001030118001"
}
```
