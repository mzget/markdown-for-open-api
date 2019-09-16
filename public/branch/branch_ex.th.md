# **Information**

เพื่อดูข้อมูล 3 ประเภท คือ

1. ข้อมูลและที่ตั้งตู้ ATM ธนาคารกสิกรไทย
2. ข้อมูลและที่ตั้งสาขาธนาคารกสิกรไทย
3. อัตราแลกเปลี่ยนต่างประเทศ

<br />

# KBank Branch Location

**Description**

ค้นหาข้อมูลและที่ตั้งสาขาธนาคารกสิกรไทย

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/info/branch/0012
```

**Example Request**

```bash
[GROUP][COPYABLE]
  ---[cURL/bash]---
curl -X GET \
  https://APIPORTALTEST.kasikornbank.com:12002/info/branch/0012 \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/info/branch/0012",
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
  "branches": [
    {
      "branchCode": "0012",
      "branchNameTh": "สาขามหาพฤฒาราม",
      "branchNameEn": "MAHA PHRUTTHARAM",
      "addressTh": "367, 369, 371 ถนนมหาพฤฒาราม แขวงมหาพฤฒาราม เขตบางรัก กรุงเทพมหานคร 10500",
      "addressEn": "367, 369, 371, MAHA PHRUTTHARAM RD. MAHA PHRUTTHARAM BANG RAK BANGKOK 10500",
      "telephone": "0-2639-0740-9 FAX 0-2236-5566",
      "officeHour": "จันทร์-ศุกร์ 8.30-15.30 น. (เว้นวันหยุดธนาคาร)%MON-FRI 08.30-15.30 HRS (EXCEPT BANK HOLIDAYS)"
    }
  ]
}
```
