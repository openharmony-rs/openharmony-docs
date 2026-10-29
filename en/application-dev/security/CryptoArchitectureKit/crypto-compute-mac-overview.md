# Message Authentication Code Computation

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=93fabc8c17767c2f12d40761db89b34b086858e3 translatedAt=2026-10-09T01:38:58.991Z pushedAt=2026-10-10T02:07:40.950Z -->

A Message Authentication Code (MAC) is used to verify message integrity. By using a key shared by both parties, it can detect message forgery, tampering, and other malicious behaviors.

This topic describes the key agreement algorithms and specifications supported by the system.

## HMAC
A hash-based message authentication code (HMAC) is a type of MAC involving a hash function and a secret key.

A HMAC uses a specified digest algorithm to generate a MAC based on the key and message shared by communicating parties. The MAC is used to check the integrity of transmitted packets. The HMAC adds key input on the basis of the message digest algorithm to ensure information correctness. The length of the generated MAC is fixed.

The **Supported Type** column in the following table lists the algorithm to be used when a **MAC** instance is created.

| Digest Algorithm| Supported Type| API Version|
| -------- | -------- | -------- |
| HASH | SHA-1| 9+ |
| HASH | SHA-224| 9+ |
| HASH | SHA-256| 9+ |
| HASH | SHA-384| 9+ |
| HASH | SHA-512| 9+ |
| HASH | SHA3-256 | 26.0.0+ |
| HASH | SHA3-384 | 26.0.0+ |
| HASH | SHA3-512 | 26.0.0+ |
| HASH | SM3 | 10+ |
| HASH | MD5 | 12+ |

## CMAC

Cipher-based Message Authentication Code (CMAC) is a cipher-based message authentication code algorithm primarily used to ensure message integrity and authenticity.

CMAC uses a block cipher (such as AES) and a key to generate a message authentication code, ensuring that the message has not been tampered with during transmission.

| Encryption Algorithm| API Version|
| -------- | -------- |
| AES128 | 16+ |
| AES256 | 16+ |
