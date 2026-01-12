# 使用RSA密钥对签名验签 (PKCS1模式)(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[签名验签算法规格：RSA](crypto-sign-sig-verify-overview.md#rsa)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```
## 签名开发步骤
1. 调用[OH_CryptoSign_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_create)，指定字符串参数'RSA1024|PKCS1|SHA256'，创建Sign实例，用于完成签名操作。

2. 调用[OH_CryptoSign_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_init)，使用私钥（OH_CryptoPrivKey）初始化Sign实例。

3. 调用[OH_CryptoSign_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_update)，传入待签名的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。如果数据量较小，可以直接调用OH_CryptoSign_Final接口一次性传入。

4. 调用[OH_CryptoSign_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_final)，获取签名后的数据。

5. 调用[OH_CryptoSign_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_destroy)等释放内存。

```c++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_signature.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"

static OH_Crypto_ErrCode doTestRsaSignature() {
   OH_CryptoAsymKeyGenerator *keyCtx = nullptr;
   OH_CryptoKeyPair *keyPair = nullptr;
   OH_CryptoSign *sign = nullptr;
   Crypto_DataBlob signData = {.data = nullptr, .len = 0};

   uint8_t plainText[] = {
      0x43, 0x31, 0x7d, 0xb5, 0x85, 0x2e, 0xd4, 0xef, 0x08, 0x7a, 0x17, 0x96, 0xbc, 0x7c, 0x8f, 0x80,
      0x8c, 0xa7, 0x63, 0x7f, 0x26, 0x89, 0x8f, 0xf0, 0xfa, 0xa7, 0x51, 0xbd, 0x9c, 0x69, 0x17, 0xf3,
      0xd1, 0xb5, 0xc7, 0x12, 0xbf, 0xcf, 0x91, 0x25, 0x82, 0x23, 0x6b, 0xd6, 0x64, 0x52, 0x77, 0x93,
      0x01, 0x9d, 0x70, 0xa3, 0xf4, 0x92, 0x16, 0xec, 0x3f, 0xa7, 0x3c, 0x83, 0x8d, 0x40, 0x41, 0xfc,
   }; // 待验证数据，仅供参考。
   Crypto_DataBlob msgBlob = {
      .data = reinterpret_cast<uint8_t *>(plainText),
      .len = sizeof(plainText)
   };

   OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create((const char *)"RSA2048", &keyCtx);
   if (ret != CRYPTO_SUCCESS) {
      return ret;
   }
   ret = OH_CryptoAsymKeyGenerator_Generate(keyCtx, &keyPair);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      return ret;
   }

   OH_CryptoPrivKey *privKey = OH_CryptoKeyPair_GetPrivKey(keyPair);
   ret = OH_CryptoSign_Create((const char *)"RSA1024|PKCS1|SHA256", &sign);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      OH_CryptoKeyPair_Destroy(keyPair);
      return ret;
   }

   ret = OH_CryptoSign_Init(sign, privKey);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoKeyPair_Destroy(keyPair);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      return ret;
   }
   ret = OH_CryptoSign_Update(sign, &msgBlob);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoKeyPair_Destroy(keyPair);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      return ret;
   }
   ret = OH_CryptoSign_Final(sign, nullptr, &signData);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoKeyPair_Destroy(keyPair);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      return ret;
   }

   OH_CryptoSign_Destroy(sign);
   OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
   OH_CryptoKeyPair_Destroy(keyPair);
   return CRYPTO_SUCCESS;
}
```

## 验签开发步骤

1. 调用[OH_CryptoVerify_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_create)，指定字符串参数'RSA1024|PKCS1|SHA256'，与签名的Sign实例保持一致。创建Verify实例，用于完成验签操作。

2. 调用[OH_CryptoVerify_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_init)，使用公钥（OH_CryptoPubKey）初始化Verify实例。

3. 调用[OH_CryptoVerify_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_update)，传入待验证的数据。

   当前单次update长度没有限制，开发者可以根据数据量判断如何调用update，如果数据量较小，可以直接调用OH_CryptoVerify_Final接口一次性传入。

   - 当待签名的数据较短时，可以在init完成后直接调用[OH_CryptoVerify_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_final)。
   - 当数据量较大时，可以多次调用update，即[分段验签](crypto-rsa-sign-sig-verify-pkcs1-by-segment-ndk.md)。

4. 调用[OH_CryptoVerify_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_final)，对数据进行验签。

<!-- @[pkcs1_verify_rsa_keypair_sign](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/rsa_pkcs1_signature_validator.cpp) -->

