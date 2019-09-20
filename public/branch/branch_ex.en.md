# **Information**

For 3 types of KBank information:

1. KBank ATM Location
2. KBank Branch Location
3. Exchange Rate

<br />

# KBank Branch Location

**Description**

Retrieve KBank Branch Location

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/info/branch/0012
```

**Example Request**

```bash
[GROUP][COPYABLE]
  ---[cURL/bash]---
curl -X GET \
  https://APIPORTAL.kasikornbank.com:12002/info/branch/0012 \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/info/branch/0012",
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
