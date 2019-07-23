# **Credit Card API**

For 3 types of information:

1. Credit Card Point Inquiry
2. Credit Card Point Redemption
3. Credit Card Unbilled Transactions Inquiry

<br />
<br />

# Credit Card Point Redemption

**Description**

· Display the redemption point of the credit card

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption
```

**Parameters**

| Field                        | Data Type | Description                                                  | Example          | Mandatory |
| ---------------------------- | --------- | ------------------------------------------------------------ | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                          | application/json |     Y     |
| [colspan=5] Body parameter   |
| mobileNum                    | string    | Customer’s mobile no. that has KPlus and credit card account | 1234567890       |     Y     |
| cardNum4Digits               | string    | Last 4 digits of credit card number                          | 5643             |     Y     |
| redemptionAmt                | decimal   | Point is redemption for Credit Card number                   | 100              |     Y     |

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/creditcard/point/redemption",
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
    "cardNumMask": "xxxx-xxxx-xxxx-5643",
    "redemptionAmt": 100,
    "pointBalance": 42603
}
```
