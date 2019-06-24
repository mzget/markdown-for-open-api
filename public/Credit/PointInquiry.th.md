# **Credit Card API**

เพื่อดูข้อมูล 3 ประเภท คือ

1. จำนวนแต้มสะสมของบัตรเครดิต
2. แต้มคะแนนแลกสินค้าของบัตรเครดิต
3. รายการใช้จ่ายผ่านบัตรเครดิตที่ยังไม่ถึงรอบบิล

<br />
<br />

# Credit Card Point Inquiry

**Description**

· เรียกดูจำนวนแต้มสะสมของบัตรเครดิตที่ระบุ

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry
```

**Parameters**

| Field                        | Data Type | Description                                                                | Example          | Mandatory |
| ---------------------------- | --------- | -------------------------------------------------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                                        | application/json |     Y     |
| [colspan=5] Body parameter   |
| mobileNum                    | string    | เลขที่โทรศัพท์มือถือของลูกค้า ที่เปิดใช้บริการ KPlus และมีข้อมูลบัตรเครดิต | 1234567890       |     Y     |
| cardNum4Digits               | string    | เลขที่บัตรเครดิต 4 หลักสุดท้าย                                             | 5643             |     Y     |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry",
  "method": "POST",
  "headers": {
    'cache-control': 'no-cache',
    'Partner-Id': '{{YOUR PARTNER ID}}',
    'Partner-Secret': '{{YOUR PARTNER SECRET}}'
  },
  });
```

**Example Response**

```json
{
  "data": {
    "cardNumMask": "xxxx-xxxx-xxxx-5643",
    "pointBalance": 42603
  }
}
```
