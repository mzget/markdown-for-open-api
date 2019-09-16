# **Information**

For 3 types of KBank information:

1. KBank ATM Location
2. KBank Branch Location
3. Exchange Rate

<br />

# Exchange Rate

**Description**

Retrieve exchange rate information between THB and given currency.

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/info/fxrate/GBP
```

**Example Request**

```bash
[GROUP][COPYABLE]
  ---[cURL/bash]---
curl -X GET \
  https://APIPORTALTEST.kasikornbank.com:12002/info/fxrate/GBP \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
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
