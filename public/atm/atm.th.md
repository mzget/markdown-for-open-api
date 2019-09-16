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
https://APIPORTALTEST.kasikornbank.com:12002/info/atm
```

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X GET \
  https://APIPORTALTEST.kasikornbank.com:12002/info/atm \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/info/atm",
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
      "atmCode": "CDM04721",
      "locationGr": "Branch",
      "branchTh": "สาขาบิ๊กซี สุขสวัสดิ์ เครื่อง 1 (ฝาก/ถอน)",
      "branchEn": "BIG C SUKSAWAT BRANCH #1(Deposit/Withdraw)",
      "roadTh": "ถนนสุขสวัสดิ์",
      "roadEn": "SUK SAWAT RD.",
      "addressTh": "สาขา บิ๊กซี สุขสวัสดิ์ เครื่อง 1 (ฝาก/ถอน)",
      "addressEn": "BIG C SUKSAWAT BRANCH #1(Deposit/Withdraw)",
      "province": "สมุทรปราการ:SAMUT PRAKAN",
      "amphur": "พระประแดง:PHRA PRADAENG"
    },
    {
      "atmCode": "CDM04722",
      "locationGr": "Branch",
      "branchTh": "สาขาสำนักถนนเสือป่า เครื่อง 1 (ฝาก/ถอน)",
      "branchEn": "THANON SUA PA MAIN BRANCH #1(Deposit/Withdraw)",
      "roadTh": "ถนนเสือป่า",
      "roadEn": "SUEA PA RD.",
      "addressTh": "สาขาสำนักถนนเสือป่า เครื่อง 1 (ฝาก/ถอน)",
      "addressEn": "THANON SUA PA MAIN BRANCH #1(Deposit/Withdraw)",
      "province": "กรุงเทพมหานคร:BANGKOK",
      "amphur": "ป้อมปราบศัตรูพ่าย:POM PRAP SATTRU PHAI"
    }
  ]
}
```
