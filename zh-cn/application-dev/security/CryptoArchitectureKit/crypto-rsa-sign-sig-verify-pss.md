# 使用RSA密钥对签名验签（PSS模式）(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[签名验签算法规格：RSA](crypto-sign-sig-verify-overview.md#rsa)。

**签名**

1. 调用[cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)、[AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10)，指定密钥参数，生成RSA非对称密钥对（KeyPair）。

   如何生成RSA非对称密钥，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[指定密钥参数生成非对称密钥对](crypto-generate-asym-key-pair-from-key-spec.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign)，指定字符串参数'RSA|PSS|SHA256|MGF1_SHA256'，创建非对称密钥类型为不带长度的RSA、填充模式为PSS、摘要算法为SHA256、掩码算法为MGF1_SHA256的Sign实例，用于完成签名操作。

3. 调用[Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3)，使用私钥（PriKey）初始化Sign实例。

4. 调用[Sign.setSignSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setsignspec10)，设置签名参数。此处设置盐值的长度（SignSpecItem.PSS_SALT_LEN_NUM）为32字节。在验签时将校验此数据。

5. 调用[Sign.getSignSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getsignspec10)，获取其他签名参数。

6. 调用[Sign.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-3)，传入待签名的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。

7. 调用[Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1)，生成数据签名。

**验签**

1. 调用[cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify)，指定字符串参数'RSA2048|PSS|SHA256|MGF1_SHA256'，创建非对称密钥类型为RSA2048、填充模式为PSS、摘要算法为SHA256、掩码算法为MGF1_SHA256的Verify实例，用于完成验签操作。

2. 调用[Verify.setVerifySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setverifyspec10)，设置签名参数。需要与签名时设置的保持一致。

3. 调用[Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5)，使用公钥（PubKey）初始化Verify实例。

4. 调用[Verify.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-5)，传入待验证的数据。当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。

5. 调用[Verify.verify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#verify-1)，对数据进行验签。

- 异步方法示例：

<!-- @[pss_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pss_signature_verification/rsa_pss_signature_verification_asynchronous.ets) -->


- 同步方法示例：

<!-- @[pss_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pss_signature_verification/rsa_pss_signature_verification_synchronous.ets) -->
