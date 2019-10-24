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

---

## Fraud Protection

**Tokenization**

K-Payment Gateway provide payment UI library for create one time use token that you use on your backend server to perform card operations. This way every card processed with us goes through tokenization.  

**3D Secure Card Payments**

3D Secure provides a layer of protection against fraudulent payments that is supported by most card issuers.
Unlike regular card payments, 3D Secure requires cardholders to complete an additional verification step with the issuer. Typically, this involves showing the customer an authentication page on their bank’s website, where they are prompted to enter a password associated with the card or a verification code sent to their phone. This process is familiar to customers through the card networks’ brand names, such as Visa Secure and Mastercard Identity Check.