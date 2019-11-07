# Integrating Payment UI (KPay.js)

---

<!-- <a href="/open-api/guide/payment-gateway"></a> -->

[_If you new to K-Payment-Gateway. Please read merchant integration guideline first_](/open-api/guide/payment-gateway)

### Description

KPay.js is JavaScript library which helps to set a pre-built UI component for building your checkout flow and secure card data by sending sensitive details from the customer's browser directly to the KBank server.

### Setup Guide

Creating a custom payment form with K-Payment UI requires three steps.

**1. Set up KPay.js into your web.**

For testing purposes, you have to include this script into your checkout page. It will automatically create payment form into your page and display a “Pay Now” button. To determine where to insert the script, we recommend you placing empty `<div>` elements with unique IDs in your checkout page.

**Sample code for payment UI integration**

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

---[React/tsx]--- import React, { useEffect } from "react"; import KPayment from
"react-kpayment"; export function CardPayment(props: any) { return (
<React.Fragment>
  <p>Credit/Debit Card</p>
  <KPayment formAction="/api/checkout" onFinish={onFinish} onProcess={onProcess}
  debug={true} attrs={{ scriptUrl:
  "https://uat-kpaymentgateway.new-kpgw.com/ui/v2/kpayment.min.js",
  apiKey:"pkey_prod_5BpmBr5LpqG84jYnDLPQe3Zv1OuhdN5dg", amount: "74.00",
  currency: "THB", paymentMethods: "card", shopName: "Your Shop Name", }} />
</React.Fragment>
) }
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

> <br>_A Token created with this method expire after 10 minutes, or after one operation with that token is made._</br>
