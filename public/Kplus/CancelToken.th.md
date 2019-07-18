# Cancel Token

**Description**

เพื่อยกเลิกรหัส Token

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/cancel-token
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
| reference1                   | string    | อ้างอิง1                                   |                                                      |     Y     |

**Response Message**

| Field                | Data Type | Description                      |
| -------------------- | --------- | -------------------------------- |
| partnerTxnUid        | string    | ID ไม่ซ้ำเพื่อให้ทำรายการ        |
| partnerId            | string    | ID ของ Partner ที่ธนาคารกำหนดให้ |
| statusCode           | string    | สถานะรายการ                      |
| errorCode            | string    | เลขรหัสกรณีไม่สำเร็จ             |
| errorDesc            | string    | คำอธิบายกรณีไม่สำเร็จ            |
| tokenList            | array     | รายการ รายละเอียด token          |
| tokenList.tokenId    | string    | อ้างอิงการสั่งซื้อ               |
| tokenList.reference1 | string    | อ้างอิง1                         |
| tokenList.status     | array     | สถานะ token                      |

**Example Request**

```code
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://203.146.225.57:12002/kplus/payment/cancel-token \
  -H 'Content-Type: application/json' \
  -d '{
    "partnerTxnUid": "transIrtses152",
    "partnerId":"PTR1902369",
    "partnerSecret":"7da57c4eb242435fa3e91bb7a69e2a28",
    "requestDt": "2019-07-04T18:00:42.411",
    "tokenId": "KMCMPTzpjbelgdzimkogvbmhxyutxytahzyqglfjenb1624PMT",
    "reference1":"av"
}'
---[JS/javascript]---
$.ajax({
  method: 'POST',
  url: 'https://203.146.225.57:12002/kplus/payment/cancel-token',
  headers:
   { 'Content-Type': 'application/json' },
  body:
   { partnerTxnUid: 'transIrtses152',
     partnerId: 'PTR1902369',
     partnerSecret: '7da57c4eb242435fa3e91bb7a69e2a28',
     requestDt: '2019-07-04T18:00:42.411',
     tokenId: 'KMCMPTzpjbelgdzimkogvbmhxyutxytahzyqglfjenb1624PMT',
     reference1: 'av' }
});
```

**Example Response**

```json
{
    "partnerId": "PTR1902369",
    "partnerTxnUid": "transIrtses152",
    "errorCode": null,
    "errorDesc": null,
    "statusCode": "00",
    "tokenList": [
        {
            "tokenId": "KMCMPTzpjbelgdzimkogvbmhxyutxytahzyqglfjenb1624PMT",
            "reference1": "KS1234567",
            "status": "CANCELLED"
        }
    ]
}
```
