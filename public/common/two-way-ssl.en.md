# Two-Way SSL

KBank OpenAPI secures its connections with partners using Two-Way SSL (Mutual Authentication) method.

## SSL Handshake

In Two-Way SSL authentication, the client and server need to authenticate and validate each others identities. The authentication message exchange between client and server is called an SSL handshake, and it includes the following steps:

1. A client requests access to a protected resource.
2. The server presents its certificate to the client.
3. The client verifies the server's certificate.
4. If successful, the client sends its certificate to the server.
5. The server verifies the client's credentials.
6. If successful, the server grants access to the protected resource requested by the client.

In step 5 (above), the server validates the client, which is the second part of the Two-Way SSL (Mutual Authentication) process. This is typically done by making sure that the client certificate is valid (non-expired and issued by a trusted Certificate Authority)

## Establishing SSL Connection

To establish a Two-Way SSL (Mutual Authentication) connection, you must have the following:

- private key
- client certificate

---

```code
[GROUP][COPYABLE]
---[Test Endpoint]---
https://APIPORTALTEST.kasikornbank.com:12002/test/ssl
```

**Parameters**

| Field                         | Data Type | Description                         | Example          | Mandatory |
| ----------------------------- | --------- | ----------------------------------- | ---------------- | :-------: |
| [colspan=5] Header parameters |
| content-type                  | string    | Type of content as application/json | application/json |     Y     |
| [colspan=5] Body parameters   |
| partnerId                     | string    | Partner-Id                          |                  |     Y     |
| partnerSecret                 | string    | Partner-Secret                      |                  |     Y     |

**Example Response**

```json
{
  "statusCode": "00",
  "certStatus": "Success",
  "partnerStatus": "Success",
  "errorMsg": null,
  "certificateObjs": [
    {
      "subject": "CN=kbank.pentest.1, O=KBTG, ST=Bangkok, C=TH",
      "issuer": "CN=KASIKORNBANK OpenAPI ROOT CA, OU=KBTG, O=KASIKORN BUSINESS TECHNOLOGY-GROUP, L=Ratburana, ST=Bangkok, C=TH",
      "startDate": "Thu May 17 19:29:15 ICT 2018",
      "expireDate": "Tue May 16 19:29:15 ICT 2023",
      "serialNumber": "14331402536859360582"
    }
  ]
}
```

<br />

## Testing Two-Way SSL Connectivity Using Postman

1. Download Postman from [https://www.getpostman.com/](https://www.getpostman.com/)
2. Open Postman and go to **Settings** > **Certificates** as shown below:

   <br />

   <img alt="Postman Review Certificates" src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/two-way-ssl%2FPostman-Review-Cert.png?alt=media&token=002c38f8-25de-4d63-840a-16a049a1d568" width="100%" />

3. Add your _certificates_ and _private key_:

   <br />

   <img alt="Postman Add Certificates" src="https://firebasestorage.googleapis.com/v0/b/kbank-open-api.appspot.com/o/two-way-ssl%2FPostman-Add-Cert.png?alt=media&token=16eceabe-fe8a-40ce-b01c-919b6c2d55a1" width="100%" />

<br />

## Sample Code for Two-Way SSL

```javascript
[GROUP][COPYABLE]
---[JS/javascript]---
import * as request from 'request';
import * as fs from 'fs';
import * as path from 'path';

let keyfile = path.join(__dirname, 'kbank.pentest.1.key');
let certificateFile = path.join(__dirname, 'kbank.pentest.1.crt');

export function Request() {
  const options = {
    url: 'https://APIPORTAL.kasikornbank.com:12002/test/ssl',
    agentOptions: {
      cert: fs.readFileSync(certificateFile),
      key: fs.readFileSync(keyfile),
    },
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      partnerId: '',
      partnerSecret: '',
    }),
  };
  request.post(options, function(error, response, body) {
    if (error) {
      console.warn(error);
    } else {
      console.log(body);
    }
  });
}

```
