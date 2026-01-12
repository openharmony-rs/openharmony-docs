# 指定密钥参数生成非对称密钥对(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

以RSA、ECC、SM2为例，根据指定的密钥参数，生成非对称密钥对（KeyPair），并获取密钥参数属性。

该对象可用于后续的加解密等操作。获取的密钥参数属性可用于存储或运输。

## 指定密钥参数生成RSA公钥

对应的算法规格请查看[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

1. 构造[RSACommonParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#rsacommonparamsspec10)对象，用于指定RSA算法中公私钥包含的公共参数（n）。
   
   RSACommonParamsSpec是AsyKeySpec的子类。需要通过参数algName指定算法'RSA'；指定密钥参数类型AsyKeySpecType.COMMON_PARAMS_SPEC，表示是公私钥中包含的公共参数。

   使用密钥参数生成密钥时，用到的bigint类型需要以大端模式输入，且必须为正数。

2. 创建[RSAPubKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#rsapubkeyspec10)对象，用于指定RSA算法中公钥包含的参数（n, pk）。
   
   RSAPubKeySpec是AsyKeySpec的子类。通过参数algName指定算法'RSA'；指定密钥参数类型AsyKeySpecType.PUBLIC_KEY_SPEC，表示是公钥中包含的参数。

3. 调用[cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)，将RSAPubKeySpec对象传入，创建非对称密钥生成器（AsyKeyGeneratorBySpec）。

4. 调用[AsyKeyGeneratorBySpec.generatePubKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatepubkey10)，获得指定的公钥（PubKey）。

5. 调用[PubKey.getAsyKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getasykeyspec10)，获取模数n和公钥pk（即公钥指数e）。

- 以使用callback方式根据密钥参数生成RSA公钥为例：
<!-- @[specify_parameter_generate_rsa_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/rsa/Callback.ets) -->


- 同步返回结果（调用方法[generatePubKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatepubkeysync12)）：
<!-- @[specify_parameter_generate_rsa_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/rsa/Sync.ets) -->


## 指定密钥参数生成ECC密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：ECC](crypto-asym-key-generation-conversion-spec.md#ecc)。

1. 构造[ECCCommonParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ecccommonparamsspec10)对象，用于指定ECC算法中公私钥包含的公共参数。
   ECCCommonParamsSpec是AsyKeySpec的子类。需要通过参数algName指定算法'ECC'；指定密钥参数类型AsyKeySpecType.COMMON_PARAMS_SPEC，表示是公私钥中包含的公共参数。

   使用密钥参数生成密钥时，用到的bigint类型需要以大端模式输入，且必须为正数。

2. 调用[cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)，将ECCCommonParamsSpec对象传入，创建非对称密钥生成器（AsyKeyGeneratorBySpec）。

3. 调用[AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10)，得到随机生成的密钥对（KeyPair）。

4. 分别传入密钥对中的私钥和公钥，调用[PriKey.getAsyKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getasykeyspec10-1)、[PubKey.getAsyKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getasykeyspec10)，获取ECC算法中私钥和公钥的各种密钥参数。

- 以使用Promise方式根据密钥参数生成ECC密钥为例：
<!-- @[specify_parameter_generate_ecc_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/ecc/Promise.ets) -->


- 同步返回结果（调用方法[generateKeyPairSync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypairsync12)）：
<!-- @[specify_parameter_generate_ecc_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/ecc/Sync.ets) -->



## 根据椭圆曲线名生成SM2密钥对

对应的算法规格请查看[非对称密钥生成和转换规格：SM2](crypto-asym-key-generation-conversion-spec.md#sm2)。

1. 构造[ECCCommonParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ecccommonparamsspec10)对象，用于指定非对称公共密钥参数。根据[genECCCommonParamsSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#genecccommonparamsspec11)接口传入相应的NID字符串名称生成相应的非对称公共密钥参数。

    使用密钥参数生成密钥时，用到的bigint类型需要以大端模式输入，且必须为正数。

2. 创建[ECCKeyPairSpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#ecckeypairspec10)对象，并且algName设置为SM2，用于指定SM2算法中密钥对包含的参数。

3. 调用[cryptoFramework.createAsyKeyGeneratorBySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygeneratorbyspec10)，将ECCKeyPairSpec对象传入，创建非对称密钥生成器。

4. 调用[AsyKeyGeneratorBySpec.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair10)，得到各项数据与密钥参数一致的密钥对（KeyPair）。

5. 调用[PriKey.getAsyKeySpec](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getasykeyspec10-1)，获取SM2算法中椭圆曲线参数。

- 以使用Promise方式根据椭圆曲线名生成SM2密钥为例：
<!-- @[specify_parameter_generate_sm2_keypair](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/sm2/Promise.ets) -->


- 同步返回结果（调用方法[generateKeyPairSync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypairsync12)）：
<!-- @[specify_parameter_generate_sm2_keypair_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/SpecifiedParametersGenerateAsymmetricKeyPair/entry/src/main/ets/pages/sm2/Sync.ets) -->

