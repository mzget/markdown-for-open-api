# Two-Way SSL

KBank OpenAPI secures its connections with partners using Two-Way SSL (Mutual Authentication) method.

## SSL Handshake

In Two-Way SSL authentication, the client and server need to authenticate and validate each otherâ€™s identities. The authentication message exchange between client and server is called an SSL handshake, and it includes the following steps:

1. A client requests access to a protected resource.
2. The server presents its certificate to the client.
3. The client verifies the server's certificate.
4. If successful, the client sends its certificate to the server.
5. The server verifies the client's credentials.
6. If successful, the server grants access to the protected resource requested by the client.

In step 5 (above), the server validates the client, which is the second part of the Two-Way SSL (Mutual Authentication) process. This is typically done by making sure that the client certificate is valid (non-expired and issued by a trusted Certificate Authority)
