# **QR Payment API**

ใช้เมื่อร้านค้าต้องการรับชำระเงินผ่าน Thai QR จากลูกค้า QR ที่สร้างขึ้นจะเป็น Dynamic QR (ร้านค้าสามารถกำหนดยอดเงินได้ แต่ลูกค้าไม่สามารถแก้ไขได้) โดย QR ที่สร้างขึ้นจะมีอายุ 10 นาที
<br />

# Payment Notification Callback

**Description**

เมื่อลูกค้าชำระเงินผ่านแอพลิเคชันเรียบร้อยแล้ว ทางเราจะส่ง Notification ไปยังร้านค้า (ไม่สามารถทดลองใช้ใน Webportal ได้)

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://yourdomain.com/qr/payment-callback
```

**Callback Parameters**

| Field                        | Data Type   | Description                                                                                | Example          | Mandatory |
| ---------------------------- | ----------- | ------------------------------------------------------------------------------------------ | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string      | Type of content as application/json                                                        | application/json |     Y     |
| [colspan=5] Body parameter   |
| partnerTxnUid                | string(15)  | ID to uniquely define each request from partner                                            | RGH001030118001  |     Y     |
| partnerId                    | string(10)  | Partner identifier. This ID will be provided to each partner by KBank                      | POS001           |     Y     |
| statusCode                   | string(2)   | Status code. Success(00), Error(10) (Please refer to Appendix)                             | 00               |     Y     |
| errorCode                    | string(35)  | Code to identify the error.                                                                | 00               |     Y     |
| errorDesc                    | string(100) | Description of the error.                                                                  | 00               |     Y     |
| merchantId                   | string(14)  | Shop's merchant ID in KBank's system                                                       | BEV06000080200   |    Y/N    |
| txnAmount                    | number      | Amount of transaction. Must be positive number. Number of digits depends on each currency. | 100.50           |    Y/N    |
| txnCurrencyCode              | string(3)   | Currency code of transaction amount in ISO 4217. Currently support only "THB"              | THB              |    Y/N    |
| txnNo                        | string(20)  | Customer payment transaction no                                                            | 201802080035496  |    Y/N    |
| loyaltyId                    | string(15)  | Loyalty or member card ID from K PLUS                                                      | 00199100000      |     N     |
| additionalInfo               | string(150) | Additional Info                                                                            | Additional Info  |     N     |

**Example Callback Parameters**

```json
{
    "partnerTxnUid": "QRH001030118001",
    "partnerId": "POS001",
    "statusCode": "00",
    "errorCode": null,
    "errorDesc": null,
    "merchantId": "BEV06000080200",
    "txnAmount": 100.5,
    "txnCurrencyCode": "THB",
    "loyaltyId": "00199100000",
    "txnNo": "201802080035496",
    "additionalInfo": "ข้อมูลประกอบอื่น ๆ"
}
```

---

**Return Parameters**

| Field                        | Data Type   | Description                                                    | Example          | Mandatory |
| ---------------------------- | ----------- | -------------------------------------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string      | Type of content as application/json                            | application/json |     Y     |
| [colspan=5] Body parameter   |
| statusCode                   | string(2)   | Status code. Success(00), Error(10) (Please refer to Appendix) | 00               |     Y     |
| errorCode                    | string(35)  | Code to identify the error.                                    | 00               |     Y     |
| errorDesc                    | string(100) | Description of the error.                                      | 00               |     Y     |

**Example Return Parameters**

```json
{
    "statusCode": "00",
    "errorCode": null,
    "errorDesc": null
}
```
