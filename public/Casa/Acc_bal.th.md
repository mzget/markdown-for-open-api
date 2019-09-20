# **Account / CASA**

เพื่อดูข้อมูล 2 ประเภท คือ

1. รายการข้อมูลการเดินบัญชีย้อนหลัง
2. ยอดเงินของบัญชี

<br />

# Account Balance

**Description**

· แสดงยอดจำนวนเงินของเลขที่บัญชีที่ระบุ
· รองรับบัญชีประเภทเงินฝากออมทรัพย์ และกระแสรายวัน

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/1562567456
```

**Parameters**

| Field                        | Data Type | Description                         | Example          | Mandatory |
| ---------------------------- | --------- | ----------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json | application/json |     Y     |
| [colspan=5] URL parameter    |
| accId                        | string    | Account no.                         | 1562567456       |     Y     |

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X GET \
 https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/{{YOUR PARAM}} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/{{YOUR PARAM}}",
  "method": "GET",
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
        "availBalance": 112024.5,
        "acctBalance": 102024.5,
        "acctStatus": "Active"
    }
}
```
