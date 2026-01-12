# 使用RSA私钥进行编码解码(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

**编码**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)、[AsyKeyGenerator.generateKeyPair](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#generatekeypair-1)，生成RSA密钥类型为RSA1024、素数个数为2的非对称密钥对（KeyPair）。KeyPair对象中包括公钥PubKey、私钥PriKey。

   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)和[随机生成非对称密钥对](crypto-generate-asym-key-pair-randomly.md)理解，参考文档与当前示例可能存在入参差异，请在阅读时注意区分。

2. 传入参数[KeyEncodingConfig](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#keyencodingconfig18)，参数PKCS1/PKCS8，调用[prikey.getEncodedPem](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getencodedpem18)生成编码后的私钥字符串。

**解码**

1. 调用[cryptoFramework.createAsyKeyGenerator](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreateasykeygenerator)生成RSA非对称密钥生成器asyKeyGenerator。

   如何生成RSA非对称密钥对，开发者可参考下文示例，并结合[非对称密钥生成和转换规格：RSA](crypto-asym-key-generation-conversion-spec.md#rsa)。

   > **注意：**
   > 解码应该与编码传入的算法一致。

2. 调用异步[asyKeyGenerator.convertPemKey](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpemkey18)或者同步方法[asyKeyGenerator.convertPemKeySync](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#convertpemkeysync18)，传入编码后的私钥字符串与编码口令。最后返回编码前的私钥字符串。

- 编码示例：

<!-- @[prikey_encoding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/ets/pages/prikeyEncoding.ets) -->

``` TypeScript

import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function prikeyEncoding() {
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = rsaGenerator.generateKeyPairSync();
  let options : cryptoFramework.KeyEncodingConfig = {
      password: '123456',
      cipherName: 'AES-128-CBC'
  }
  let priPemKey = keyPair.priKey;
  let priString = priPemKey.getEncodedPem('PKCS1', options);
  console.info('[sync]TestPriKeyPkcs1Encoded priString output is ' + priString);
}
```


- 解码示例：

<!-- @[prikey_decoding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/KeyGenerationConversion/PrikeyOperation/entry/src/main/ets/pages/prikeyDecoding.ets) -->
