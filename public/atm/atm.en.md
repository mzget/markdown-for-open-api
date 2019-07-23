# **Information**

For 3 types of KBank information:

1. KBank ATM Location
2. KBank Branch Location
3. Exchange Rate
   <br />
   <br />

# KBank ATM Location

**Description**

Retrieve KBank ATM Location

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/info/atm
```

**Example Request**

```
[GROUP][COPYABLE]
  ---[cURL/curl]---
curl -X GET \
  https://APIPORTAL.kasikornbank.com:12002/info/atm \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/info/atm",
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
