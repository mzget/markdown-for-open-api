# **Credit Card API**

เพื่อดูข้อมูล 3 ประเภท คือ

1. จำนวนแต้มสะสมของบัตรเครดิต
2. แต้มคะแนนแลกสินค้าของบัตรเครดิต
3. รายการใช้จ่ายผ่านบัตรเครดิตที่ยังไม่ถึงรอบบิล

<br />

# Credit Card Unbilled Transactions Inquiry

**Description**

· แสดงรายการใช้จ่ายผ่านบัตรเครดิต ที่ยังไม่ถึงรอบบิล

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/creditcard/transactions/unbilled
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

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X POST \
 https://APIPORTAL.kasikornbank.com:12002/creditcard/transactions/unbilled \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/creditcard/transactions/unbilled",
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
    "nextStmtDate": "2019-05-25",
    "totalItems": 10,
    "stmtInfos": [
      {
        "creditCardType": "500",
        "tranCode": "40",
        "tranAmt": 2000,
        "tranDate": "2019-05-10",
        "postDate": "2019-05-04",
        "srcTranCode": "0000",
        "tranDesc": "EDC.TEST 2(NORMAL) BANGKOK TH",
        "orgCurrcyCode": "000",
        "orgCurrAmt": "0.00"
      },
      {
        "creditCardType": "500",
        "tranCode": "50",
        "tranAmt": 1000,
        "tranDate": "2019-05-12",
        "postDate": "2019-05-06",
        "srcTranCode": "0000",
        "tranDesc": "EDC.TEST 1(NORMAL) BANGKOK TH",
        "orgCurrcyCode": "000",
        "orgCurrAmt": "0.00"
      },
      … more
    ]
  }
}
```
