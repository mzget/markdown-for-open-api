# **QR Payment API**

ใช้เมื่อร้านค้าต้องการรับชำระเงินผ่าน Thai QR จากลูกค้า QR ที่สร้างขึ้นจะเป็น Dynamic QR (ร้านค้าสามารถกำหนดยอดเงินได้ แต่ลูกค้าไม่สามารถแก้ไขได้) โดย QR ที่สร้างขึ้นจะมีอายุ 10 นาที

<br />

# Cancel QR

**Description**

ใช้เมื่อกรณีที่ต้องการยกเลิก QR เนื่องจากยกเลิกการขาย หรือต้องการเปลี่ยนราคารับชำระใหม่ ทั้งนี้ต้องใช้หมายเลขรายการที่ต้องการยกเลิกด้วย เมื่อยกเลิกแล้ว QR นั้นจะไม่สามารถรับชำระได้

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_cancel
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
  https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_cancel \
  -H 'cache-control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid":"{{YOUR TXN ID}}",
    "partnerId":"{{YOUR PARTNER ID}}",
    "partnerSecret":"{{YOUR PARTNER SECRET}}",
    "requestDt": "2018-01-29T04:42:51Z",
    "merchantId": "PAR01000080170",
    "terminalId": null,
    "qrType": "3",
    "origPartnerTxnUid": "{{YOUR QR TXN ID}}"
  }'

---[Javascript/javascript]---
var request = require("request");

var options = {
  method: 'POST',
  url: 'https://APIPORTALTEST.kasikornbank.com:12002/pos/qr_cancel',
  headers: {
    'cache-control': 'no-cache',
    'Content-Type': 'application/json',
  },
  body: {
    partnerTxnUid: '{{YOUR TXN ID}}',
    partnerId: '{{YOUR PARTNER ID}}',
    partnerSecret: '{{YOUR PARTNER SECRET}}',
    requestDt: '2018-01-29T04:42:51Z',
    merchantId: 'PAR01000080170',
    terminalId: null,
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
