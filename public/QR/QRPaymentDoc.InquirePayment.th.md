# **QR Payment API**

ใช้เมื่อร้านค้าต้องการรับชำระเงินผ่าน Thai QR จากลูกค้า QR ที่สร้างขึ้นจะเป็น Dynamic QR (ร้านค้าสามารถกำหนดยอดเงินได้ แต่ลูกค้าไม่สามารถแก้ไขได้) โดย QR ที่สร้างขึ้นจะมีอายุ 10 นาที
<br />

# Inquire Payment (Transaction Status)

**Description**

ใช้สำหรับตรวจสอบสถานะของ QR Code ที่สร้างขึ้นว่าจ่ายแล้วหรือไม่

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/pos/inquire_payment/v2
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

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTAL.kasikornbank.com:12002/pos/inquire_payment/v2 \
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
---[node.js/nodejs]---
var request = require("request");

var options = {
  method: 'POST',
  url: 'https://APIPORTAL.kasikornbank.com:12002/pos/inquire_payment/v2,
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
