# Transaction Verification

**Description**
Creditor bank (Receiving Bank) can verify payment transaction using unique reference from Debtor Bank (Sending Bank) where Bank account already been deducted from Debtor bank customer.

This API can rectify on the problem where customer already paid or transfer money to Creditor bank but money does not been added to Creditor bank customer, Creditor bank customer can verify and ensure that he/she will receive money from customer definitely.

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}
```

**Parameters**

| Field                        | Data Type | Description                         | Example            | Mandatory |
| ---------------------------- | --------- | ----------------------------------- | ------------------ | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json | application/json   |     Y     |
| Partner-Id                   | string    | Partner-Id                          |                    |     Y     |
| Partner-Secret               | string    | Partner-Secret                      |                    |     Y     |
| [colspan=5] query parameter  |
| sendingBank                  | string    | sending bank                        | 004                |     Y     |
| transref                     | string    | transaction reference               | 019182105907167129 |     Y     |

<br />

**TEST DATA**

| Field                                             | Value              |
| ------------------------------------------------- | ------------------ |
| [colspan=2] Dataset 1 (Online Fund Transfer)      |
| sendingBank                                       | 004                |
| transref                                          | 019182105907167129 |
| [colspan=2] Dataset 2 (PromptPay Transfer Mobile) |
| sendingBank                                       | 004                |
| transref                                          | 019183135058827134 |
| [colspan=2] Dataset 3 (Fund transfer)             |
| sendingBank                                       | 004                |
| transref                                          | 019183135540904172 |
| [colspan=2] Dataset 4 (Bill Payment)              |
| sendingBank                                       | 004                |
| transref                                          | 019183135837377182 |
| [colspan=2] Dataset 5 (Promptpay E-wallet)        |
| sendingBank                                       | 004                |
| transref                                          | 019183140443361142 |

<br />

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://APIPORTALTEST.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://APIPORTALTEST.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}",
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
    "transRef": "019182105907167129",
    "sendingBank": "004",
    "receivingBank": "069",
    "transDate": "20190705",
    "transTime": "08:12:36",
    "sender": {
        "displayName": "โพธิจันทร ธ",
        "name": "PHOTICHANTHON P",
        "account": {
            "type": "BANKAC",
            "value": "xxx-x-x7404-x"
        }
    },
    "receiver": {
        "displayName": "นาย คิทแคท ช",
        "name": "MR. KITKAT G",
        "account": {
            "type": "BANKAC",
            "value": "xxx-x-x7404-x"
        }
    },
    "amount": 21.0,
    "paidLocalAmount": 21.0,
    "transFeeAmount": 0.0,
    "ref1": null,
    "ref2": null,
    "ref3": null
}
```
