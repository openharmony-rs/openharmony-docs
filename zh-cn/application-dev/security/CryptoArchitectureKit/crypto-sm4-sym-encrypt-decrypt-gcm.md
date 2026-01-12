# 使用SM4对称密钥（GCM模式）加解密(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[对称密钥加解密算法规格：SM4](crypto-sym-encrypt-decrypt-spec.md#sm4)。

**加密**

1. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)、[SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1)，生成密钥算法为SM4、密钥长度为128位的对称密钥（SymKey）。
   
   如何生成SM4对称密钥，开发者可参考下文示例，并结合[对称密钥生成和转换规格：SM4](crypto-sym-key-generation-conversion-spec.md#sm4)和[随机生成对称密钥](crypto-generate-sym-key-randomly.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'SM4_128|GCM|PKCS7'，创建对称密钥类型为SM4_128、分组模式为GCM、填充模式为PKCS7的Cipher实例，用于完成加密操作。

3. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为加密（CryptoMode.ENCRYPT_MODE），指定加密密钥（SymKey）和GCM模式对应的加密参数（GcmParamsSpec），初始化加密Cipher实例。

4. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（明文）。
   
   当前单次update长度没有限制，开发者可以根据数据量判断如何调用update。

   - 当数据量较小时，可以在init完成后直接调用doFinal。
   - 当数据量较大时，可以多次调用update，即[分段加解密](crypto-sm4-sym-encrypt-decrypt-gcm-by-segment.md)。

5. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取加密后的数据。
   - 由于已使用update传入数据，此处data传入null。
   - doFinal输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，避免产生异常。

6. 读取[GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag作为解密的认证信息。

   在GCM模式下，需要从加密后的数据中取出末尾16字节，作为解密时初始化的认证信息。示例中authTag恰好为16字节。

**解密**

1. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'SM4_128|GCM|PKCS7'，创建对称密钥类型为SM4_128、分组模式为GCM、填充模式为PKCS7的Cipher实例，用于完成解密操作。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为解密（CryptoMode.DECRYPT_MODE），指定解密密钥（SymKey）和GCM模式对应的解密参数（GcmParamsSpec），初始化解密Cipher实例。

3. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（密文）。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取解密后的数据。

- 异步方法示例：

<!-- @[async_symmetry_encrypt_decrypt_sm4_gcm](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_encryption_decryption/sm4_gcm_encryption_decryption_asynchronous.ets) -->


- 同步方法示例：

<!-- @[sync_symmetry_encrypt_decrypt_sm4_gcm](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceSM4ArkTs/entry/src/main/ets/pages/sm4_gcm_encryption_decryption/sm4_gcm_encryption_decryption_synchronous.ets) -->
