# 使用ECC压缩/非压缩公钥格式转换(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

可通过指定ECC公钥数据生成公钥对象（PubKey），也可以从公钥对象（PubKey）中获取ECC公钥数据。 

当前仅支持满足X509规范的ECC算法压缩和非压缩格式的公钥数据。此处的公钥数据应当是完整的X509公钥，对于只使用点数据的情况，请参考[使用ECC压缩/非压缩点格式转换](crypto-convert-compressed-or-uncompressed-ECC-point.md)。  
ECC的算法规格请查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。  
通过传入字符串参数format，可指定需要获取的ECC公钥数据格式。如果需要获取满足X509规范的压缩格式数据，则指定format为："X509|COMPRESSED"；需要获取非压缩格式，则指定format为："X509|UNCOMPRESSED"。

##  指定非压缩公钥数据转换为压缩公钥数据

1. 将Uint8Array类型的ECC非压缩公钥数据封装成DataBlob对象。
公钥和私钥可只传入其中一个。此处示例传入非压缩公钥。
2. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'ECC_BrainPoolP256r1'，创建密钥算法为ECC、密钥长度为256位的非对称密钥生成器（AsyKeyGenerator）。
3. 调用[AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)，传入封装后的DataBlob对象，生成非对称密钥对象（KeyPair）。
4. 调用[PubKey.getEncodedDer](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedder12)，设置参数为'X509|COMPRESSED'，获取压缩公钥数据的字节流。

<!-- @[convert_ecc_uncompressed_point](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/ets/pages/CompressedPointData.ets) -->
