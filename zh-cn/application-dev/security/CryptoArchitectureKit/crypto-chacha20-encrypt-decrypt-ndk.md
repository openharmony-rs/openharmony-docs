# 使用ChaCha20对称密钥加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API22开始，算法库支持该算法。

对应的算法规格请查看[对称密钥加解密算法规格：ChaCha20](crypto-sym-encrypt-decrypt-spec.md#chacha20)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```
## 开发步骤

**创建对象**

调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)、[OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate)，生成密钥算法为ChaCha20的对称密钥（OH_CryptoSymKey）。
   
   如何生成ChaCha20对称密钥，开发者可参考下文示例，并结合[对称密钥生成和转换规格：ChaCha20](crypto-sym-key-generation-conversion-spec.md#chacha20)和[随机生成对称密钥](crypto-generate-sym-key-randomly-ndk.md)理解。参考文档与示例可能存在入参差异，请注意区分。

**加密**

1. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'ChaCha20'，创建对称密钥类型为ChaCha20的Cipher实例，用于完成加密操作。

2. 调用[OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create)创建参数对象，调用[OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam)设置对应的加密参数。

3. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定加密密钥（OH_CryptoSymKey）和对应的加密参数（OH_CryptoSymCipherParams），初始化加密Cipher实例。

4. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（明文）。

5. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取加密后的数据。
   
    > **说明**
    >
    > 由于已使用update传入数据，此处data传入null。
    >
    > doFinal输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，避免产生异常。

6. 调用[OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy)、[OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy)、[OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy)销毁各对象。

**解密**

1. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'ChaCha20'，创建对称密钥类型为ChaCha20的Cipher实例，用于完成解密操作。

2. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为解密（CRYPTO_DECRYPT_MODE），指定解密密钥（OH_CryptoSymKey）和对应的解密参数（OH_CryptoSymCipherParams），初始化解密Cipher实例。

3. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（密文）。

4. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取解密后的数据。

<!-- @[encrypt_decrypt_chacha20_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/cpp/types/project/chacha20_encryption_decryption.cpp) -->

