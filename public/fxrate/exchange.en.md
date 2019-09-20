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
https://APIPORTAL.kasikornbank.com:12002/info/fxrate
```

**Example Request**

```bash
[GROUP][COPYABLE]
  ---[cURL/bash]---
curl -X GET \
  https://APIPORTAL.kasikornbank.com:12002/info/fxrate \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/info/fxrate",
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
            "underlyingCurrency": "AED",
            "descriptionCurrency": "UAE Dirham",
            "baseCurrency": "THB",
            "denomination": null,
            "buy": {
                "travellercheque": null,
                "exportsightbill": 8.276,
                "telextransfer": 8.276,
                "banknotes": 7.2275
            },
            "sell": {
                "tt_draft_cheque": 9.10173,
                "banknotes": 9.13294
            }
        },
        {
            "underlyingCurrency": "AUD",
            "descriptionCurrency": "Australian Dollar",
            "baseCurrency": "THB",
            "denomination": null,
            "buy": {
                "travellercheque": 22.17275,
                "exportsightbill": 22.17275,
                "telextransfer": 22.25242,
                "banknotes": 21.97155
            },
            "sell": {
                "tt_draft_cheque": 23.211695,
                "banknotes": 23.41761
            }
        }
    ]
}
```
