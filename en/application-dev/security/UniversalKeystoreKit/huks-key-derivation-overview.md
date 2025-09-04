# Key Derivation Overview and Algorithm Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

To stretch keys into longer keys or to obtain keys in the required format, you can use the HUKS APIs to derive one or more secrete keys from a key (base key) by using a pseudorandom function.

> **NOTE**<br> 
> * In HUKS, only the keys managed by HUKS can be used for key derivation.  
> * Key derivation is not supported<!--RP2--> by mini-system devices<!--RP2End-->.
> * Using an existing key alias as the alias of the key generated from derivation will overwrite the existing key.

## Supported Algorithms

The following table lists the supported key derivation specifications.
<!--Del-->
The key management service specifications include mandatory specifications and optional specifications. Mandatory specifications are algorithm specifications that must be supported. Optional specifications can be used based on actual situation. Before using the optional specifications, refer to the documents provided by the vendor to ensure that the specifications are supported.

**You are advised to use mandatory specifications in your development for compatibility purposes.**
<!--DelEnd-->

A derived key is the key session result obtained using the Init-Update-Finish mechanism. It can be managed by HUKS (the key is always in a [TEE](huks-concepts.md)) or independently managed by the service based on service requirements.

> **NOTE**<br>
> PBKDF2 and HKDF do not support derivation based on non-HUKS-managed keys, for example, user passwords. For details about key escrow, see [Key Import Overview and Algorithm Specifications](huks-key-import-overview.md).

| Algorithm/MD| Algorithm/Length of the Base Key| Available Algorithm/Length of the Derived Key| API Version| <!--DelCol5-->Mandatory|
| -------- | -------- | -------- | -------- | -------- |
| HKDF/SHA256 | AES/192-256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
| HKDF/SHA384 | AES/256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
| HKDF/SHA512 | AES/256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
| PBKDF2/SHA256 | AES/192-256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
| PBKDF2/SHA384 | AES/256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
| PBKDF2/SHA512 | AES/256 | AES/128/192/256<br>HMAC/8-1024<br>SM4/128 | 8+ | Yes|
<!--RP1--><!--RP1End-->
