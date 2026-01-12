# 指定二进制数据转换非对称密钥对(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以RSA、ECC、SM2为例，根据指定的非对称密钥二进制数据，生成非对称密钥对（KeyPair），即将外部或存储的二进制数据转换为算法库的密钥对象，该对象可用于后续的加解密等操作。

> **说明：**
>
> 针对非对称密钥的convertKey操作：
>
> - 公钥需满足：ASN.1语法、X.509规范、DER编码格式。
>
> - 私钥需满足：ASN.1语法、PKCS\#8规范、DER编码格式。

## 指定二进制数据转换RSA密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

1. 获取RSA公钥或私钥二进制数据，封装成DataBlob对象。

   公钥和私钥可单独传入，此处示例传入公钥。

2. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'RSA1024'，创建RSA密钥类型为RSA1024、素数个数为2的非对称密钥生成器（AsyKeyGenerator）。

   生成RSA非对称密钥时，默认素数为2，此处省略了参数PRIMES_2。

3. 调用[AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)，传入二进制密钥数据，生成非对称密钥对象（KeyPair）。即将外部或存储的二进制数据转换为算法库的密钥对象，该对象可用于后续的加解密等操作。

- 以使用callback方式生成RSA密钥对为例：

<!-- @[bin_convert_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/rsa/Callback.ets) -->


- 同步返回结果（调用方法[convertKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkeysync12)）：

<!-- @[bin_convert_rsa_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/rsa/Sync.ets) -->


## 指定二进制数据转换ECC密钥对

查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。

1. 获取ECC公钥或私钥二进制数据，封装成DataBlob对象。

   公钥和私钥可以只传入其中一个，此处示例以传入公钥和私钥为例。

2. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'ECC256'，创建密钥算法为ECC、密钥长度为256位的非对称密钥生成器（AsyKeyGenerator）。

3. 调用[AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)，传入公钥二进制和私钥二进制，生成非对称密钥对象（KeyPair）。

- 使用callback方式生成ECC密钥对：

<!-- @[bin_convert_ecc_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/ecc/Callback.ets) -->


- 同步返回结果（调用[convertKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkeysync12)）：

<!-- @[bin_convert_ecc_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/ecc/Sync.ets) -->


## 指定PKCS8二进制数据转换ECC私钥

查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。

获取ECC公钥或私钥二进制数据，封装成DataBlob对象再转为ECC密钥格式。示例如下：

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'ECC256'，创建密钥算法为ECC、密钥长度为256位的非对称密钥生成器（AsyKeyGenerator）。

2. 调用[PubKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded)获取公钥数据字节流，调用[PriKey.getEncodeDer](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedder12-1) 并设置参数为'PKCS8'，获取私钥数据的字节流。由此分别获取密钥对象的二进制数据。

3. 调用[AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)，将生成的二进制密钥数据转为非对称密钥对象（KeyPair）。

<!-- @[pkcs8_convert_ecc_pri_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/pkcs8ecc/PKCS8ECC.ets) -->


## 指定二进制数据转换SM2密钥对

查看[非对称密钥生成和转换规格：SM2](crypto-asym-key-generation-conversion-spec.md#sm2)。

1. 获取SM2公钥或私钥的二进制数据，封装成DataBlob对象。

   公钥和私钥可以只传入其中一个，示例以传入公钥和私钥为例。

2. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'SM2_256'，创建密钥算法为SM2、密钥长度为256位的非对称密钥生成器（AsyKeyGenerator）。

3. 调用[AsyKeyGenerator.convertKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkey-3)，传入公钥和私钥的二进制数据，生成非对称密钥对象（KeyPair）。

- 以使用callback方式生成SM2密钥对为例：

<!-- @[bin_convert_sm2_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/sm2/Callback.ets) -->


- 同步返回结果（调用方法[convertKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertkeysync12)）：

<!-- @[bin_convert_sm2_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/BinaryDataConvertAsymmetricKeyPairArkTS/entry/src/main/ets/pages/sm2/Sync.ets) -->

