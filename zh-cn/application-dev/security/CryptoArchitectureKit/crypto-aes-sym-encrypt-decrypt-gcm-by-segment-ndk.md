# 使用AES对称密钥（GCM模式）分段加解密(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[对称密钥加解密算法规格：AES](crypto-sym-encrypt-decrypt-spec.md#aes)。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 开发步骤

**创建对象**

调用[OH_CryptoSymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_create)和[OH_CryptoSymKeyGenerator_Generate](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_generate)，生成密钥算法为AES、密钥长度为128位的对称密钥（OH_CryptoSymKey）。
   
   如何生成AES对称密钥，开发者可参考下文示例，并结合[对称密钥生成和转换规格：AES](crypto-sym-key-generation-conversion-spec.md#aes)和[随机生成对称密钥](crypto-generate-sym-key-randomly-ndk.md)文档进行理解。参考文档与当前示例可能存在入参差异，请注意区分。

**加密**

1. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定字符串参数'AES128|GCM|PKCS7'，创建对称密钥算法为AES128、分组模式为GCM、填充模式为PKCS7的Cipher实例，用于完成加密操作。

2. 调用[OH_CryptoSymCipherParams_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_create)创建参数对象，调用[OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam)设置对应的加密参数。

3. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为加密（CRYPTO_ENCRYPT_MODE），指定对称密钥（OH_CryptoSymKey）和GCM模式的加密参数（OH_CryptoSymCipherParams），以初始化加密 Cipher 实例。

4. 将一次传入数据量设置为20字节，多次调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（明文）。
   
   - 当前单次update没有长度限制，开发者可根据数据量判断如何调用update。
   - 建议开发者对每次update的结果都判断是否为null，并在结果不为null时取出其中的密文进行拼接，形成完整的密文。因为在不同的规格下，update的结果可能会受到不同影响。
      
      1）例如ECB和CBC模式，始终以分组为基本单位进行加密，并输出本次更新产生的加密分组结果。即当本次更新操作凑满一个分组时，输出密文；若未凑满，则本次更新输出null，将未加密的数据与下次输入的数据拼接后，再进行分组输出。最后进行doFinal操作时，将未加密的数据根据指定的填充模式进行填充，再输出剩余加密结果。解密过程中的update操作同理。

      2）对于流加密模式（比如CTR和OFB模式），通常密文长度和明文长度相等。

5. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)，获取密文。
   
   - 由于已使用update传入数据，此处传入null。
   - final输出结果可能为null，在访问具体数据前，需要先判断结果是否为null，以避免产生异常。
   > **注意：**
   > 在GCM模式下，final会返回authTag，作为解密操作时初始化的认证信息，需要保存。
   > 在GCM模式下，算法库当前只支持16字节的authTag，作为解密操作时初始化的认证信息。示例中authTag恰好为16字节。

**解密**

1. 调用[OH_CryptoSymCipher_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_create)，指定参数'AES128|GCM|PKCS7'，创建对称密钥类型为AES128、分组模式为GCM、填充模式为PKCS7的Cipher实例，完成解密操作。

2. 调用[OH_CryptoSymCipherParams_SetParam](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_setparam)设置authTag作为解密的认证信息。
   
   在GCM模式下，从加密后的数据中取出末尾16字节，作为解密时初始化的认证信息。示例中authTag恰好为16字节。

3. 调用[OH_CryptoSymCipher_Init](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_init)，设置模式为解密（CRYPTO_DECRYPT_MODE），指定解密密钥（OH_CryptoSymKey）和GCM模式对应的解密参数（OH_CryptoSymCipherParams），初始化解密Cipher实例。

4. 将一次传入数据量设置为20字节，多次调用[OH_CryptoSymCipher_Update](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_update)，更新数据（密文）。

5. 调用[OH_CryptoSymCipher_Final](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_final)获取解密数据。

**销毁对象**

调用[OH_CryptoSymKeyGenerator_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-key-h.md#oh_cryptosymkeygenerator_destroy)、[OH_CryptoSymCipher_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipher_destroy)和[OH_CryptoSymCipherParams_Destroy](../../reference/apis-crypto-architecture-kit/capi-crypto-sym-cipher-h.md#oh_cryptosymcipherparams_destroy)销毁各对象。

<!-- @[gcm_seg_encrypt_decrypt_aes_symkey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/EncryptionDecryption/EncryptionDecryptionGuidanceAes/entry/src/main/cpp/types/project/aes_gcm_segment_encryption_decryption.cpp) -->

