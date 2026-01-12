# 使用RSA非对称密钥（PKCS1_OAEP模式）加解密

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[非对称密钥加解密算法规格：RSA](crypto-asym-encrypt-decrypt-spec.md#rsa)。

**加密**

1. 调用[cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)、[AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10)，指定密钥参数，生成RSA非对称密钥对（KeyPair）。
   
   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[指定密钥参数生成非对称密钥对](crypto-generate-asym-key-pair-from-key-spec.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'RSA2048|PKCS1_OAEP|SHA256|MGF1_SHA1'，创建非对称密钥类型为RSA2048、填充模式为PKCS1_OAEP、摘要算法为SHA256、掩码摘要为MGF1_SHA1的RSA密钥的Cipher实例，用于完成加解密操作。

3. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为加密（CryptoMode.ENCRYPT_MODE），指定加密密钥（KeyPair.PubKey），初始化加密Cipher实例。
   
   非对称密钥无加密参数，直接传入null。

4. 在调用Cipher.doFinal前，调用[Cipher.setCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setcipherspec10)设置PKCS1_OAEP填充参数pSource。调用[Cipher.getCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getcipherspec10)可获得OAEP相关参数。

5. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，传入明文，获取加密后的数据。

**解密**


1. 由于RSA算法的Cipher实例不支持重复init操作，需要调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，重新生成Cipher实例。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为解密（CryptoMode.DECRYPT_MODE），指定解密密钥（KeyPair.PriKey）初始化解密Cipher实例。PKCS1模式无加密参数，直接传入null。

3. 在调用Cipher.doFinal前，调用[Cipher.setCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#setcipherspec10)设置PKCS1_OAEP填充参数pSource，此处需要和加密时设置的保持一致。调用[Cipher.getCipherSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getcipherspec10)可获得OAEP相关参数。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，传入密文，获取解密后的数据。

- 异步方法示例：

<!-- @[pss_verify_rsa_keypair_sign_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1_oaep/RSAPKCS1OAEPAsync.ets) -->


- 同步方法示例：

<!-- @[pss_verify_rsa_keypair_sign_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceRSA/entry/src/main/ets/pages/rsa_pkcs1_oaep/RSAPKCS1OAEPSync.ets) -->
