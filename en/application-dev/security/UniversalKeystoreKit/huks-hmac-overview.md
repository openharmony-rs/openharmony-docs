# HMAC Overview and Algorithm Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

A message authentication code (MAC) is used for verifying the authenticity and integrity of information transmitted or stored on unreliable media. A hash-based message authentication code (HMAC) is a MAC involving a cryptographic hash function and a secret cryptographic key. The HMAC can be used with any cryptographic hash function, such as SHA-256 and SM3. HUKS supports the use of HMAC with mainstream message digest (MD) algorithms.

## Supported Algorithms

The following table lists the HMAC specifications supported by the system.
<!--Del-->
The key management service specifications include mandatory specifications and optional specifications. Mandatory specifications are algorithm specifications that must be supported. Optional specifications can be used based on actual situation. Before using the optional specifications, refer to the documents provided by the vendor to ensure that the specifications are supported.

You are advised to use mandatory specifications in your development for compatibility purposes.
<!--DelEnd-->
| MD Algorithm| Supported Key Length (Bit)| API Version| <!--DelCol4-->Mandatory|
| -------- | -------- | -------- | -------- |
| <!--DelRow-->SHA-1, SHA-224| 8 to 1024 | 8+ | No|
| SHA-256 | 192 to 1024 | 8+ | Yes|
| SHA-384, SHA-512| 256 to 1024 | 8+ | Yes|
| SM3 | <!--RP1-->8 to 4096 <!--RP1End--> | 8+ | Yes|
