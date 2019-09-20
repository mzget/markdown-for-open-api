# **Information**

เพื่อดูข้อมูล 3 ประเภท คือ

1. ข้อมูลและที่ตั้งตู้ ATM ธนาคารกสิกรไทย
2. ข้อมูลและที่ตั้งสาขาธนาคารกสิกรไทย
3. อัตราแลกเปลี่ยนต่างประเทศ

<br />

# KBank ATM Location

**Description**

ค้นหาข้อมูลและที่ตั้งตู้ ATM ธนาคารกสิกรไทย

```code
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/info/atm/CDM04723
```

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X GET \
  https://APIPORTAL.kasikornbank.com:12002/info/atm/CDM04723 \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/info/atm/CDM04723",
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
    "atms": [
        {
            "atmCode": "CDM04723",
            "locationGr": "MiniBranch",
            "branchTh": "ศูนย์แพลทตินั่มพหลโยธิน ชั้น 2 (ฝาก)",
            "branchEn": "PHAHON YOTHIN MAIN BRANCH Fl.2",
            "roadTh": "ถนนพหลโยธิน",
            "roadEn": "PHAHON YOTHIN RD.",
            "addressTh": "ศูนย์แพลทตินั่มพหลโยธิน ชั้น 2 (ฝาก)",
            "addressEn": "PHAHON YOTHIN MAIN BRANCH Fl.2",
            "province": "กรุงเทพมหานคร:BANGKOK",
            "amphur": "พญาไท:PHAYA THAI"
        }
    ]
}
```
