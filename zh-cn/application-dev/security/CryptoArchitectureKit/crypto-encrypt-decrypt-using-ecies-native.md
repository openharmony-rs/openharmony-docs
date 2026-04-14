# 使用ECIES混合加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，支持ECIES算法，ECIES是一种基于椭圆曲线密码学的加密算法。

**约束条件：**

- 密钥协商算法支持ECC256、ECC384、ECC521。
- 密钥派生算法仅支持X963KDF，摘要算法支持SHA1、SHA256、SHA384、SHA512。
- 对称加密算法支持AES128、AES192、AES256。
- 分组模式仅支持GCM。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 开发步骤

### 加密

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)和[OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，使用ECC算法生成密钥对。

2. 调用[OH_CryptoKeyAgreement_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_create)和[OH_CryptoKeyAgreement_GenerateSecret](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret)，基于本端的私钥（KeyPair.priKey）与对端的公钥（KeyPair.pubKey）进行密钥协商，返回共享密钥。

3. X963KDF密钥派生，调用[OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create)和[OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive)，基于协商的共享密钥（Secret）进行密钥派生，返回派生后的密钥。

4. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'AES128|GCM'，创建对称密钥类型为AES128、分组模式为GCM的Cipher实例，用于完成加密操作。

5. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定加密密钥（OH_CryptoSymKey），初始化加密Cipher实例。

6. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（明文），获取加密后的数据。

7. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取authTag。

   > **注意：**
   > 在GCM模式下，final会返回authTag，作为解密操作时初始化的认证信息，需要保存。
   > 在GCM模式下，算法库当前只支持16字节的authTag，作为解密操作时初始化的认证信息。

### 解密

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)和[OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，使用ECC算法生成密钥对。

2. 调用[OH_CryptoKeyAgreement_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_create)和[OH_CryptoKeyAgreement_GenerateSecret](../../reference/apis-crypto-architecture-kit/capi-crypto-key-agreement-h.md#oh_cryptokeyagreement_generatesecret)，基于本端的私钥（KeyPair.priKey）与对端的公钥（KeyPair.pubKey）进行密钥协商，返回共享密钥。

3. X963KDF密钥派生，调用[OH_CryptoKdf_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_create)和[OH_CryptoKdf_Derive](../../reference/apis-crypto-architecture-kit/capi-crypto-kdf-h.md#oh_cryptokdf_derive)，基于协商的共享密钥（Secret）进行密钥派生，返回派生后的密钥。

4. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'AES128|GCM'，创建对称密钥类型为AES128、分组模式为GCM的Cipher实例，用于完成解密操作。

5. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为加密（CRYPTO_DECRYPT_MODE），指定加密密钥（OH_CryptoSymKey），初始化解密Cipher实例。

6. 调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（密文）。

7. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取解密数据。

### 示例代码

<!-- @[use_sample_native_test](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceECIES/entry/src/main/cpp/project/native_test.cpp) -->
