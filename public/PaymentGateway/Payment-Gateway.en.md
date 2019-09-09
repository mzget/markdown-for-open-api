# K-Payment Gateway

## Merchant Integration Guideline 1.0

### 1. System Details

    K-Payment Gateway provided by the KASIKORNBANK Public Company Limited (hereinafter referred to as “KBank”) is the online payment service to facilitate merchants accept card payment (both credit and debit card), support multi-currencies over the world, and Thai QR payment. We provide you with the ability to customize the look and feel of your web page while ensuring that you are compliant with PCI DSS 3.2 Requirements.

    <strong>Customer Journey</strong>

       1. Card Payment

       ![Card-Payment]({{site.baseurl}}/https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FCard_Payment.png?alt=media&token=2d60b4ce-b991-4bb5-977a-fb6c4f6939bc)

       2. QR Payment

          ![QR-Payment]({{site.baseurl}}/https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/kpgw%2FQR_Payment.png?alt=media&token=d088ebcc-22ac-4e8b-87d4-8c8e59ca9b80)

### 2. Test case

    1. Verify SSL Certificate issued by CA (Certificate Authority)
       _ Support at least 128-bits encryption
       _ Support TLS 1.2
       HTTPS requirements, all submissions of payment info using K-Payment Gateway are made via a secure HTTPS connection.
    2. Questionnaire of Merchant Integration

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

    3. Integrating with KPay.js

    KPay.js is JavaScript library which helps to set a pre-built UI component for building your checkout flow and secure card data by sending sensitive details from the customer's browser directly to the KBank server.

    **Setup Guide**

    Creating a custom payment form with K-Payment UI requires three steps.

         1. Set up KPay.js into your web.

    -----------------น้องรูปภาพ-----------------

    For testing purposes, you have to include this script into your checkout page. It will automatically create payment form into your page and display a “Pay Now” button. To determine where to insert the script, we recommend you placing empty `<div>` elements with unique IDs in your checkout page.

    When the form above has loaded, it will create an instance of a Payment form on your checkout page as follows:

    Also, the data attributes that you can config with KPay.js which support collected card details and information’s from your customers.

    | Data Attributes                    | Type          | Description                                                                                |
    | ---------------------------------- | ------------- | ------------------------------------------------------------------------------------------ |
    | **data-apikey** (Required)         | String(50)    | The public key of authentication Sample Data: **data-apikey="pkey_test_1234567890123456"** |
    | **data-amount** (Required)         | Decimal(10,2) | Amount Sample Data: **data-amount="1000.50"**                                              |
    | **data-paymentmethods** (Required) | String        | Payment method must be card, qr and redirect. Sample Data: **data-payment-methods="card"** |
    | **data-name** (Optional)           | (Optional)    | Your shop name Sample Data: **data-name="Awesome Shop"**                                   |
    | **data-mid** (Optional)            | String(15)    | Your merchant ID Sample Data: **data-mid="444123456789001"**                               |
    | **data-currency** (Optional)       | String(3)     | Currency unit (Default is THB) Sample Data: **data-currency="THB"**                        |
    | **data-description** (Optional)    | String(255)   | Product description Sample Data: **data-description="Awesome Shoe and Bag"**               |

         2. Create a token to securely transmit card information.


    After the customers submit card information’s with Payment UI **TBC**


        3. Submit the token and the rest of your form to your server.

    The last step is to submit the token, along with any additional information that has been collected, to your server. **TBC**

    4. Verify case (Only success) - **TBC**
        1. Verify Charge Object (Credit Card)
        2. Verify Charge Object (Thai QR)

5. API Reference

   Merchant Registration
   -----------------น้องหัวตารางซ้าย-----------------

   -----------------น้องรูปภาพ-----------------

   Sample request message

   Request Attributes

   | Attitude Name    | Data type    | Required | Description                                     |
   | ---------------- | ------------ | -------- | ----------------------------------------------- |
   | companyCode      | varchar(255) | Y        | The unique name of company                      |
   | companyTradeName | varchar(255) | Y        | Company trade name                              |
   | companyNameTH    | varchar(255) | Y        | Company name (TH)                               |
   | companyNameEN    | varchar(255) | Y        | Company name (EN)                               |
   | firstName        | varchar(255) | Y        | Firstname                                       |
   | lastName         | varchar(255) | Y        | Lastname                                        |
   | email            | varchar(50)  | Y        | Email (use for merchant login)                  |
   | password         | varchar(15)  | Y        | Password (use for merchant login)               |
   | addressStr       | varchar(255) | N        | address                                         |
   | postCodeId       | Integer      | Y        | Postcode ID (Ref : getPostCodes method)         |
   | homePhoneNo      | varchar(20)  | N        | Home phone number                               |
   | officePhoneNo    | varchar(20)  | N        | Office phone number                             |
   | mobilePhoneNo    | varchar(20)  | Y        | Mobile phone number                             |
   | faxNo            | varchar(20)  | N        | Fax number                                      |
   | emailCompany     | varchar(50)  | N        | Email of company                                |
   | businessTypeId   | Integer      | Y        | Business type ID (Ref : getBusinessType method) |

   Sample response message

   -----------------น้องรูปภาพ-----------------

   Response Attributes

   | Attitude Name | Data type    | Can Null (Fail) | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   | ------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | statusCode    | varchar(255) | N               | Status code (success or fail)                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   | statusMessage | varchar(255) | N               | Result Messages                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   | companyId     | Integer      | Y               | Company Id (Auto generated from KPGW systems)                                                                                                                                                                                                                                                                                                                                                                                                                         |
   | companyCode   | varchar(255) | Y               | The unique name of company                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   | approveStatus | varchar(10)  | Y               | Status of Registration <div> **PENDING** - Wait for approve and checking an information’s to integrate test with K-Payment Sandbox system. <div> **REJECTED** - Not approve, after reviewed by Business team. <div> **APPROVED** - Approved, after reviewed by Business team. KPGW will successfully a result by email. <div> **COMPLETED** - Completely test with Sandbox K-Payment system. Waiting for business team and Merchant launch to Production Environment. |

   Results for APl

   | Status Code | Status Message                                                              |
   | ----------- | --------------------------------------------------------------------------- |
   | success     | Successfully created your merchant account.                                 |
   | fail        | Your email is already resisted in sandbox systems.                          |
   | fail        | Your postcode or business type parameters don’t exist in K-Payment systems. |
   | fail        | Your input parameter is invalid such as email, phone number and others.     |

   Get information of company

   -----------------น้องหัวตารางซ้าย-----------------

   -----------------น้องรูปภาพ-----------------

   Sample request message

   Request Attributes

   | Attitude Name | Data type | Required | Description |
   | ------------- | --------- | -------- | ----------- |
   |               |           |          |             |

   Sample request message

   Response Attributes

   | Attitude Name | Data type | Can Null (Fail) | Description |
   | ------------- | --------- | --------------- | ----------- |
   |               |           |                 |             |

   Results for APl

   | Status Code | Status Message |
   | ----------- | -------------- |
   |             |                |

   Get Address information with postcode

   -----------------น้องหัวตารางซ้าย-----------------

   -----------------น้องรูปภาพ-----------------

   Sample request message

   Request Attributes

   | Attitude Name | Data type  | Required | Description                                                        |
   | ------------- | ---------- | -------- | ------------------------------------------------------------------ |
   | postcode      | varchar(5) | Y        | Thai Postcode. Can be “ALL” or Thai Postcode is 10230, 10600, etc. |

   -----------------น้องรูปภาพ-----------------

   Sample response message

   -----------------น้องรูปภาพ-----------------

   Response Attributes

   | Attitude Name            | Data type    | Can Null (Fail) | Description                |
   | ------------------------ | ------------ | --------------- | -------------------------- |
   | statusCode               | varchar(255) | N               | Status code success / fail |
   | statusMessage            | varchar(255) | N               | Result message             |
   | postcodes/postcodeId     | Integer      | Y               | Postcode ID                |
   | postcodes/postcode       | Integer      | Y               | Postcode                   |
   | postcodes/districtCode   | Integer      | Y               | District code              |
   | postcodes/destrictName   | varchar(255) | Y               | District name (TH)         |
   | postcodes/destrictNameEN | varchar(255) | Y               | District name (EN)         |
   | postcodes/amphurCode     | Integer      | Y               | Amphur code                |
   | postcodes/amphurName     | varchar(255) | Y               | Amphur name (TH)           |
   | postcodes/amphurNameEn   | varchar(255) | Y               | Amphur name (EN)           |
   | postcodes/provinceCode   | Integer      | Y               | Province code              |
   | postcodes/provinceName   | varchar(255) | Y               | Province name (TH)         |
   | postcodes/provinceNameEn | varchar(255) | Y               | Province name (EN)         |

   Results for APl

   | Status Code | Status Message                                            |
   | ----------- | --------------------------------------------------------- |
   | success     | Result is list of Thai post code and address information. |
   | fail        | Your post code is not found.                              |

   -----------------น้องหัวตารางซ้าย-----------------

   -----------------น้องรูปภาพ-----------------

   Sample request message

   Request Attributes

   | Attitude Name | Data type | Required | Description |
   | ------------- | --------- | -------- | ----------- |
   | -             | -         | -        | -           |

   -----------------น้องรูปภาพ-----------------

   Sample response message

   Response Attributes

   | Attitude Name                    | Data type    | Can Null (Fail) | Description                             |
   | -------------------------------- | ------------ | --------------- | --------------------------------------- |
   | statusCode                       | varchar(255) | N               | Status code success / Otherwise is fail |
   | statusMessage                    | varchar(255) | N               | Status message                          |
   | businessTypes/businessTypeId     | Integer      | Y               | Business type ID                        |
   | businessTypes/businessTypeCode   | Integer      | Y               | Business type code                      |
   | businessTypes/businessTypeDesc   | varchar(255) | Y               | Business type description (TH)          |
   | businessTypes/businessTypeDescEn | varchar(255) | Y               | Business type description (EN)          |

   Results for APl

   | Status Code | Status Message                       |
   | ----------- | ------------------------------------ |
   | success     | Results is list of business type.    |
   | fail        | Your request has invalid parameters. |
