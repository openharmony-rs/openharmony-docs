# 使用RSA私钥进行编码解码(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

**编码**

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)、[OH_CryptoAsymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，生成RSA密钥类型为RSA2048、素数个数为2的非对称密钥对（keyPair）。keyPair对象中包括公钥PubKey、私钥PriKey。

   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[随机生成非对称密钥对(C/C++)](crypto-generate-asym-key-pair-randomly-ndk.md)理解。参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[OH_CryptoPrivKeyEncodingParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_create)创建参数对象（params），并通过[OH_CryptoPrivKeyEncodingParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoprivkeyencodingparams_setparam)设置加密算法和密码。

3. 调用[OH_CryptoPrivKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoprivkey_encode)，传入参数CRYPTO_PEM/CRYPTO_DER、PKCS1/PKCS8和参数对象（params）生成编码后的私钥字符串。

**解码**

1. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)生成RSA非对称密钥生成器keyGen。

   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

2. 调用[OH_CryptoAsymKeyGenerator_SetPassword]，传入编码后的私钥字符串与编码口令。

3. 调用[OH_CryptoAsymKeyGenerator_Convert]，传入参数CRYPTO_PEM和编码后的私钥字符串，返回RSA密钥对。

- 编码示例：

<!-- @[prikey_encoding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/cpp/types/project/prikey_encoding.cpp) -->


- 解码示例：

<!-- @[prikey_decoding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/cpp/types/project/prikey_decoding.cpp) -->
