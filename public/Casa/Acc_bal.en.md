# **Account / CASA**

For 2 types of information:

1. Recent Account Activities
2. Account Balance

<br />
<br />

# Account Balance

**Description**

· Display account balance of specified account no.
· Support both savings accounts and current accounts

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/1562567456
```

**Parameters**

| Field                        | Data Type | Description                         | Example          | Mandatory |
| ---------------------------- | --------- | ----------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json | application/json |     Y     |
| [colspan=5] URL parameter    |
| accId                        | string    | Account no.                         | 1562567456       |     Y     |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X GET \
 https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/{{YOUR PARAM}} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/deposit/sight/balance/{{YOUR PARAM}}",
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
    "data": {
        "availBalance": 112024.5,
        "acctBalance": 102024.5,
        "acctStatus": "Active"
    }
}
```
