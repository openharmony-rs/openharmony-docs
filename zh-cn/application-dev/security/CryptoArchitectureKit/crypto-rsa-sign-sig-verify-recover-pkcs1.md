# 使用RSA密钥对（PKCS1模式）签名及签名恢复(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[签名验签算法规格：RSA](crypto-sign-sig-verify-overview.md#rsa)。

**签名**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)、[AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1)，生成密钥算法为RSA、密钥长度为1024位、素数个数为2的非对称密钥对象（KeyPair），包括公钥（PubKey）和私钥（PriKey）。
   
   如何生成RSA非对称密钥，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[随机生成非对称密钥对](crypto-generate-asym-key-pair-randomly.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[cryptoFramework.createSign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesign)，指定字符串参数'RSA1024|PKCS1|SHA256|SignOnly'，创建非对称密钥类型为RSA1024、填充模式为PKCS1、摘要算法为SHA256的Sign实例，用于完成仅签名操作。

3. 调用[Sign.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-3)，使用私钥（PriKey）初始化Sign实例。

4. 调用[Sign.sign](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#sign-1)，生成数据签名。

**验签**

1. 调用[cryptoFramework.createVerify](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateverify)，指定字符串参数'RSA1024|PKCS1|SHA256|Recover'，与签名的Sign实例保持一致。创建Verify实例，用于完成验签操作。

2. 调用[Verify.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-5)，使用公钥（PubKey）初始化Verify实例。

3. 调用[Verify.recover](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#recover12)，对数据进行签名恢复。

- 异步方法示例：

<!-- @[pkcs1_recover_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_restoration/rsa_pkcs1_signature_restoration_asynchronous.ets) -->


- 同步方法示例：

<!-- @[pkcs1_recover_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/SignatureVerification/SigningSignatureVerificationArkTs/entry/src/main/ets/pages/rsa_pkcs1_signature_restoration/rsa_pkcs1_signature_restoration_synchronous.ets) -->

