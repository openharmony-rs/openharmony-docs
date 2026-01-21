# Signing and Signature Verification Overview and Algorithm Specifications

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

After Ukey PIN authentication, an application can use **resourceId** to perform the signing operation on the corresponding key. This capability is implemented using the three-segment API provided by HUKS. The application only needs to specify the algorithm parameters (including the algorithm type, purpose, padding, and digest).

> **NOTE**
>
> 1. [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) is used to specify the key managed by the external key management extension.
> 2. During the signing phase in the three-segment operations, **keyAlias** must be set to the value of **resourceId**.
> 3. The finish phase in the three-segment operations releases resources. If an exception occurs during the operation, **abort** is used to release the resources.

## Specifications

The specifications are related to the implementation of the external hardware key management extension, which vary according to vendors.

| Algorithm/MD Algorithm/Padding Mode| Remarks| API Version| Mandatory|
| -------- | -------- | -------- | -------- |
| RSA/SHA256/PKCS1 | The signature is in the ASN1 format.| 22+ | Yes|
| RSA/SHA384/PKCS1 | The signature is in the ASN1 format.| 22+ | Yes|
| RSA/SHA512/PKCS1 | The signature is in the ASN1 format.| 22+ | Yes|
| RSA/SHA256/PSS | The signature is in the ASN1 format.| 22+ | Yes|
| RSA/SHA384/PSS | The signature is in the ASN1 format.| 22+ | Yes|
| RSA/SHA512/PSS | The signature is in the ASN1 format.| 22+ | Yes|
| ECC/SHA256 | The signature is in the ASN1 format.| 22+ | Yes|
| ECC/SHA384 | The signature is in the ASN1 format.| 22+ | Yes|
| ECC/SHA512 | The signature is in the ASN1 format.| 22+ | Yes|
