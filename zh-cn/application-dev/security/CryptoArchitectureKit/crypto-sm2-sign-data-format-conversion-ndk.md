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

``` C++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"
#include "CryptoArchitectureKit/crypto_signature.h"

OH_Crypto_ErrCode DoTestSm2RStoDER()
{
    static unsigned char rCoordinate[] = {
        107, 93,  198, 247, 119, 18,  40,  110, 90,  156, 193,
        158, 205, 113, 170, 128, 146, 109, 75,  17,  181, 109,
        110, 91,  149, 5,   110, 233, 209, 78,  229, 96};

    static unsigned char sCoordinate[] = {
        45,  153, 88,  82,  104, 221, 226, 43,  174, 21,  122,
        248, 5,   232, 105, 41,  92,  95,  102, 224, 216, 149,
        85,  236, 110, 6,   64,  188, 149, 70,  70,  183};

    // 由R和S生成DER格式的签名数据。
    OH_CryptoEccSignatureSpec *spec = NULL;
    Crypto_DataBlob r = {0};
    Crypto_DataBlob s = {0};
    r.data = rCoordinate;
    r.len = sizeof(rCoordinate);
    s.data = sCoordinate;
    s.len = sizeof(sCoordinate);
    OH_Crypto_ErrCode ret = OH_CryptoEccSignatureSpec_Create(NULL, &spec);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoEccSignatureSpec_Destroy(spec);
        return ret;
    }
    ret = OH_CryptoEccSignatureSpec_SetRAndS(spec, &r, &s);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoEccSignatureSpec_Destroy(spec);
        return ret;
    }
    Crypto_DataBlob sig = {0};
    ret = OH_CryptoEccSignatureSpec_Encode(spec, &sig);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoEccSignatureSpec_Destroy(spec);
        return ret;
    }
    OH_Crypto_FreeDataBlob(&sig);
    OH_CryptoEccSignatureSpec_Destroy(spec);
    spec = NULL;
    return CRYPTO_SUCCESS;
}
```


**指定DER格式，转换为r、s格式**

1. 调用[OH_CryptoEccSignatureSpec_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_create)传入签名数据，创建[OH_CryptoEccSignatureSpec](../../reference/apis-crypto-architecture-kit/capi-cryptosignatureapi-oh-cryptoeccsignaturespec.md)对象，用于获取转换后的数据。

2. 调用[OH_CryptoEccSignatureSpec_GetRAndS](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_getrands)拿到转换后的数据r、s。

3. 调用[OH_CryptoEccSignatureSpec_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoeccsignaturespec_destroy)释放内存。

<!-- @[sm2_der_convert_r_s](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/sm2_der_convert_r_s.cpp) -->
