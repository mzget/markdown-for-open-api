# ITMX PROMPTPAY API V1.1

## ITMX API Standard  Error Code

|  |  |  |  |  |
| ------------ | ---- | ---------------- | ---------- | --------------------------------------------------------------------------------- |
| **data ---ref1** | 0..1 | Alphanumeric(20) | string(20) | 1st reference number on pay slip - For Bill Payment, this will be Mandatory |
| **data ---ref2** | 0..1 | Alphanumeric(20) | string(20) | 2st reference number on pay slip - For Bill Payment, this will be **Conditional** |
| **data ---ref3** | 0..1 | Alphanumeric(20) | string(20) | 3st reference number on pay slip - **For Bill Payment, this will be Conditional** |

### JSON Failure Response Content (Http status code 4xx, 5xx)

| Parameter          | Occurrence                  | Format    | Type         | Description                                  |
| ------------------ | --------------------------- | --------- | ------------ | -------------------------------------------- |
| status             | 0..1 - success 1..1 - error | -         | object       | -                                            |
| status --- code    | 1..1                        | 0000      | string(4)    | Error code please find detail below section. |
| status --- message | 1..1                        | **ERROR** | string(1024) | Short explanation                            |

### ITMX Failure Response Code

| HTTP Response Code | Response Code | Description                                                 | Source of Response Code | Remarks                                                                                                                                                                                                                                                                                                    |
| ------------------ | ------------- | ----------------------------------------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200                | 0000          | Successful response                                         | Bank                    | Success                                                                                                                                                                                                                                                                                                    |
| 200                | 8404          | Transaction Reference does not exist                        | Bank                    | - Transaction does not exit in sending bank - Verify bank send invalid 'Sending Bank' - Payment is too old to verify as specified by business rule (**At least 7 days**- Ex. Payment occurs on **1 Aug**, verification can be verified until **8 Aug** but will be error transaction too old on **9 Aug**) |
| 200                | 6501          | Destination bank does not support or implement this service | ITMX                    | - Invalid Destination bank - Destination bank does not support this service, validate at ITMX |
| 200                | 8501          | Sponsor Bank error due to E-Wallet provider does not support or implement this service | Bank                    | Sponsor Bank return error due to e-wallet provider does not support or implement this service. |
| 200                | 8503          | Communication error between ITMX - Destination Bank | Bank                    | Target server cannot connect |
| 400                | 6400          | Bad Request | ITMX                    | Request missing required parameter both in URL or query parameter|
| 400                | 6410          | Bad Request | ITMX                    | Sending bank missing required http headers - X-API-Version |
| 400                | 6411          | Bad Request | ITMX                    | Sending bank missing required http headers - X-CRT-Bank |
| 400                | 6412          | Bad Request | ITMX                    | Sending bank missing required http headers - X-Dest-Bank |
| 400                | 8400          | Bad Request | Bank                    | Request missing required parameter both in URL or query parameter |
| 400                | 8410          | Bad Request | Bank                    | ITMX missing required http headers - X-API-Version |
| 400                | 8411          | Bad Request | Bank                    | ITMX missing required http headers - X-CRT-Version |
| 401                | 6421          | Unauthorized | ITMX                   | Invalid API-Key, API-Secret |
| 401                | 6422          | Unauthorized | ITMX                   | Requester bank (JWT issuer) does not match with API-Key |
| 401                | 6423          | Unauthorized | ITMX                   | Audience must be itmx (invalid audience) |
| 401                | 6424          | Unauthorized | ITMX                   | Missing JWT Unique Tracing Id |
| 401                | 6701          | Unauthorized | ITMX                   | JWT Invalild signature |
| 401                | 6702          | Unauthorized | ITMX                   | JWT Token expire |
| 401                | 6703          | Unauthorized | ITMX                   | Invalid JWT Certificate version to verify signature |
| 401                | 8701          | Destination Bank UnAuthorized error | Bank                    | **Destination bank** throw error 401 with status code 8701 invalid ITMX signature verification |
| 401                | 8702          | Destination Bank UnAuthorized error | Bank                    | **Destination bank** throw error JWT token expire |
| 401                | 8703          | Destination Bank UnAuthorized error | Bank                    | **Destination bank throw** Invalid ITMX Certificate Version |
| 403                | 6403          | Forbidden | ITMX                    | Participant bank does not subscribe to this service. |
| 500                | 6500          | ITMX Internal Error | ITMX                    | Unknown ITMX Internal Error |
| 500                | 8500          | Internal system error - Destination Bank | Bank     | Destination bank throw unknown internal error |
