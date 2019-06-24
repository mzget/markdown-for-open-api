# **Information**

เพื่อดูข้อมูล 3 ประเภท คือ

1. ข้อมูลและที่ตั้งตู้ ATM ธนาคารกสิกรไทย
2. ข้อมูลและที่ตั้งสาขาธนาคารกสิกรไทย
3. อัตราแลกเปลี่ยนต่างประเทศ
   <br />
   <br />

# Exchange Rate

**Description**

อัตราแลกเปลี่ยนต่างประเทศในสกุลบาท

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/info/fxrate/GBP
```

**Example Request**

```
[GROUP][COPYABLE]
  ---[cURL/curl]---
curl -X GET \
  https://APIPORTALTEST.kasikornbank.com:12002/info/fxrate/GBP \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/info/fxrate/GBP",
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
  "rates": [
    {
      "underlyingCurrency": "GBP",
      "description": "Pound Sterling",
      "baseCurrency": "THB",
      "denomination": null,
      "buy": {
        "travellercheque": 40.85379,
        "exportsightbill": 40.85379,
        "telextransfer": 40.99836,
        "banknotes": 40.41507
      },
      "sell": {
        "tt_draft_cheque": 41.84692,
        "banknotes": 41.63843
      }
    }
  ]
}
```
