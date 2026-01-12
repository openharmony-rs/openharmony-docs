# 使用SM2非对称密钥加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[非对称密钥加解密算法规格：SM2](crypto-asym-encrypt-decrypt-spec.md#sm2)。

**加密**

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)、[OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，生成SM2密钥类型为SM2_256的非对称密钥对（keyPair）。keyPair对象中包括公钥PubKey、私钥PriKey。

   如何生成SM2非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：SM2](crypto-asym-key-generation-conversion-spec.md#sm2)和[随机生成非对称密钥对](crypto-generate-asym-key-pair-randomly-ndk.md)理解。参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create)，指定字符串参数'SM2_256|SM3'，创建非对称密钥类型为SM2_256、摘要算法为SM3的Cipher实例，用于完成加解密操作。

3. 调用[OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定加密密钥（keyPair），初始化加密Cipher实例。

4. 调用[OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final)，传入明文，获取加密后的数据。

   OH_CryptoAsymCipher_Final输出结果可能为NULL，在访问具体数据前，需要先判断结果是否为NULL，避免产生异常。

**解密**

1. 由于SM2算法的Cipher实例不支持重复init操作，需要调用[OH_CryptoAsymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_create)，重新生成Cipher实例。

2. 调用[OH_CryptoAsymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_init)，设置模式为解密（CRYPTO_DECRYPT_MODE），指定解密密钥（keyPair）初始化解密Cipher实例。

3. 调用[OH_CryptoAsymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-cipher-h.md#oh_cryptoasymcipher_final)，传入密文，获取解密后的数据。

<!-- @[encrypt_decrypt_sm2_asymkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceCpp/entry/src/main/cpp/types/project/sm2/SM2EncryptionDecryption.cpp) -->
