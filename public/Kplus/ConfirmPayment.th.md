# Confirm Payment

**Description**

เพื่อยืนยันการชำระเงินไปยังระบบของ Partner

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://yourdomain.com/kplus/payment-callback
```

**Callback Parameters**

| Field                      | Data Type    | Description                                 | Example                                              | Mandatory |
| -------------------------- | ------------ | ------------------------------------------- | ---------------------------------------------------- | :-------: |
| [colspan=5] Body parameter |
| partnerTxnUid              | string       | ID ไม่ซ้ำเพื่อให้ทำรายการ                   | RGH001030118001                                      |     Y     |
| partnerId                  | string       | ID ของ Partner ที่ธนาคารกำหนดให้            | KP2XXX000033159                                      |     Y     |
| partnerSecret              | string       | secret key ของ PartnerId ที่ธนาคารกำหนดให้  | S1AyQ0ZCMDAwMDMzMTU5LWtwbHVzLXNpdC0yYzJwLWZhY2Vib29r |     Y     |
| requestDt                  | long         | เวลาที่ทำรายการ                             | 1519630776                                           |     Y     |
| reference1                 | string       | อ้างอิง1                                    |                                                      |     Y     |
| reference2                 | string       | อ้างอิง2                                    |                                                      |     N     |
| totalAmount                | string       | จำนวนทั้งหมด                                | 000000005000 = 50.00THB                              |     Y     |
| slipImage                  | binaryBase64 | รูปใบเสร็จชำระ                              |                                                      |     Y     |
| paymentRefernceId          | string       | ใช้อ้างอิงการชำระ                           | 170621063616352                                      |     Y     |
| paymentAccount             | string       | เลขที่บัญชีที่ชำระรายการ แบบแสดงไม่เต็มหลัก | x-x-x0055-x                                          |     N     |
| paymentDt                  | long         | วันที่และเวลา                               | 1519630776                                           |     Y     |
| currencyCode               | string       | สกุลเงิน                                    | THB                                                  |     Y     |
| currencyExponent           | string       | แปลงสกุลเงิน                                | 2                                                    |     Y     |
| tokenId                    | string       | อ้างอิงการสั่งซื้อ                          | KP2XXX00003315900BBC3C374D644DE9F2BA5CDC189C27B      |     Y     |
| additionalInfo1            | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |                                                      |     N     |
| additionalInfo2            | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |                                                      |     N     |
| additionalInfo3            | string       | สำรองเพื่อข้อมูลเพิ่มเติม                   |                                                      |     N     |

**Return Parameters**

| Field         | Data Type | Description                      |
| ------------- | --------- | -------------------------------- |
| partnerTxnUid | string    | ID ไม่ซ้ำเพื่อให้ทำรายการ        |
| partnerId     | string    | ID ของ Partner ที่ธนาคารกำหนดให้ |
| statusCode    | string    | สถานะรายการ                      |
| errorCode     | string    | เลขรหัสกรณีไม่สำเร็จ             |
| errorDesc     | string    | คำอธิบายกรณีไม่สำเร็จ            |
