# <strong>K-Payment Gateway</strong>

---

## [Get Started](#get-started)

<img src="https://firebasestorage.googleapis.com/v0/b/imageupload-19583.appspot.com/o/icon_manage.png?alt=media&token=639509f9-2202-4d45-9efd-349b4d7d9f8d" alt="manage"  width="25" height="25"  style="object-fit: contain; margin-right: 10px;" />
<a name="step1">
<strong>ขั้นตอนที่ 1:</strong> สมัครใช้งาน และเข้าสู่ระบบ</a>

ก่อนเข้าใช้งาน APIs กรุณา

<p>
1) สมัครใช้งานเพื่อ <strong><a href="/open-api/register">สร้าง Account</a></strong> ใหม่
</p>
<p>
2) ทำตามขั้นตอนในการสมัครใช้งาน และทำการ <strong><a href="/open-api/login">Log In</a></strong> เข้าสู่ระบบ
</p>

---

<img src="https://firebasestorage.googleapis.com/v0/b/imageupload-19583.appspot.com/o/icon_partner.png?alt=media&token=b210871c-6594-400e-8cd1-b0534c1950db" alt="partner"  width="25" height="25"  style="object-fit: contain; margin-right: 10px;" />
<a name="step2">
<strong>ขั้นตอนที่ 2:</strong> 
รับ PartnerID, PartnerSecret, Public & Secret Key
</a>

<p>
ทำการสร้าง App บน <strong><a href="/open-api/my-apps">Application Dashboard</a></strong> เพื่อรับ <b>PartnerID, PartnerSecret,   Public & Secret Key</b>
</p>

<div class="image-wrap" style="text-align: center; margin: 30px 0px ;" >
<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2Fguide_kpgw_create.png?alt=media&token=e728b77a-cb53-41d9-ae88-401105a44e6d" alt="create-app"  width="80%" height="auto" /></div>

<div class="image-wrap" style="text-align: center; margin: 30px 0px ;" >
<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2Fguide_kpgw_app.png?alt=media&token=60f321a6-bf0c-4672-8f44-fc0a376e0a65" alt="kpgw-app"  width="80%" height="auto" /></div>

---

<img src="https://firebasestorage.googleapis.com/v0/b/imageupload-19583.appspot.com/o/icon_api_black.png?alt=media&token=c5cbc9d7-231b-450f-8856-1f446c1afb4f" alt="api"  width="25" height="25"  style="object-fit: contain; margin-right: 10px;" />
<a name="step3"><strong>ขั้นตอนที่ 3:</strong> เริ่มใช้งาน Sandbox</a>

คุณสามารถเลือก API ที่อยากจะเริ่ม Testing ได้ โดยรายละเอียดการตั้งค่า ในการเชื่อมต่อ API จะอยู่ใน API Documentation

คุณพร้อมแล้วที่จะเริ่มสร้าง Application ด้วย API บน Sandbox ของธนาคาร!

---

## [Merchant Integration Guideline 1.0](#merchant-integration)

### 1. System Details

K-Payment Gateway provided by the KASIKORNBANK Public Company Limited (hereinafter referred to as “KBank”) is the online payment service to facilitate merchants accept card payment (both credit and debit card), support multi-currencies over the world, and Thai QR payment. We provide you with the ability to customize the look and feel of your web page while ensuring that you are compliant with PCI DSS 3.2 Requirements.

**Customer Journey**

> **Figure 1: Card Payment**

<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FCard_Payment.jpg?alt=media&token=edf5db68-a2e7-4573-99ef-82f1fa5a2f0a" width="100%" alt="Card Payment" />

> **Figure 2: QR Payment**

<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FQR_Payment.jpg?alt=media&token=4052bd88-c6da-47b3-8924-0857eec9643b" width="100%" alt="QR Payment">

---

### 2. Test case

**2.1. Verify SSL Certificate issued by CA (Certificate Authority)**

- Support at least 128-bits encryption
- Support TLS 1.2

HTTPS requirements, all submissions of payment info using K-Payment Gateway are made via a secure HTTPS connection.

**2.2. Questionnaire of Merchant Integration**

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

## [Fraud Protection](#fraud-protection)

**Tokenization**

K-Payment Gateway provide payment UI library for create one time use token that you use on your backend server to perform card operations. This way every card processed with us goes through tokenization.

> **Figure 3: Tokenization**

   <img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FTokenization.png?alt=media&token=4d2a4178-4558-4e18-9183-264267d763fa" width="100%" alt="Tokenization">

**3D Secure Card Payments**

3D Secure provides a layer of protection against fraudulent payments that is supported by most card issuers.
Unlike regular card payments, 3D Secure requires cardholders to complete an additional verification step with the issuer. Typically, this involves showing the customer an authentication page on their bank’s website, where they are prompted to enter a password associated with the card or a verification code sent to their phone. This process is familiar to customers through the card networks’ brand names, such as Visa Secure and Mastercard Identity Check.

> **Figure 4: Card Issuer Authentication**

<img src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2F3D_Secure_Step2.png?alt=media&token=57963ae8-41a1-4aa3-b219-d523270cac32" width="100%" alt="3D Secure Step2">
