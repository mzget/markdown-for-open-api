# QR Payment API Reference

---

## Status Code (statusCode)

<br />

| Value | Description |
| ----- | ----------- |
| 00    | Successs    |
| 10    | Error       |

<br />

## QR Type (qrType)

<br />

| Value | Description | Type of Data |
| ----- | ----------- | ------------ |
| 1     | AliPay      | URL          |
| 2     | WeChat Pay  | URL          |
| 3     | ThaiQR      | Text         |

<br />

## Authentication Channel (authChannel)

<br />

| Value | Description        |
| ----- | ------------------ |
| KPLUS | K+ application     |
| KPSME | K+ SME apllication |

<br />

## Transaction Status (txnStatus)

<br />

| Value     | Description                                    |
| --------- | ---------------------------------------------- |
| PAID      | Transaction has been paid.                     |
| CANCELLED | QR is cancelled and cannot be used.            |
| EXPIRED   | QR is expired and cannot be used.              |
| NOT_FOUND | Transaction with given id does not exist.      |
| REQUESTED | QR is requested but not yet paid or cancelled. |
| VOIDED    | Transaction is voided after it is paid.        |

<br />

## Error Codes (errorCode)

<br />

| Error Code                | Error Description                                                    |
| ------------------------- | -------------------------------------------------------------------- |
| account_error             | Cannot credit to account. (EMACF)                                    |
| account_error             | Account is closed. (EMAC)                                            |
| authentication_error      | Wrong partner key. (EMA)                                             |
| bad_request               | Invalid JSON. (EMBR)                                                 |
| duplicate_request         | This request is duplicated. (EMDR)                                   |
| general_error             | ระบบไม่สามารถดำเนินรายการนี้ได้ กรุณาทำรายการอีกครั้งในภายหลัง (EMG) |
| internal_error            | Cannot connect to database. (EMIDB)                                  |
| internal_error            | System unavailable. (EMIU)                                           |
| invalid_currency_code     | Currency code XXX is not allowed. (EMICC)                            |
| invalid_origPartnerTxnUid | origPartnerTxnUid does not exist. (EMITDNE)                          |
| invalid_txn_amount        | Invalid Amount. (EMITA)                                              |
| invalid_txn_amount        | Amount must be an integer with two digits precision. (EMITF)         |
| invalid_qr_type           | QR Type X is not allowed. (EMIQR)                                    |
| invalid_reference1        | reference1 must not be empty. (EMIR)                                 |
| invalid_shop_id           | Shop ID is a duplicate. (EMISD)                                      |
| invalid_shop_id           | Shop ID does not exist. (EMISDNE)                                    |
| merchant_closed           | Merchant is already closed. (EMMC)                                   |
| duplicate_merchant        | National ID or Email already registered. (EMMD)                      |
| authentication_error      | Miss match partner id and mid. (EMPM)                                |
| invalid_merchant          | Merchant ID does not exist. (EMDNE)                                  |
| duplicate_merchant        | Partner ID and Partner Shop ID already registered. (EMRD)            |
| qr_cancelled              | QR is cancelled. (EMQRC)                                             |
| qr_paid                   | QR already paid. (EMQRP)                                             |
| qr_expired                | QR already expired. (EMQRAE)                                         |
| qr_expired                | QR has expired. (EMQRE)                                              |
| settlement_error          | Transaction is already settled (EMSET)                               |
| settlement_error          | Manual settlement is not allow between 22:00 - 02:30 (EMSMSG)        |
| qr_void                   | Cannot void other channel. (EMQRVOTCH)                               |
