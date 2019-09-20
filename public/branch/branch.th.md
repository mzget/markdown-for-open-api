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
https://APIPORTAL.kasikornbank.com:12002/info/branch
```

**Example Request**

```bash
[GROUP][COPYABLE]
  ---[cURL/bash]---
curl -X GET \
  https://APIPORTAL.kasikornbank.com:12002/info/branch \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/info/branch",
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
            "branchCode": "0001",
            "branchNameTh": "สาขาสำนักสีลม",
            "branchNameEn": "SILOM MAIN",
            "addressTh": "142 ถนนสีลม แขวงสุริยวงศ์ เขตบางรัก กรุงเทพมหานคร 10500",
            "addressEn": "142 SILOM RD. SURIYAWONG BANG RAK BANGKOK 10500",
            "telephone": "0-2232-5001 FAX 0-2234-7445",
            "officeHour": "จันทร์-ศุกร์ 8.30-15.30 น. (เว้นวันหยุดธนาคาร)%MON-FRI 08.30-15.30 HRS (EXCEPT BANK HOLIDAYS)"
        },
        {
            "branchCode": "0002",
            "branchNameTh": "สาขาตลาดพลู",
            "branchNameEn": "TALAT PHLU",
            "addressTh": "1087 ถนนเทอดไท แขวงตลาดพลู เขตธนบุรี กรุงเทพมหานคร 10600",
            "addressEn": "1087 THOET THAI RD. TALAT PHLU THON BURI BANGKOK 10600",
            "telephone": "0-2891-4022-9 0-2891-4262-5 FAX 0-2891-4278",
            "officeHour": "จันทร์-ศุกร์ 8.30-15.30 น. (เว้นวันหยุดธนาคาร)%MON-FRI 08.30-15.30 HRS (EXCEPT BANK HOLIDAYS)"
        }
    ]
}
```
