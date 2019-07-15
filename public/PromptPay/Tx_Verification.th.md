# Transaction Verification
**Description**

API นี้ใช้สำหรับตรวจสอบสถานะของการทำรายการนั้น โดยใช้ข้อมูลเป็น bank code ของธนาคารต้นทาง(Sending Bank) และ รหัสอ้างอิงของการทำรายการนั้นๆ(Transaction Reference)

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://kbankapi.tech/v1/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}
```

**Parameters**

| Field                        | Data Type | Description                                                  | Example          | Mandatory |
| ---------------------------- | --------- | ------------------------------------------------------------ | ---------------- | :-------: |
| [colspan=5] Header parameter |
| content-type                 | string    | Type of content as application/json                          | application/json |     Y     |
| Partner-Id                   | string    | Partner-Id     						                      |  				 |     Y     |
| Partner-Secret               | string    | Partner-Secret                                               |    				 |     Y     |
| [colspan=5] query parameter  |
| sendingBank                  | string    | sending bank 												  | 004		         |     Y     |
| transref 			           | string    | transaction reference                          			  | 019182105907167129 |     Y     |

<br />

**TEST DATA**

| Field                        | Value |
| ---------------------------- | --------- |
| [colspan=2] Dataset 1 (Online Fund Transfer)  |
| sendingBank        	       | 004 |
| transref                     | 019182105907167129 |
| [colspan=2] Dataset 2 (PromptPay_Transfer_Mobile)	   |
| sendingBank        	       | 004 |
| transref                     | 019183135058827134 |
| [colspan=2] Dataset 3	(Fund transfer)	   |
| sendingBank        	       | 004 |
| transref                     | 019183135540904172 |
| [colspan=2] Dataset 4 (Bill_Payment)	   |
| sendingBank        	       | 004 |
| transref                     | 019183135837377182 |
| [colspan=2] Dataset 5 (Promptpay E-wallet)	   |
| sendingBank        	       | 004 |
| transref                     | 019183140443361142 |

<br />

**Example Request**

```
[GROUP][COPYABLE]
---[cURL/curl]---
curl -X POST \
  https://kbankapi.tech/v1/promptpay/transactions?sendingBank={sendingBank}&transref={transRef} \
  -H 'cache-control': 'no-cache' \
  -H 'Partner-Id': '{{YOUR PARTNER ID}}' \
  -H 'Partner-Secret': '{{YOUR PARTNER SECRET}}'
---[JS/javascript]---
$.ajax({
  "url": "https://kbankapi.tech/v1/promptpay/transactions?sendingBank={sendingBank}&transref={transRef}",
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
    "amount": 21.00,
    "paidLocalAmount": 21.00,
    "transFeeAmount": 0.00,
    "ref1": null,
    "ref2": null,
    "ref3": null
}

```
