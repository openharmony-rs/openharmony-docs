# 使用SM2密钥对签名验签 (C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[签名验签算法规格：SM2](crypto-sign-sig-verify-overview.md#sm2)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 签名开发步骤
1. 调用[OH_CryptoSign_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_create)，指定字符串参数'SM2_256|SM3'，创建非对称密钥类型为SM2_256、摘要算法为SM3的Sign实例，用于完成签名操作。

2. 调用[OH_CryptoSign_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_init)，使用私钥[OH_CryptoPrivKey](../../reference/apis-crypto-architecture-kit/capi-cryptoasymkeyapi-oh-cryptoprivkey.md)初始化Sign实例。

3. 调用[OH_CryptoSign_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_update)，传入待签名的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。如果数据量较小，可以直接调用OH_CryptoSign_Final接口一次性传入。

4. 调用[OH_CryptoSign_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_final)，获取签名后的数据。

5. 调用[OH_CryptoSign_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptosign_destroy)等释放内存。

```c++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_asym_key.h"
#include "CryptoArchitectureKit/crypto_signature.h"

static OH_Crypto_ErrCode doSm2Test() {
   OH_CryptoAsymKeyGenerator *keyCtx = nullptr;
   OH_CryptoKeyPair *keyPair = nullptr;
   OH_CryptoSign *sign = nullptr;

   uint8_t plainText[] = {
      0x96, 0x46, 0x2e, 0xde, 0x3f, 0x47, 0xbf, 0xd6, 0x87, 0x48, 0x36, 0x1d, 0x75, 0x35, 0xbd, 0xbc,
      0x6b, 0x06, 0xe8, 0xb3, 0x68, 0x91, 0x53, 0xce, 0x76, 0x5d, 0x24, 0xda, 0xdc, 0xc4, 0x9f, 0x94,
   };
   Crypto_DataBlob msgBlob = {
      .data = reinterpret_cast<uint8_t *>(plainText),
      .len = sizeof(plainText)};

   OH_Crypto_ErrCode ret = OH_CryptoAsymKeyGenerator_Create((const char *)"SM2_256", &keyCtx);
   if (ret != CRYPTO_SUCCESS) {
      return ret;
   }
   ret = OH_CryptoAsymKeyGenerator_Generate(keyCtx, &keyPair);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      return ret;
   }

   OH_CryptoPrivKey *privKey = OH_CryptoKeyPair_GetPrivKey(keyPair);
   ret = OH_CryptoSign_Create((const char *)"SM2_256|SM3", &sign);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      OH_CryptoKeyPair_Destroy(keyPair);
      return ret;
   }
   ret = OH_CryptoSign_Init(sign, privKey);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      OH_CryptoKeyPair_Destroy(keyPair);
      return ret;
   }

   ret = OH_CryptoSign_Update(sign, &msgBlob);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      OH_CryptoKeyPair_Destroy(keyPair);
      return ret;
   }

   Crypto_DataBlob signBlob = {.data = nullptr, .len = 0};
   ret = OH_CryptoSign_Final(sign, nullptr, &signBlob);
   if (ret != CRYPTO_SUCCESS) {
      OH_CryptoSign_Destroy(sign);
      OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
      OH_CryptoKeyPair_Destroy(keyPair);
      return ret;
   }
   OH_CryptoSign_Destroy(sign);
   OH_CryptoAsymKeyGenerator_Destroy(keyCtx);
   OH_CryptoKeyPair_Destroy(keyPair);
   OH_Crypto_FreeDataBlob(&signBlob);
   return CRYPTO_SUCCESS;
}
```


## 验签开发步骤

1. 调用[OH_CryptoVerify_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_create)，指定字符串参数'SM2_256|SM3'，创建非对称密钥类型为SM2_256、摘要算法为SM3的Verify实例，用于完成验签操作。

2. 调用[OH_CryptoVerify_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_init)，使用公钥（OH_CryptoPubKey）初始化Verify实例。

3. 调用[OH_CryptoVerify_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_update)，传入待验证的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update，如果数据量较小，可以直接调用OH_CryptoVerify_Final接口一次性传入。

4. 调用[OH_CryptoVerify_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-signature-h.md#oh_cryptoverify_final)，对数据进行验签。

<!-- @[verify_signatures_with_sm2_key_pair_c](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerification/entry/src/main/cpp/types/project/sm2_signature_verification.cpp) -->

