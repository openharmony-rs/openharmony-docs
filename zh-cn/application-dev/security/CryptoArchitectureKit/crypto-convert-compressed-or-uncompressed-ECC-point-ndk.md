# 使用ECC压缩/非压缩点格式转换(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

支持将压缩/非压缩的点数据，转换为Point对象，用于密钥对象生成；也支持将Point对象转换为压缩/非压缩的点数据。<br>
ECC的算法规格请查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。<br>
通过传入字符串参数format，可指定获取的点数据格式。如果获取压缩格式，则指定format为："COMPRESSED"；获取非压缩格式，则指定format为："UNCOMPRESSED"。

## 指定非压缩点数据转换为压缩点数据

1. 指定uint8_t类型的ECC非压缩点数据，调用[OH_CryptoEcPoint_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoecpoint_create)，构造[OH_CryptoEcPoint](../../reference/apis-crypto-architecture-kit/capi-cryptoasymkeyapi-oh-cryptoecpoint.md)对象，用于生成点数据。
2. 调用[OH_CryptoEcPoint_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoecpoint_encode)，获取压缩点数据。

<!-- @[convert_ecc_uncompressed_point](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/cpp/types/project/compressedPointData.cpp) -->


## 指定压缩点数据获取密钥对象

1. 指定uint8_t类型的ECC压缩点数据，调用[OH_CryptoEcPoint_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoecpoint_create)，构造[OH_CryptoEcPoint](../../reference/apis-crypto-architecture-kit/capi-cryptoasymkeyapi-oh-cryptoecpoint.md)对象，用于生成点数据。
2. 调用[OH_CryptoEcPoint_Encode](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoecpoint_encode)，获取非压缩点数据。

<!-- @[specify_ecc_uncompressed_point_get_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/ECCCompressPublicKeyFormatConversion/entry/src/main/cpp/types/project/getKeyObject.cpp) -->
