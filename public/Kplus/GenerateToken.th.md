# Generate Token

**Description**

เพื่อสร้าง token ในการอ้างอิงรายการสั่งซื้อสินค้า ประกอบด้วย ราคาทั้งหมด จำนวน และข้อมูลเพิ่มเติม

<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kplus%2Fbanner-generate-token%402x.jpg?alt=media&token=c6bc55fd-6b29-4126-a9a7-ace52c15648c" alt="manage"  width="100%" height="100%"  style="object-fit: cover;" />

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/generate-token
```

**Request Parameters**

| Field                        | Data Type | Description                                | Example                                              | Mandatory |
| ---------------------------- | --------- | ------------------------------------------ | ---------------------------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json        | application/json                                     |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string    | ID ไม่ซ้ำเพื่อให้ทำรายการ                  | RGH001030118001                                      |     Y     |
| partnerId                    | string    | ID ของ Partner ที่ธนาคารกำหนดให้           | KP2XXX000033159                                      |     Y     |
| partnerSecret                | string    | secret key ของ PartnerId ที่ธนาคารกำหนดให้ | S1AyQ0ZCMDAwMDMzMTU5LWtwbHVzLXNpdC0yYzJwLWZhY2Vib29r |     Y     |
| requestDt                    | long      | เวลาที่ทำรายการ                            | 1519630776                                           |     Y     |
| reference1                   | string    | อ้างอิง1                                   |                                                      |     Y     |
| reference2                   | string    | อ้างอิง2                                   |                                                      |     N     |
| totalAmount                  | string    | จำนวนทั้งหมด                               | 000000005000 = 50.00THB                              |     Y     |
| shopImageUrl                 | string    | รูปของร้านค้า url                          |                                                      |     Y     |
| partnerIconUrl               | string    | รูปสัญลักษณ์ Partner url                   |                                                      |     N     |
| shopName                     | string    | ชื่อร้านค้า                                |                                                      |     Y     |
| shippingFee                  | string    | ค่าธรรมเนียมขนส่ง                          | 000000005000 = 50.00THB                              |     Y     |
| osPlatform                   | string    | ระบบปฏิบัติการ                             | IOS / ANDROID                                        |     Y     |
| items                        | array     | รายละเอียดรายการสั่งซื้อ                   |                                                      |     N     |
| items.itemName               | string    | ชื่อสินค้า                                 |                                                      |     N     |
| items.quantity               | number    | จำนวน                                      | 1                                                    |     N     |
| items.amount                 | string    | ราคา                                       | 000000005000 = 50.00THB                              |     N     |
| currencyCode                 | string    | สกุลเงิน                                   | THB                                                  |     Y     |
| currencyExponent             | string    | แปลงสกุลเงิน                               | 2                                                    |     Y     |
| buyerName                    | string    | ชื่อผู้ซื้อ                                |                                                      |     N     |
| partnerToken                 | string    | Token เครื่องแสดงเพื่อใช้ตรวจสอบรายการ     |                                                      |     N     |
| promotionCode                | string    | Key-in promotion code                      |                                                      |     N     |
| additionalInfo1              | string    | สำรองเพื่อข้อมูลเพิ่มเติม                  |                                                      |     N     |
| additionalInfo2              | string    | สำรองเพื่อข้อมูลเพิ่มเติม                  |                                                      |     N     |
| additionalInfo3              | string    | สำรองเพื่อข้อมูลเพิ่มเติม                  |                                                      |     N     |

**Response Message**

| Field          | Data Type | Description                      |
| -------------- | --------- | -------------------------------- |
| partnerTxnUid  | string    | ID ไม่ซ้ำเพื่อให้ทำรายการ        |
| partnerId      | string    | ID ของ Partner ที่ธนาคารกำหนดให้ |
| statusCode     | string    | สถานะรายการ                      |
| errorCode      | string    | เลขรหัสกรณีไม่สำเร็จ             |
| errorDesc      | string    | คำอธิบายกรณีไม่สำเร็จ            |
| callBackAppUrl | string    | URL สำหรับเปลี่ยนไปเรียก kplus   |
| tokenId        | string    | รหัสอ้างอิงการสั่งซื้อ           |
| expiryDate     | long      | วันที่หมดอายุ                    |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/generate-token \
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
  url: 'https://APIPORTALTEST.kasikornbank.com:12002/kplus/payment/generate-token',
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
