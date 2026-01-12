# 使用AES对称密钥（GCM模式）加解密(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[对称密钥加解密算法规格：AES](crypto-sym-encrypt-decrypt-spec.md#aes)。

**加密**

1. 调用[cryptoFramework.createSymKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatesymkeygenerator)，生成密钥算法为AES、密钥长度为128位的对称密钥（SymKey）。然后调用[SymKeyGenerator.generateSymKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatesymkey-1)生成对称密钥。
   
   如何生成AES对称密钥，开发者可以参考以下示例，并结合[对称密钥生成和转换规格：AES](crypto-sym-key-generation-conversion-spec.md#aes)和[随机生成对称密钥](crypto-generate-sym-key-randomly.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'AES128|GCM|PKCS7'，创建对称密钥类型为AES128、分组模式为GCM、填充模式为PKCS7的Cipher实例，用于完成加密操作。

3. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为加密（CryptoMode.ENCRYPT_MODE），指定加密密钥（SymKey）和GCM模式对应的加密参数（GcmParamsSpec），以初始化加密Cipher实例。

4. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（明文）。
   
   当前单次update无长度限制，开发者可根据数据量调用update。

   - 当数据量较小时，可以在init完成后直接调用doFinal。
   - 当数据量较大时，可以多次调用update，即[分段加解密](crypto-aes-sym-encrypt-decrypt-gcm-by-segment.md)。

5. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取加密后的数据。注意，由于已使用update传入数据，此处data传入null。doFinal输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，避免产生异常。
   - 已使用update传入数据，data传入null。
   - doFinal输出可能为null，访问数据前先判断结果。

6. 读取[GcmParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#gcmparamsspec).authTag作为解密的认证信息。

   在GCM模式下，算法库目前仅支持16字节的authTag，用于解密时的初始化认证。示例中的authTag恰好为16字节。

**解密**

1. 调用[cryptoFramework.createCipher](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatecipher)，指定字符串参数'AES128|GCM|PKCS7'，创建对称密钥类型为AES128、分组模式为GCM、填充模式为PKCS7的Cipher实例，用于完成解密操作。

2. 调用[Cipher.init](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#init-1)，设置模式为解密（CryptoMode.DECRYPT_MODE），指定解密密钥（SymKey）和GCM模式对应的解密参数（GcmParamsSpec），初始化解密Cipher实例。

3. 调用[Cipher.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-1)，更新数据（密文）。

4. 调用[Cipher.doFinal](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#dofinal-1)，获取解密后的数据。

- 异步方法示例：

  <!-- @[gcm_encrypt_decrypt_aes_symkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_encryption_decryption/aes_gcm_encryption_decryption_asynchronous.ets) -->


- 同步方法示例：

  <!-- @[gcm_encrypt_decrypt_aes_symkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAesArkTs/entry/src/main/ets/pages/aes_gcm_encryption_decryption/aes_gcm_encryption_decryption_synchronous.ets) -->
