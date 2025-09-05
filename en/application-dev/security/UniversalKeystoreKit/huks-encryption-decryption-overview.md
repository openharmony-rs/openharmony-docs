# Encryption and Decryption Overview and Algorithm Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

You can use the keys in HUKS to encrypt or decrypt data.

## Supported Algorithms

The following table lists the supported specifications for key encryption and decryption.
<!--Del-->
The key management service specifications include mandatory specifications and optional specifications. Mandatory specifications are algorithm specifications that must be supported. Optional specifications can be used based on actual situation. Before using the optional specifications, refer to the documents provided by the vendor to ensure that the specifications are supported.

**You are advised to use mandatory specifications in your development for compatibility purposes.**
<!--DelEnd-->

**Specifications****<!--RP1--> for standard devices<!--RP1End-->**

| Algorithm/Cipher Mode/Padding Mode| Description| API Version| <!--DelCol4-->Mandatory|
| -------- | -------- | -------- | -------- |
| <!--DelRow-->AES/ECB/NoPadding<br>AES/ECB/PKCS7 | In ECB mode, the data length should be a multiple of the block size used by the encryption algorithm. If the padding mode is **NoPadding** and the length of the input data is not a multiple of 16 bytes, the service side must pad the input data to the required length.| 8+ | No|
| AES/CBC/NoPadding<br>AES/CBC/PKCS7<br>AES/CTR/NoPadding | **IV** is mandatory.<br>In CBC mode, the data length should be a multiple of the block size used by the encryption algorithm. If the padding mode is **NoPadding** and the length of the input data is not a multiple of 16 bytes, the service side must pad the input data to the required length.| 8+ | Yes|
| AES/GCM/NoPadding | **Nonce** is mandatory for encryption.<br>**Nonce** and **TAG** are mandatory for decryption.| 8+ | Yes|
| RSA/ECB/NoPadding<br>RSA/ECB/PKCS1_V1_5<br>RSA/ECB/OAEP | The OAEP padding mode supports the following MD algorithms: SHA-256, SHA-384, and SHA-512.| 8+ | Yes|
| <!--DelRow-->SM4/ECB/NoPadding<br>SM4/ECB/PKCS7 | The ECB mode is not recommended.| 9+ | No|
| SM4/ECB/PKCS7 | The ECB mode is not recommended.| 20+ | Yes|
| SM4/CBC/PKCS7 | **IV** is mandatory.| 9+ | Yes|
| SM4/CTR/NoPadding<br>SM4/CBC/NoPadding<br>SM4/CFB/NoPadding<br>SM4/OFB/NoPadding | **IV** is mandatory.| 12+ | Yes|
| SM2/-/NoPadding | SM3 is used as the MD algorithm.| 11+ | Yes|
| DES/CBC/NoPadding<br>DES/ECB/NoPadding | The **IV** parameter is mandatory in CBC mode.| 18+ | Yes|
| 3DES/CBC/NoPadding<br>3DES/ECB/NoPadding | The **IV** parameter is mandatory in CBC mode.| 18+ | Yes|

**Specifications****<!--RP2--> for mini-system devices<!--RP2End-->**

<!--Del-->
Before implementing the specifications for mini-system devices, determine whether your device supports the related specifications.
<!--DelEnd-->

| Algorithm/Cipher Mode/Padding Mode| Description| API Version|
| -------- | -------- | -------- |
| AES/GCM/NoPadding | **Nonce** is mandatory for encryption.<br>**Nonce** and **TAG** are mandatory for decryption.| 8+ |
| AES/CBC/NoPadding<br>AES/CTR/NoPadding | **IV** is mandatory.| 11+ |
| DES/ECB/NoPadding | - | 12+ |
| DES/CBC/NoPadding | **IV** is mandatory.| 12+ |
| 3DES/ECB/NoPadding | - | 12+ |
| 3DES/CBC/NoPadding | **IV** is mandatory.| 12+ |
| RSA/ECB/NoPadding | - | 12+ |
| RSA/ECB/PKCS1_V1_5 | - | 12+ |
| RSA/ECB/OAEP | SHA-256 is used as the MD algorithm.| 12+ |
