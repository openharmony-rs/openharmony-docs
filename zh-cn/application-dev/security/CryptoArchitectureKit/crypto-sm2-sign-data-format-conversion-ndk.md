# SM2签名数据格式转换 (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

当前支持DER格式与r、s格式互转的能力。

开发者可指定SM2密文的参数，将其转换成DER格式密文。反之，也可以从DER格式密文中提取出SM2的具体密文参数。

**指定密文参数，转换为DER格式**
1. 调用[OH_CryptoEccSignatureSpec_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_create)，创建[OH_CryptoEccSignatureSpec](../../reference/apis-crypto-architecture-kit/capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md)对象，用于设置SM2密文参数。

2. 调用[OH_CryptoEccSignatureSpec_SetRAndS](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_setrands)，将R、S设置到OH_CryptoEccSignatureSpec对象中。

3. 调用[OH_CryptoEccSignatureSpec_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_encode)得到转换后的DER格式的密文。

4. 调用[OH_CryptoEccSignatureSpec_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_destroy)释放对象。

<!-- @[sm2_signature_format_conversion_der](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/sm2_signature_format_conversion_der.cpp) -->


**指定DER格式，转换为r、s格式**

1. 调用[OH_CryptoEccSignatureSpec_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_create)传入签名数据，创建[OH_CryptoEccSignatureSpec](../../reference/apis-crypto-architecture-kit/capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md)对象，用于获取转换后的数据。

2. 调用[OH_CryptoEccSignatureSpec_GetRAndS](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_getrands)拿到转换后的数据r、s。

3. 调用[OH_CryptoEccSignatureSpec_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_destroy)释放内存。

<!-- @[sm2_der_convert_r_s](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/sm2_der_convert_r_s.cpp) -->
