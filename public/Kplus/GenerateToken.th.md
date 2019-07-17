# Generate Token

**Description**

เพื่อสร้าง token ในการอ้างอิงรายการสั่งซื้อสินค้า ประกอบด้วย ราคาทั้งหมด จำนวน และข้อมูลเพิ่มเติม

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://kbankapi.tech/v1/kplus/payment/generate-token
```

**Request Parameters**

| Field                        | Data Type | Description                                | Example                                              | Mandatory |
| ---------------------------- | --------- | ------------------------------------------ | ---------------------------------------------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json        | application/json                                     |     Y     |
| Partner-Id                   | string    | Partner-Id                                 |                                                      |     Y     |
| Partner-Secret               | string    | Partner-Secret                             |                                                      |     Y     |
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
| items.amount                 | string    | ราคา                                       | 000000005000 = 50.00THB                              |     Y     |
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
