# 使用ECC压缩/非压缩点格式转换(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->
 
支持将压缩/非压缩的点数据转换为Point对象，用于密钥对象生成；也支持将Point对象转换为压缩/非压缩的点数据。

ECC的算法规格请查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。  

通过传入字符串参数format，可指定需要获取的点数据格式。如果需要获取压缩格式，则指定format为："COMPRESSED"；需要获取非压缩格式，则指定format为："UNCOMPRESSED"。

## 指定非压缩点数据转换为压缩点数据

1. 指定Uint8Array类型的ECC非压缩点数据，调用[ECCKeyUtil.convertPoint](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpoint12)，构造[Point](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#point10)对象，用于生成点数据。

2. 调用[ECCKeyUtil.getEncodedPoint](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedpoint12)，获取压缩点数据。

<!-- @[convert_ecc_uncompressed_pub_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/ets/pages/SpecifyUncompressedPublicKey.ets) -->


## 指定压缩点数据获取密钥对象

1. 指定Uint8Array类型的ECC压缩点数据，调用[ECCKeyUtil.convertPoint](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpoint12)，得到[Point](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#point10)对象，用于密钥对象生成。
2. 调用[ECCKeyUtil.genECCCommonParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#genecccommonparamsspec11)，指定曲线名'NID_brainpoolP256r1'，生成ECC的非对称公共密钥参数。
3. 构造[ECCPubKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#eccpubkeyspec10)对象，用于指定ECC算法中公钥包含的参数。ECCPubKeySpec是AsyKeySpec的子类。需要通过参数algName指定算法'ECC'；指定密钥参数类型[AsyKeySpecType.PUBLIC_KEY_SPEC](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#asykeyspectype10)，参数pk指定为得到的point对象。
4. 通过得到的公钥参数，调用[createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)，创建非对称密钥生成器（AsyKeyGeneratorBySpec）。
5. 调用[AsyKeyGeneratorBySpec.generatePubKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatepubkey10)，得到指定的公钥。
6. 调用[ECCKeyUtil.getEncodedPoint](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedpoint12)，得到非压缩点数据。
7. 调用[PubKey.getAsyKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getasykeyspec10)，获取ECC算法中公钥pk的x坐标。

<!-- @[specify_ecc_uncompressed_point_get_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/ets/pages/GetKeyObject.ets) -->
