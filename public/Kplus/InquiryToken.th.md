# Inquiry Token Status

**Description**

เพื่อดูสถานะของรหัส Token

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/inquire-token
```

**Request Parameters**

| Field                        | Data Type | Description                                | Example                                              | Mandatory |
| ---------------------------- | --------- | ------------------------------------------ | ---------------------------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json        | application/json                                     |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string    | ID ไม่ซ้ำเพื่อให้ทำรายการ                  | RGH001030118001                                      |     Y     |
| partnerId                    | string    | ID ของ Partner ที่ธนาคารกำหนดให้           | KP2XXX000033159                                      |     Y     |
| partnerSecret                | string    | Secret key ของ PartnerId ที่ธนาคารกำหนดให้ | S1AyQ0ZCMDAwMDMzMTU5LWtwbHVzLXNpdC0yYzJwLWZhY2Vib29r |     Y     |
| requestDt                    | long      | เวลาที่ทำรายการ                            | 1519630776                                           |     Y     |
| tokenId                      | string    | อ้างอิงการสั่งซื้อ                         | KP2XXX00003315900BBC3C374D644DE9F2BA5CDC189C27B      |     Y     |

**Response Message**

| Field             | Data Type    | Description                                 |
| ----------------- | ------------ | ------------------------------------------- |
| partnerTxnUid     | string       | ID ไม่ซ้ำเพื่อให้ทำรายการ                   |
| partnerId         | string       | ID ของ Partner ที่ธนาคารกำหนดให้            |
| statusCode        | string       | สถานะรายการ                                 |
| errorCode         | string       | เลขรหัสกรณีไม่สำเร็จ                        |
| errorDesc         | string       | คำอธิบายกรณีไม่สำเร็จ                       |
| paymentStatus     | string       | สถานะการชำระ                                |
| paymentTimeStamp  | long         | วันและเวลาชำระ                              |
| paymentRefernceId | string       | ใช้อ้างอิงการชำระ                           |
| slipImage         | binaryBase64 | รูปใบเสร็จชำระ                              |
| paymentAccount    | string       | เลขที่บัญชีที่ชำระรายการ แบบแสดงไม่เต็มหลัก |
| paymentDt         | long         | วันที่และเวลา                               |
| reference1        | string       | อ้างอิง1                                    |
| reference2        | string       | อ้างอิง2                                    |
| totalAmount       | string       | จำนวนทั้งหมด                                |
| currencyCode      | string       | สกุลเงิน                                    |
| currencyExponent  | string       | แปลงสกุลเงิน                                |
| tokenId           | string       | อ้างอิงการสั่งซื้อ                          |
| additionalInfo1   | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |
| additionalInfo2   | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |
| additionalInfo3   | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |

**Example Request**

```code
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
   https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/inquire-token \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid": "transIrtses222",
    "partnerId":"PTR1902369",
    "partnerSecret":"7da57c4eb242435fa3e91bb7a69e2a28",
    "requestDt": "2019-07-04T18:00:42.411",
    "tokenId": "KMCMPTtbbibmvyvnutyyknckxtngiwaklpcjptykxon34f8PMT"
}'
---[JS/javascript]---
$.ajax({
  method: 'POST',
  url: 'https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/inquire-token',
  headers:
   { 'Content-Type': 'application/json' },
  body:
   { partnerTxnUid: 'transIrtses222',
     partnerId: 'PTR1902369',
     partnerSecret: '7da57c4eb242435fa3e91bb7a69e2a28',
     requestDt: '2019-07-04T18:00:42.411',
     tokenId: 'KMCMPTtbbibmvyvnutyyknckxtngiwaklpcjptykxon34f8PMT' }
});
```

**Example Response**

```json
{
    "partnerId": "PTR1902369",
    "partnerTxnUid": "transIrtses222",
    "errorCode": null,
    "errorDesc": null,
    "statusCode": "00",
    "paymentStatus": "PAID",
    "paymentTimeStamp": null,
    "paymentRefernceId": null,
    "slipImage": null,
    "paymentAccount": null,
    "paymentDt": "2019-07-11T13:53:04",
    "reference1": "KS1234567",
    "reference2": "",
    "totalAmount": 500,
    "currencyCode": "THB",
    "currencyExponent": null,
    "tokenId": "KMCMPTtbbibmvyvnutyyknckxtngiwaklpcjptykxon34f8PMT",
    "additionalInfo1": null,
    "additionalInfo2": null,
    "additionalInfo3": null
}
```
