# **Credit Card API**

For 3 types of information:

1. Credit Card Point Inquiry
2. Credit Card Point Redemption
3. Credit Card Unbilled Transactions Inquiry

<br />

# Credit Card Point Inquiry

**Description**

· Inquire the point balance of the credit card

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry
```

**Parameters**

| Field                        | Data Type | Description                                                  | Example          | Mandatory |
| ---------------------------- | --------- | ------------------------------------------------------------ | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                          | application/json |     Y     |
| [colspan=5] Body parameter   |
| mobileNum                    | string    | Customer’s mobile no. that has KPlus and credit card account | 1234567890       |     Y     |
| cardNum4Digits               | string    | Last 4 digits of credit card number                          | 5643             |     Y     |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/creditcard/point/inquiry",
  "method": "POST",
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
    "cardNumMask": "xxxx-xxxx-xxxx-5643",
    "pointBalance": 42603
  }
}
```
