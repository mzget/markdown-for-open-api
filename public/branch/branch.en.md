# **Information**

For 3 types of KBank information:

1. KBank ATM Location
2. KBank Branch Location
3. Exchange Rate
   <br />
   <br />

# KBank Branch Location

**Description**

Retrieve KBank Branch Location

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/info/branch
```

**Example Request**

```
[GROUP][COPYABLE]
  ---[cURL/curl]---
curl -X GET \
  https://APIPORTALTEST.kasikornbank.com:12002/info/branch \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/info/branch",
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
