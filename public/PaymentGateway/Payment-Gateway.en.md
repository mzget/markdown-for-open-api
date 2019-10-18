# K-Payment Gateway

## Merchant Integration Guideline 1.0

---

### 1. System Details

K-Payment Gateway provided by the KASIKORNBANK Public Company Limited (hereinafter referred to as “KBank”) is the online payment service to facilitate merchants accept card payment (both credit and debit card), support multi-currencies over the world, and Thai QR payment. We provide you with the ability to customize the look and feel of your web page while ensuring that you are compliant with PCI DSS 3.2 Requirements.

<strong>Customer Journey</strong>

1. Card Payment
   <img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FCard_Payment.png?alt=media&token=2d60b4ce-b991-4bb5-977a-fb6c4f6939bc" width="100%" alt="Card Payment" />

2. QR Payment
   <img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FQR_Payment.png?alt=media&token=d088ebcc-22ac-4e8b-87d4-8c8e59ca9b80" width="100%" alt="QR Payment">

---

### 2. Test case

<strong>2.1. Verify SSL Certificate issued by CA (Certificate Authority)</strong>

- Support at least 128-bits encryption
- Support TLS 1.2

HTTPS requirements, all submissions of payment info using K-Payment Gateway are made via a secure HTTPS connection.

<strong>2.2. Questionnaire of Merchant Integration</strong>

Do your systems have the PCI DSS 3.2 Certification?

If yes, please sent your AOC Report to xxxx@kasikornbank.com.

Which type of payments that your systems supported?

- Visa Card
- Master Card
- JCB Card
- Thai QR

Which type of credit card that you need to enable the 3D Secure payment?

- Visa Card
- Master Card
- JCB Card

<strong>2.3. Integrating with KPay.js</strong>

KPay.js is JavaScript library which helps to set a pre-built UI component for building your checkout flow and secure card data by sending sensitive details from the customer's browser directly to the KBank server.

<strong>Setup Guide</strong>

Creating a custom payment form with K-Payment UI requires three steps.

**1. Set up KPay.js into your web.**

For testing purposes, you have to include this script into your checkout page. It will automatically create payment form into your page and display a “Pay Now” button. To determine where to insert the script, we recommend you placing empty `<div>` elements with unique IDs in your checkout page.

```html
[GROUP][COPYABLE] ---[HTML/html]---
<form method="POST" action="/api/checkout">
  <script
    type="text/javascript"
    src="https://uat-kpaymentgateway.new-kpgw.com/ui/v2/kpayment.min.js"
    data-apikey="pkey_prod_5BpmBr5LpqG84jYnDLPQe3Zv1OuhdN5dg"
    data-amount="74.00"
    data-currency="THB"
    data-payment-methods="card"
    data-name="Your Shop Name"
  ></script>
</form>

---[React/tsx]---
import React, { useEffect } from "react";
import KPayment from "react-kpayment";

export function CardPayment(props: any) {
  return (
    <React.Fragment>
      <p>Credit/Debit Card</p>
      <KPayment
      formAction="/api/checkout"
      onFinish={onFinish}
      onProcess={onProcess}
      debug={true}
      attrs={{ scriptUrl: "https://uat-kpaymentgateway.new-kpgw.com/ui/v2/kpayment.min.js",
      apiKey:"pkey_prod_5BpmBr5LpqG84jYnDLPQe3Zv1OuhdN5dg",
      amount: "74.00",
      currency: "THB",
      paymentMethods: "card",
      shopName: "Your Shop Name", }} />
    </React.Fragment>
  )
}
```

When the form above has loaded, it will create an instance of a Payment form on your checkout page as follows:

<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FCheckout_Page.png?alt=media&token=9e8572c3-33bd-4a2c-ab41-f3c5d996e8d3" width="100%" alt="Checkout Page" />

Also, the data attributes that you can config with KPay.js which support collected card details and information’s from your customers.

| Data Attributes                     | Type          | Description                                                                                    |
| ----------------------------------- | ------------- | ---------------------------------------------------------------------------------------------- |
| **data-apikey** (Required)          | String(50)    | The public key of authentication<br/>Sample Data: **data-apikey="pkey_test_1234567890123456"** |
| **data-amount** (Required)          | Decimal(10,2) | Amount<br/>Sample Data: **data-amount="1000.50"**                                              |
| **data-payment-methods** (Required) | String        | Payment method must be card, qr and redirect.<br/>Sample Data: **data-payment-methods="card"** |
| **data-name** (Optional)            | (Optional)    | Your shop name<br/>Sample Data: **data-name="Awesome Shop"**                                   |
| **data-mid** (Optional)             | String(15)    | Your merchant ID<br/>Sample Data: **data-mid="444123456789001"**                               |
| **data-currency** (Optional)        | String(3)     | Currency unit (Default is THB)<br/>Sample Data: **data-currency="THB"**                        |
| **data-description** (Optional)     | String(255)   | Product description<br/>Sample Data: **data-description="Awesome Shoe and Bag"**               |

**2. Receive a token to securely transmit card information.**

When the customers submit card information’s with Payment UI. Their data will be sent and collected at K-Payment backend and then be converted into a token. This step is submitted by JavaScript. (KPay.js)

**3. Submit the token and the rest of your form to your server.**

The last step to make credit/debit card payments, First you need to create the POST request method requests that a web server accepts the data from step 2 and then passing parameters to API with a secret key to complete payment.
_A Token created with this method expire after 10 minutes, or after one operation with that token is made._

```typescript
[GROUP][COPYABLE]
---[Node.js/typescript]---

import { NextApiRequest, NextApiResponse } from "next";
import { fetch } from "cross-fetch";

const apikey = "pkey_prod_5BpmBr5LpqG84jYnDLPQe3Zv1OuhdN5dg";
let chargeEndpoint = "https://apiportal.kasikornbank.com:12002/card/v2/charge";
type AcceptBody = {
  apikey: string;
  amount: string;
  currency: string;
  source_type: string;
  mode: string;
  token: string;
  reference_order: string;
} & {
  paymentMethods: string;
  saveCard: true;
  token: string;
};
async function Checkout(req: NextApiRequest, res: NextApiResponse) {
  let { method } = req;
  let body: AcceptBody = req.body;

  switch (method) {
    case "POST":
      try {
        let data = {
          token: body.token,
          saveCard: body.saveCard,
          source_type: body.paymentMethods,
          amount: body.amount,
          currency: body.currency,
          mode: "token",
          reference_order: "test123",
        };
        const resp = await fetch(chargeEndpoint, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            "Cache-Control": "no-cache",
            "x-api-key": apikey,
          },
          body: JSON.stringify(data),
        });
        if (resp.ok) {
          const result = await resp.json();
          res.status(200).json(result);
        } else {
          const result = await resp.json();
          throw new Error(JSON.stringify(result));
        }
      } catch (ex) {
        res.status(400).json({ status: "Bad Request", message: ex.message });
      }
      break;
    default:
      res.setHeader("Allow", ["GET", "POST"]);
      res.status(405).end(`Method ${method} Not Allowed`);
  }
}
export default Checkout;

```

**4. Pay with Payment UI.**

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
  "token": "tokn_test_1fadeb16520513a076c2d97df3b0841f9",
  "reference_order" : "20180530175600" }' \
  https://dev-kpaymentgateway-services.kasikornbank.com/card/v2/charge
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

<strong>2.4. For Open API(Sandbox), Verify case (Only success)</strong>

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
