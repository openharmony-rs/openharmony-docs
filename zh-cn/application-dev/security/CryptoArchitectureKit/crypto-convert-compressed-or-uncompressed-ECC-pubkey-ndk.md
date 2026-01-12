# 使用ECC压缩/非压缩公钥格式转换(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

可通过指定ECC公钥数据生成公钥对象（[PubKey](../../reference/apis-crypto-architecture-kit/capi-cryptoasymkeyapi-oh-cryptopubkey.md)），也可从公钥对象中获取ECC公钥数据。
当前仅支持满足X509规范的ECC算法的压缩或非压缩格式的完整公钥数据。此处的公钥数据应当是完整的X509公钥，对于仅使用点数据的情况，请参考[使用ECC压缩/非压缩点格式转换](crypto-convert-compressed-or-uncompressed-ECC-point.md)。    
查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。  
通过传入字符串参数，可指定需要获取的ECC公钥数据格式。如果需要获取满足X509规范的压缩格式数据，则指定参数为："X509|COMPRESSED"；需要获取非压缩格式，则指定参数为："X509|UNCOMPRESSED"。

##  指定非压缩公钥数据转换为压缩公钥数据

1. 指定uint8_t类型的ECC非压缩公钥数据，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。  
公钥和私钥可单独传入，此处示例传入非压缩公钥。
2. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_generate)，指定字符串参数'ECC_BrainPoolP256r1'，创建密钥算法为ECC、密钥长度为256位的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。
3. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入封装后的[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)，生成非对称密钥对象（OH_CryptoKeyPair）。
4. 调用[OH_CryptoPubKey_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptopubkey_encode)，设置参数为'X509|COMPRESSED'，获取压缩公钥数据的字节流。

<!-- @[convert_ecc_uncompressed_pub_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/cpp/types/project/specifyUncompressedPublicKey.cpp) -->

