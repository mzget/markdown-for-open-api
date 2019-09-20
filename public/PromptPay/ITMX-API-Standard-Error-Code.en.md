# ITMX PromptPay API Standard Error Code

<br />

## JSON Failure Response Content (Http status code 4xx, 5xx)

<br />

| Parameter          | Occurrence                     | Format    | Type         | Description                                  |
| ------------------ | ------------------------------ | --------- | ------------ | -------------------------------------------- |
| status             | 0..1 - success<br>1..1 - error | -         | object       | -                                            |
| status --- code    | 1..1                           | 0000      | string(4)    | Error code please find detail below section. |
| status --- message | 1..1                           | **ERROR** | string(1024) | Short explanation                            |

<br />

## ITMX Failure Response Code

<br />

| HTTP Response Code | Response Code | Description                              | Source of Response Code | Remarks                                       |
| ------------------ | ------------- | ---------------------------------------- | ----------------------- | --------------------------------------------- |
| 200                | 0000          | Successful response                      | Bank                    | Success                                       |
| 500                | 8500          | Internal system error - Destination Bank | Bank                    | Destination bank throw unknown internal error |
