# 使用ChaCha20对称密钥（Poly1305模式）加解密(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API22开始，算法库支持该算法。

对应的算法规格请查看[对称密钥加解密算法规格：ChaCha20](crypto-sym-encrypt-decrypt-spec.md#chacha20)。

## 开发步骤

**创建对象**

调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)、[SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1)，生成密钥算法为ChaCha20的对称密钥（SymKey）。
   
   如何生成ChaCha20对称密钥，开发者可参考下文示例，并结合[对称密钥生成和转换规格：ChaCha20](crypto-sym-key-generation-conversion-spec.md#chacha20)和[随机生成对称密钥](crypto-generate-sym-key-randomly.md)理解。参考文档与示例可能存在入参差异，请注意区分。

**加密**

1. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'ChaCha20|Poly1305'，创建对称密钥类型为ChaCha20、模式为Poly1305的Cipher实例，用于完成加密操作。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为加密（CryptoMode.ENCRYPT_MODE），指定加密密钥（SymKey）和Poly1305模式对应的加密参数（Poly1305ParamsSpec），初始化加密Cipher实例。

3. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（明文）。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取加密后的数据。

    > **说明**
    >
    > 由于已使用update传入数据，此处data传入null。
    >
    > doFinal输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，避免产生异常。

5. 读取[Poly1305ParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#poly1305paramsspec22).authTag作为解密的认证信息。

   在Poly1305模式下，需要从加密后的数据中取出末尾16字节，作为解密时初始化的认证信息。

**解密**

1. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'ChaCha20|Poly1305'，创建对称密钥类型为ChaCha20、模式为Poly1305的Cipher实例，用于完成解密操作。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为解密（CryptoMode.DECRYPT_MODE），指定解密密钥（SymKey）和Poly1305模式对应的解密参数（Poly1305ParamsSpec），初始化解密Cipher实例。

3. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（密文）。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取解密后的数据。

- 异步方法示例：

<!-- @[encrypt_decrypt_chacha20_poly1305_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20Poly1305EncryptionDecryptionAsync.ets) -->


- 同步方法示例：

<!-- @[encrypt_decrypt_chacha20_poly1305_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceChaCha20/entry/src/main/ets/pages/chacha20/ChaCha20Poly1305EncryptionDecryptionSync.ets) -->
