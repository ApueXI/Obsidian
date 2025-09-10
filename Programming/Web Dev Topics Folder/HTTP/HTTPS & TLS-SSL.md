---
Created: 2025-06-23T18:51
---
## What is HTTPS?

- **HTTPS** = **HTTP Secure**
- It’s HTTP layered over **TLS/SSL** to encrypt data between client and server.
- Ensures **confidentiality**, **integrity**, and **authentication**.

  

## What is TLS/SSL?

- **TLS (Transport Layer Security)** is the modern cryptographic protocol for securing internet communication.
- **SSL (Secure Sockets Layer)** is the predecessor to TLS (now deprecated but term still used interchangeably).
- TLS encrypts the data and verifies the server identity.

  

## How HTTPS Works (Simplified)

1. **Client connects** to server using HTTPS (port 443).
2. **TLS Handshake** occurs:
    - Client and server agree on encryption algorithms.
    - Server sends its **digital certificate** (issued by a Certificate Authority, CA).
    - Client verifies the certificate’s authenticity.
    - Keys are exchanged securely.
3. **Encrypted communication** starts — all HTTP data is now encrypted.
4. Client and server can securely send and receive data.

  

## Key Components

|   |   |
|---|---|
|Term|Description|
|**Certificate Authority (CA)**|Trusted entity that issues digital certificates|
|**Digital Certificate**|Proves the server’s identity to the client|
|**Public Key / Private Key**|Used for encryption and decryption during handshake|
|**Symmetric Encryption**|Used for encrypting the actual data after handshake|

  

## Benefits of HTTPS

- **Encryption:** Prevents eavesdropping and man-in-the-middle attacks.
- **Authentication:** Verifies you’re communicating with the real server.
- **Data integrity:** Detects if data is tampered with in transit.
- **SEO boost:** Search engines prefer HTTPS sites.
- **User trust:** Shows padlock icon in browsers.

  

## Common TLS Versions

|   |   |
|---|---|
|Version|Status|
|SSL 2.0|Deprecated|
|SSL 3.0|Deprecated|
|TLS 1.0|Deprecated|
|TLS 1.1|Deprecated|
|TLS 1.2|Widely used|
|TLS 1.3|Latest & recommended|

  

## HTTPS vs HTTP Summary

|   |   |   |
|---|---|---|
|Feature|HTTP|HTTPS|
|Port|80|443|
|Security|None (plaintext)|Encrypted (TLS/SSL)|
|URL prefix|`http://`|`https://`|
|Data Integrity|No|Yes|
|Authentication|No|Yes (via certificates)|