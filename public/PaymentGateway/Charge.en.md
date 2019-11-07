# Charge API

---

### Description

After you collect data and tokenize your customer’s credit card, you can charge the card immediately.
Unlike tokenization, which occurs in the browser, charge attempts are made from your server.

<br/>

```
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/kpgw/card/v1/charge
```

---

<strong>For Open API (Sandbox), Verify case (Only success)</strong>

1.  Verify Response Object (Credit Card & Thai QR)

| Attitude Name       | Data type     | Description                                                                                                                                                                                                                                                                                                                                           |
| ------------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                  | varchar(100)  | Charge ID Data.<br/>Sample Data: "chrg_test_12345678"                                                                                                                                                                                                                                                                                                 |
| object              | String        | Object type Data.<br/>Sample Data: "charge"                                                                                                                                                                                                                                                                                                           |
| amount              | Decimal(12,2) | The amount charged in currency unit.<br/>Sample Data: 200.50                                                                                                                                                                                                                                                                                          |
| currency            | varchar(50)   | 3 Letter ISO Currency code in upper case.<br/>Sample Data: "THB", "JPY" etc                                                                                                                                                                                                                                                                           |
| transaction_state   | varchar(50)   | The status of payment transaction. <br/>**Authorized** - Completely, authorize process with issue bank and Acquiring bank are captured a customer balance for purchase.<br/>**Declined** - Authorize process with issue bank. It not unsuccessful and reject payment.<br/>**Reversed** - Pre-Authorized - Payment need to do authentication 3D secure |
| source/id           | varchar(50)   | Card object ID<br/>Sample Data:"card_test_42f00571ac396ad600ce8e72b0e58def1"                                                                                                                                                                                                                                                                          |
| source/object       | varchar(10)   | Object type<br/>Sample Data: "card"                                                                                                                                                                                                                                                                                                                   |
| source/brand        | varchar(10)   | Card brand<br/>Sample Data: "MASTERCARD", "JCB", "VISA" etc.                                                                                                                                                                                                                                                                                          |
| source/card_masking | varchar(16)   | Masked card number<br/>Sample Data: "514950xxxxxx9007"                                                                                                                                                                                                                                                                                                |
| source/issuer_bank  | varchar(56)   | Card issuer bank name<br/>Sample Data: "Kasikornbank Public Limited"                                                                                                                                                                                                                                                                                  |
| created             | varchar(17)   | Creation date of the charge<br/>Format: YYYYMMDDHHmmSS<br/>Sample Data: "20180322121944000"                                                                                                                                                                                                                                                           |
| status              | varchar       | Whether the charge is authorized or not<br/>Sample Data: "status": "success"                                                                                                                                                                                                                                                                          |
| livemode            | Boolean       | Whether this is live environment (true) or not (false)<br/>Sample Data: "livemode": true                                                                                                                                                                                                                                                              |
| approval_code       | varchar(20)   | Authorization’s approval code from Issuer<br/>Data Type: String (20)<br/>Sample Data: "approval_code": "123456"                                                                                                                                                                                                                                       |
| failure_code        | varchar(256)  | Failure code returned when there is an error                                                                                                                                                                                                                                                                                                          |
| failure_message     | varchar(256)  | Failure description returned when there is an error                                                                                                                                                                                                                                                                                                   |

<br/>

**Pay with Payment UI.**

The following example applies for credit card payments using a Payment UI at token.

_Sample Request_

```bash
curl -X POST \
  -H 'Content-Type: application/json' \
  -H 'x-api-key : skey_test_41Bbw6At8dJjVyKV3ZaXghhLpRro5oAtR' \
  -d '{	"amount": 200.50,
  "currency": "THB",
  "description": "TESTPRODUCT",
  "source_type": "card",
  "mode": "token",
  "token": "pkey_prod_5BpmBr5LpqG84jYnDLPQe3Zv1OuhdN5dg",
  "reference_order" : "20180530175600" }' \
  https://apiportal.kasikornbank.com:12002/kpgw/card/v1/charge
```

_Sample response_

```json
{
  "id": "chrg_prod_47b66904ca59846c6be83cf444870a2f2",
  "object": "charge",
  "amount": 15,
  "currency": "USD",
  "transaction_state": "Auhtorized",
  "source": {
    "id": "card_test_42f00571ac396ad600ce8e72b0e58def1",
    "object": "card",
    "brand": "MASTERCARD",
    "last4": "514950******9007",
    "issuer_bank": "Kasikornbank Public Limited"
  },
  "created": "20180322121944000",
  "status": "success",
  "approval_code": "764253",
  "livemode": "false",
  "metadata": {},
  "failure_code": "",
  "failure_message": "",
  "redirect_url": "",
  "settlement_info": "",
  "refund_info": ""
}
```

<br/>

**Sample code for submit token to charge API**
