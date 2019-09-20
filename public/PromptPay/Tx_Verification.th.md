# Transaction Verification

**Description**

API นี้ใช้สำหรับตรวจสอบสถานะของการทำรายการนั้น โดยใช้ข้อมูลเป็น bank code ของธนาคารต้นทาง(Sending Bank) และ รหัสอ้างอิงของการทำรายการนั้นๆ(Transaction Reference)

```bash
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTAL.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}
```

**Parameters**

| Field                         | Data Type | Description                                                                                              | Example            | Mandatory |
| ----------------------------- | --------- | -------------------------------------------------------------------------------------------------------- | ------------------ | :-------: |
| [colspan=5] Header parameters |
| content-type                  | string    | Type of content as application/json                                                                      | application/json   |     Y     |
| Partner-Id                    | string    | Partner-Id                                                                                               |                    |     Y     |
| Partner-Secret                | string    | Partner-Secret                                                                                           |                    |     Y     |
| [colspan=5] URL parameters    |
| sendingBank                   | string    | sending bank                                                                                             | 004                |     Y     |
| transref                      | string    | Transaction Reference Number<br>Contains Reference number of the transaction required to verify the pay. | 019182105907167129 |     Y     |

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

```bash
[GROUP][COPYABLE]
---[cURL/bash]---
curl -X POST \
  https://APIPORTAL.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'

---[Javascript/javascript]---
$.ajax({
  "url": "https://APIPORTAL.kasikornbank.com:12002/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}",
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
  "language": "TH",
  "transRef": "019183135540904172",
  "sendingBank": "004",
  "receivingBank": "004",
  "transDate": "20190702",
  "transTime": "13:55:40",
  "sender": {
    "displayName": "ชิซูกะ ส",
    "name": "CHICHUKA S",
    "account": {
      "type": "BANKAC",
      "value": "xxx-x-x2295-x"
    },
    "proxy": {
      "type": null,
      "value": null
    }
  },
  "receiver": {
    "displayName": "โนบิตะ ส",
    "name": "NOBITA S",
    "account": {
      "type": "BANKAC",
      "value": "xxx-x-x1411-x"
    },
    "proxy": {
      "type": "",
      "value": ""
    }
  },
  "amount": 10.04,
  "paidLocalAmount": 10.04,
  "paidLocalCurrency": "764",
  "countryCode": "TH",
  "transFeeAmount": 0,
  "ref1": "",
  "ref2": "",
  "ref3": "",
  "toMerchantId": ""
}
```
