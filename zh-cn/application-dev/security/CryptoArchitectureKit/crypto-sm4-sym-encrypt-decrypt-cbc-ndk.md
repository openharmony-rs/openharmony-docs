# 使用SM4对称密钥（CBC模式）加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[对称密钥加解密算法规格：SM4](crypto-sym-encrypt-decrypt-spec.md#sm4)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

**加密**

1. 调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)、[OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate)，生成密钥算法为SM4、密钥长度为128位的对称密钥（OH_CryptoSymKey）。
   
   如何生成SM4对称密钥，开发者可参考下文示例，并结合[对称密钥生成和转换规格：SM4](crypto-sym-key-generation-conversion-spec.md#sm4)和[随机生成对称密钥](crypto-generate-sym-key-randomly-ndk.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'SM4_128|CBC|PKCS7'，创建对称密钥类型为SM4_128、分组模式为CBC、填充模式为PKCS7的Cipher实例，用于完成加密操作。

3. 调用[OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create)创建参数对象，调用[OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam)设置对应的加密参数。

4. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定加密密钥（OH_CryptoSymKey）和CBC模式对应的加密参数（OH_CryptoSymCipherParams），初始化加密Cipher实例。

5. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（明文）。
   
   - 当数据量较小时，可以在init完成后直接调用final。
   - 当数据量较大时，可以多次调用update，即分段加解密。

6. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取加密后的数据。
   
   - 由于已使用update传入数据，此处data传入null。
   - final输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，避免产生异常。

7. 调用[OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy)、[OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy)、[OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy)销毁各对象。

**解密**

1. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'SM4_128|CBC|PKCS7'，创建对称密钥类型为SM4_128、分组模式为CBC、填充模式为PKCS7的Cipher实例，用于完成解密操作。

2. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为解密（CRYPTO_DECRYPT_MODE），指定解密密钥（OH_CryptoSymKey）和CBC模式对应的解密参数（OH_CryptoSymCipherParams），初始化解密Cipher实例。

3. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（密文）。

4. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取解密后的数据。

```c++
#include "CryptoArchitectureKit/crypto_common.h"
#include "CryptoArchitectureKit/crypto_sym_cipher.h"
#include <string.h>

static OH_Crypto_ErrCode doTestSm4Cbc()
{
    OH_CryptoSymKeyGenerator *genCtx = nullptr;
    OH_CryptoSymCipher *encCtx = nullptr;
    OH_CryptoSymCipher *decCtx = nullptr;
    OH_CryptoSymKey *keyCtx = nullptr;
    OH_CryptoSymCipherParams *params = nullptr;
    Crypto_DataBlob outUpdate = {.data = nullptr, .len = 0};
    Crypto_DataBlob decUpdate = {.data = nullptr, .len = 0};

    char *plainText = const_cast<char *>("this is test!");
    Crypto_DataBlob msgBlob = {.data = (uint8_t *)(plainText), .len = strlen(plainText)};
    uint8_t iv[16] = {1, 2, 4, 12, 3, 4, 2, 3, 3, 2, 0, 4, 3, 1, 0, 10}; // iv使用安全随机数生成。
    Crypto_DataBlob ivBlob = {.data = iv, .len = sizeof(iv)};
    // 生成对称密钥。
    OH_Crypto_ErrCode ret;
    ret = OH_CryptoSymKeyGenerator_Create("SM4_128", &genCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymKeyGenerator_Generate(genCtx, &keyCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // 设置参数。
    ret = OH_CryptoSymCipherParams_Create(&params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipherParams_SetParam(params, CRYPTO_IV_DATABLOB, &ivBlob);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // 加密。
    ret = OH_CryptoSymCipher_Create("SM4_128|CBC|PKCS7", &encCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(encCtx, CRYPTO_ENCRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(encCtx, &msgBlob, &outUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // 解密。
    ret = OH_CryptoSymCipher_Create("SM4_128|CBC|PKCS7", &decCtx);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Init(decCtx, CRYPTO_DECRYPT_MODE, keyCtx, params);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }
    ret = OH_CryptoSymCipher_Final(decCtx, &outUpdate, &decUpdate);
    if (ret != CRYPTO_SUCCESS) {
        goto end;
    }

    // 资源释放。
end:
    OH_CryptoSymCipherParams_Destroy(params);
    OH_CryptoSymCipher_Destroy(encCtx);
    OH_CryptoSymCipher_Destroy(decCtx);
    OH_CryptoSymKeyGenerator_Destroy(genCtx);
    OH_CryptoSymKey_Destroy(keyCtx);
    OH_Crypto_FreeDataBlob(&outUpdate);
    OH_Crypto_FreeDataBlob(&decUpdate);
    return ret;
}
```