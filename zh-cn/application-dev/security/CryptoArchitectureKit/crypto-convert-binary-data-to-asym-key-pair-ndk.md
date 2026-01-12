# 指定二进制数据转换非对称密钥对(C/C++)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以RSA、ECC、SM2为例，根据指定的非对称密钥二进制数据，生成非对称密钥对（OH_CryptoKeyPair），即将外部或存储的二进制数据转换为算法库的密钥对象，该对象可用于后续的加解密等操作。

> **说明：**
>
> 针对非对称密钥的convertKey操作：
>
> - 公钥需满足：ASN.1语法、X.509规范、DER编码格式。
>
> - 私钥需满足：ASN.1语法、PKCS\#8规范、DER编码格式。

## 在CMake脚本中链接相关动态库
```txt
target_link_libraries(entry PUBLIC libohcrypto.so)
```

## 指定二进制数据转换RSA密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

1. 获取RSA公钥或私钥二进制数据，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。

   公钥和私钥可单独传入，此处示例传入公钥。

2. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)，指定字符串参数'RSA1024'，创建密钥算法为RSA1024、素数个数为2的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。

   生成RSA非对称密钥时，默认素数为2，此处省略了参数PRIMES_2。

3. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入二进制密钥数据，生成非对称密钥对象（OH_CryptoKeyPair）。

- 以下以生成RSA密钥对为例：

<!-- @[convert_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPair/entry/src/main/cpp/types/project/rsa.cpp) -->


## 指定二进制数据转换ECC密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。

1. 获取ECC公钥或私钥二进制数据，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。

   公钥和私钥可单独传入，此处示例传入公钥和私钥。

2. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)，指定字符串参数'ECC256'，创建密钥算法为ECC、密钥长度为256位的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。

3. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入公钥二进制和私钥二进制，生成非对称密钥对象（OH_CryptoKeyPair）。

- 以下以生成ECC密钥对为例：

<!-- @[convert_ecc_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPair/entry/src/main/cpp/types/project/ecc.cpp) -->


## 指定二进制数据转换SM2密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：SM2](crypto-asym-key-generation-conversion-spec.md#sm2)。

1. 获取SM2公钥或私钥二进制数据，封装成[Crypto_DataBlob](../../reference/apis-crypto-architecture-kit/capi-cryptocommonapi-crypto-datablob.md)。

   公钥和私钥可单独传入，此处示例传入公钥和私钥。

2. 调用[OH_CryptoAsymKeyGenerator_Create](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_create)，指定字符串参数'SM2_256'，创建密钥算法为SM2、密钥长度为256位的非对称密钥生成器（OH_CryptoAsymKeyGenerator）。

3. 调用[OH_CryptoAsymKeyGenerator_Convert](../../reference/apis-crypto-architecture-kit/capi-crypto-asym-key-h.md#oh_cryptoasymkeygenerator_convert)，传入公钥二进制和私钥二进制，生成非对称密钥对象（OH_CryptoKeyPair）。

- 以生成SM2密钥对为例：

<!-- @[convert_sm2_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPair/entry/src/main/cpp/types/project/sm2.cpp) -->


