# **Credit Card API**

เพื่อดูข้อมูล 3 ประเภท คือ

1. จำนวนแต้มสะสมของบัตรเครดิต
2. แต้มคะแนนแลกสินค้าของบัตรเครดิต
3. รายการใช้จ่ายผ่านบัตรเครดิตที่ยังไม่ถึงรอบบิล

<br />

# Credit Card Point Redemption

**Description**

· แต้มคะแนนแลกสินค้าของบัตรเครดิต

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption
```

**Parameters**

| Field                        | Data Type | Description                                                                | Example          | Mandatory |
| ---------------------------- | --------- | -------------------------------------------------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                                        | application/json |     Y     |
| [colspan=5] Body parameter   |
| mobileNum                    | string    | เลขที่โทรศัพท์มือถือของลูกค้า ที่เปิดใช้บริการ KPlus และมีข้อมูลบัตรเครดิต | 1234567890       |     Y     |
| cardNum4Digits               | string    | เลขที่บัตรเครดิต 4 หลักสุดท้าย                                             | 5643             |     Y     |
| redemptionAmt                | decimal   | คะแนนของบัตรเครดิตใช้แลกสินค้า                                             | 100              |     Y     |

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X POST \
 https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption",
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
    "cardNumMask": "xxxx-xxxx-xxxx-5643",
    "redemptionAmt": 100,
    "pointBalance": 42603
}
```
