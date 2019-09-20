# **Account / CASA**

For 2 types of information:

1. Recent Account Activities
2. Account Balance

<br />

# Recent Account Activities

**Description**

· Retrieve account transaction history of specified account no.
· Able to display up to 200 transactions or up to last 3 months
· Support both savings accounts and current accounts

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/deposit/sight/transactions/1562567456
```

**Parameters**

| Field                        | Data Type | Description                         | Example          | Mandatory |
| ---------------------------- | --------- | ----------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json | application/json |     Y     |
| [colspan=5] URL parameter    |
| accId                        | string    | Account no.                         | 1562567456       |     Y     |

**Example Request**

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X GET \
 https://APIPORTAL.kasikornbank.com:12002/deposit/sight/transactions/{{YOUR PARAM}} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/deposit/sight/transactions/{{YOUR PARAM}}",
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
        "totalItems": 127,
        "items": [
            {
                "toAccountName": null,
                "channelDetail": null,
                "merchantCode": null,
                "toAccountNameEN": "KONKAMHOY NANTHAWAN",
                "fromAccountId": null,
                "outstandingBalance": 42603.82,
                "fromBankCode": null,
                "txnTime": "17:54:49",
                "txnAmount": 286,
                "fromAccountNameTH": null,
                "toAccountNo": "0991328424",
                "feeAmount": null,
                "serviceBranchNo": "0923",
                "txnDescEN": "Transfer Withdrawal ",
                "fromAccountNameEN": null,
                "effectiveDate": "2017-05-12",
                "toAccountNameTH": "ก้อนคำฮ้อย นันทวัลลภ์",
                "channelCode": "0923",
                "txnDate": "2017-05-12",
                "txnDesc": "โอนเงิน",
                "chequeNo": "00000000",
                "proxyId": null,
                "proxyTypeCode": null,
                "toBankCode": null,
                "tellerId": "KMP00001",
                "debitCreditFlag": "DR"
            }
        ]
    }
}
```
