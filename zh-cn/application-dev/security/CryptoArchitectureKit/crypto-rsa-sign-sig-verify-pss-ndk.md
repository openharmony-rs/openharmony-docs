# 使用RSA密钥对签名验签 (PSS模式)(C/C++)

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
1. 调用[OH_CryptoSign_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_create)，指定字符串参数'RSA2048|PSS|SHA256|MGF1_SHA256'，创建非对称密钥类型为RSA2048、填充模式为PSS、摘要算法为SHA256、掩码算法为MGF1_SHA256的Sign实例，用于完成签名操作。
2. 调用[OH_CryptoSign_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_init)，使用私钥（OH_CryptoPrivKey）初始化Sign实例。
3. 调用[OH_CryptoSign_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_update)，传入待签名的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。如果数据量较小，可以直接调用OH_CryptoSign_Final接口一次性传入。
4. 调用[OH_CryptoSign_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_final)，获取签名后的数据。
5. 调用[OH_CryptoSign_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_destroy)等释放内存。

```c++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_signature.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"

static OH_Crypto_ErrCode doTestRsaPssSignSeg() {
   OH_CryptoAsymKeyGenerator *keyCtx = nullptr;
   OH_CryptoKeyPair *keyPair = nullptr;
   OH_CryptoSign *sign = nullptr;
   Crypto_DataBlob signData = {.data = nullptr, .len = 0};

   uint8_t plainText[] = {
      0x13, 0xa7, 0x73, 0xe8, 0xb8, 0x22, 0x99, 0x72, 0x98, 0x29, 0xae, 0x74, 0xa8, 0x4a, 0xea, 0xa9,
   };
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
   ret = OH_CryptoSign_Create((const char *)"RSA2048|PSS|SHA256|MGF1_SHA256", &sign);
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

## 开发步骤

1. 调用[OH_CryptoVerify_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_create)，指定字符串参数'RSA2048|PSS|SHA256|MGF1_SHA256'，创建非对称密钥类型为RSA2048、填充模式为PSS、摘要算法为SHA256、掩码算法为MGF1_SHA256的Verify实例，用于完成验签操作。

2. 调用[OH_CryptoVerify_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_setparam)，设置签名参数。需要与签名时设置的保持一致。

3. 调用[OH_CryptoVerify_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_init)，使用公钥（OH_CryptoPubKey）初始化Verify实例。

4. 调用[OH_CryptoVerify_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_update)，传入待验证的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update，如果数据量较小，可以直接调用OH_CryptoVerify_Final接口一次性传入。

5. 调用[OH_CryptoVerify_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_final)，对数据进行验签。

<!-- @[pss_verify_rsa_keypair_sign](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/rsa_pss_verification_tool.cpp) -->

