# 使用私钥对象获取公钥对象(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

从API version 23开始，算法库支持从私钥对象中获取公钥对象的操作。

以RSA为例，根据私钥对象获取公钥对象。

对应的算法规格请查看[非对称密钥加解密算法规格：RSA](crypto-asym-encrypt-decrypt-spec.md#rsa)。

## 开发步骤

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)，指定字符串参数'RSA1024'，创建RSA密钥类型为RSA1024、素数个数为2的非对称密钥生成器（AsyKeyGenerator）。

   生成RSA非对称密钥时，默认素数为2，此处省略了参数PRIMES_2。

2. 调用[AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1)，随机生成非对称密钥对象（KeyPair）。
   
   KeyPair对象中包括公钥PubKey、私钥PriKey。

3. 调用[PubKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded)获取KeyPair中公钥对象的二进制数据。

4. 调用[PriKey.getPubKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getpubkey23)从私钥中获取公钥对象为PubKey。

5. 调用[PubKey.getEncoded](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencoded)获取PubKey对象的二进制数据。

6. 比较两个公钥对象的二进制数据。

- 以异步方式生成RSA密钥对为例（调用方法[getPubKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getpubkey23)）：

<!-- @[prikey_get_pubkey_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/ets/pages/prikeyGetPubkeyAsync.ets) -->


- 以同步方式生成RSA密钥对为例（调用方法[getPubKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getpubkeysync23)）：

<!-- @[prikey_get_pubkey_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/ets/pages/prikeyGetPubKeySync.ets) -->


