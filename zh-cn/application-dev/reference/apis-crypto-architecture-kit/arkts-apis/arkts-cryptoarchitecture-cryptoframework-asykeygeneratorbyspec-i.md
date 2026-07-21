# AsyKeyGeneratorBySpec

AsyKeyGeneratorBySpec非对称密钥生成器。在使用该类的方法前，需要先使用[createAsyKeyGeneratorBySpec()](arkts-cryptoarchitecture-cryptoframework-createasykeygeneratorbyspec-f.md#createasykeygeneratorbyspec-1)方法构建一个AsyKeyGeneratorBySpec实例。

**起始版本：** 10

<!--Device-cryptoFramework-interface AsyKeyGeneratorBySpec--><!--Device-cryptoFramework-interface AsyKeyGeneratorBySpec-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="generatekeypair"></a>
## generateKeyPair

```TypeScript
generateKeyPair(callback: AsyncCallback<KeyPair>): void
```

获取非对称密钥生成器生成的密钥。使用callback异步回调。

当使用[COMMON_PARAMS_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到随机生成的密钥对；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到各项数据与密钥参数一致的密钥对。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generateKeyPair(callback: AsyncCallback<KeyPair>): void--><!--Device-AsyKeyGeneratorBySpec-generateKeyPair(callback: AsyncCallback<KeyPair>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;KeyPair&gt; | 是 | 回调函数。当生成非对称密钥成功时，err为undefined，data为获取到的KeyPair；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：参数类型不正确。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGenerateKeyPair() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  asyKeyGeneratorBySpec.generateKeyPair((err, keyPair) => {
    if (err) {
      console.error(`generateKeyPair failed, errCode: ${err.code}, errMsg: ${err.message}`);
      return;
    }
    console.info('generateKeyPair result: success.');
  })
}

```

<a id="generatekeypair-1"></a>
## generateKeyPair

```TypeScript
generateKeyPair(): Promise<KeyPair>
```

获取该非对称密钥生成器生成的密钥。使用Promise异步回调。

当使用[COMMON_PARAMS_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到随机生成的密钥对；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到各项数据与密钥参数一致的密钥对。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generateKeyPair(): Promise<KeyPair>--><!--Device-AsyKeyGeneratorBySpec-generateKeyPair(): Promise<KeyPair>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KeyPair&gt; | Promise对象，返回非对称密钥KeyPair。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGenerateKeyPair() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  let keyGenPromise = asyKeyGeneratorBySpec.generateKeyPair();
  keyGenPromise.then(keyPair => {
    console.info('generateKeyPair result: success.');
  }).catch((error: BusinessError) => {
    console.error(`generateKeyPair failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}

```

<a id="generatekeypairsync"></a>
## generateKeyPairSync

```TypeScript
generateKeyPairSync(): KeyPair
```

同步获取该非对称密钥生成器生成的密钥。

当使用[COMMON_PARAMS_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到随机生成的密钥对；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到各项数据与密钥参数一致的密钥对。

<br><br>**说明：**<br>建议优先使用异步API{@link generateKeyPair}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generateKeyPairSync(): KeyPair--><!--Device-AsyKeyGeneratorBySpec-generateKeyPairSync(): KeyPair-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyPair](arkts-cryptoarchitecture-cryptoframework-keypair-i.md) | 非对称密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGenerateKeyPairSync() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  try {
    let keyPairData = asyKeyGeneratorBySpec.generateKeyPairSync();
    if (keyPairData != null) {
      console.info('[Sync]: key pair result: success.');
    } else {
      console.error('[Sync]: get key pair result: fail.');
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`sync failed: errCode: ${error.code}, errMsg: ${error.message}`);
  }
}

```

<a id="generateprikey"></a>
## generatePriKey

```TypeScript
generatePriKey(callback: AsyncCallback<PriKey>): void
```

获取非对称密钥生成器生成的密钥。使用callback异步回调。

使用[PRIVATE_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型密钥参数创建密钥生成器，生成指定私钥。使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型密钥参数创建密钥生成器，从生成的密钥对中获取指定私钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePriKey(callback: AsyncCallback<PriKey>): void--><!--Device-AsyKeyGeneratorBySpec-generatePriKey(callback: AsyncCallback<PriKey>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;PriKey&gt; | 是 | 回调函数。当生成私钥成功时，err为undefined，data为获取到的私钥；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：必填参数未指定。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePriKey() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  asyKeyGeneratorBySpec.generatePriKey((err, prikey) => {
    if (err) {
      console.error(`generateKeyPair failed, errCode: ${err.code}, errMsg: ${err.message}`);
      return;
    }
    console.info('generatePriKey result: success.');
  })
}

```

<a id="generateprikey-1"></a>
## generatePriKey

```TypeScript
generatePriKey(): Promise<PriKey>
```

获取该非对称密钥生成器生成的密钥。使用Promise异步回调。

当使用[PRIVATE_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到指定的私钥；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以从生成的密钥对中获取指定的私钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePriKey(): Promise<PriKey>--><!--Device-AsyKeyGeneratorBySpec-generatePriKey(): Promise<PriKey>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PriKey&gt; | Promise对象，返回私钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePriKey() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  let keyGenPromise = asyKeyGeneratorBySpec.generatePriKey();
  keyGenPromise.then(priKey => {
    console.info('generatePriKey result: success.');
  }).catch((error: BusinessError) => {
    console.error(`generatePriKey failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}

```

<a id="generateprikeysync"></a>
## generatePriKeySync

```TypeScript
generatePriKeySync(): PriKey
```

使用该非对称密钥生成器生成私钥。该接口以同步方式返回结果。

当使用[PRIVATE_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到指定的私钥；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以从生成的密钥对中获取指定的私钥。

<br><br>**说明：**<br>建议优先使用异步API{@link generatePriKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePriKeySync(): PriKey--><!--Device-AsyKeyGeneratorBySpec-generatePriKeySync(): PriKey-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 私钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePriKeySync() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  try {
    let priKeyData = asyKeyGeneratorBySpec.generatePriKeySync();
    if (priKeyData != null) {
      console.info('[Sync]: pri key result: success.');
    } else {
      console.error('[Sync]: get pri key result: fail.');
    }
  } catch (e) {
    console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

<a id="generatepubkey"></a>
## generatePubKey

```TypeScript
generatePubKey(callback: AsyncCallback<PubKey>): void
```

获取非对称密钥生成器生成的公钥。使用callback异步回调。

当使用[PUBLIC_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到指定的公钥；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以从生成的密钥对中获取指定的公钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePubKey(callback: AsyncCallback<PubKey>): void--><!--Device-AsyKeyGeneratorBySpec-generatePubKey(callback: AsyncCallback<PubKey>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;PubKey&gt; | 是 | 回调函数。当生成公钥成功时，err为undefined，data为获取到的公钥；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： 参数类型不正确。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePubKey() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  asyKeyGeneratorBySpec.generatePubKey((err, pubKey) => {
    if (err) {
      console.error(`generatePubKey failed, errCode: ${err.code}, errMsg: ${err.message}`);
      return;
    }
    console.info('generatePubKey result: success.');
  })
}

```

<a id="generatepubkey-1"></a>
## generatePubKey

```TypeScript
generatePubKey(): Promise<PubKey>
```

获取该非对称密钥生成器生成的公钥。使用Promise异步回调。

当使用[PUBLIC_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到指定的公钥；当使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以从生成的密钥对中获取指定的公钥。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePubKey(): Promise<PubKey>--><!--Device-AsyKeyGeneratorBySpec-generatePubKey(): Promise<PubKey>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PubKey&gt; | Promise对象，返回非对称密钥的公钥PubKey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePubKey() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  let keyGenPromise = asyKeyGeneratorBySpec.generatePubKey();
  keyGenPromise.then(pubKey => {
    console.info('generatePubKey result: success.');
  }).catch((error: BusinessError) => {
    console.error(`generatePubKey failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}

```

<a id="generatepubkeysync"></a>
## generatePubKeySync

```TypeScript
generatePubKeySync(): PubKey
```

同步获取该非对称密钥生成器生成的密钥。

当使用[PUBLIC_KEY_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数来创建密钥生成器时，可以得到指定的公钥；使用[KEY_PAIR_SPEC](arkts-cryptoarchitecture-cryptoframework-asykeyspectype-e.md)类型的密钥参数时，可以从生成的密钥对中获取指定的公钥。

<br><br>**说明：**<br>建议优先使用异步API{@link generatePubKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-generatePubKeySync(): PubKey--><!--Device-AsyKeyGeneratorBySpec-generatePubKeySync(): PubKey-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 公钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 配置DSA1024公钥和私钥中包含的公共参数。
function genDsa1024CommonSpecBigE() {
  let dsaCommonSpec: cryptoFramework.DSACommonParamsSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    p: BigInt('0xed1501551b8ab3547f6355ffdc2913856ddeca198833dbd04f020e5f25e47c50e0b3894f7690a0d2ea5ed3a7be25c54292a698e1f086eb3a97deb4dbf04fcad2dafd94a9f35c3ae338ab35477e16981ded6a5b13d5ff20bf55f1b262303ad3a80af71aa6aa2354d20e9c82647664bdb6b333b7bea0a5f49d55ca40bc312a1729'),
    q: BigInt('0xd23304044019d5d382cfeabf351636c7ab219694ac845051f60b047b'),
    g: BigInt('0x2cc266d8bd33c3009bd67f285a257ba74f0c3a7e12b722864632a0ac3f2c17c91c2f3f67eb2d57071ef47aaa8f8e17a21ad2c1072ee1ce281362aad01dcbcd3876455cd17e1dd55d4ed36fa011db40f0bbb8cba01d066f392b5eaa9404bfcb775f2196a6bc20eeec3db32d54e94d87ecdb7a0310a5a017c5cdb8ac78597778bd'),
  }
  return dsaCommonSpec;
}

// 设置DSA1024密钥对中包含的全参数。
function genDsa1024KeyPairSpecBigE() {
  let dsaCommonSpec = genDsa1024CommonSpecBigE();
  let dsaKeyPairSpec: cryptoFramework.DSAKeyPairSpec = {
    algName: 'DSA',
    specType: cryptoFramework.AsyKeySpecType.KEY_PAIR_SPEC,
    params: dsaCommonSpec,
    sk: BigInt('0xa2dd2adb2d11392c2541930f61f1165c370aabd2d78d00342e0a2fd9'),
    pk: BigInt('0xae6b5d5042e758f3fc9a02d009d896df115811a75b5f7b382d8526270dbb3c029403fafb8573ba4ef0314ea86f09d01e82a14d1ebb67b0c331f41049bd6b1842658b0592e706a5e4d20c14b67977e17df7bdd464cce14b5f13bae6607760fcdf394e0b73ac70aaf141fa4dafd736bd0364b1d6e6c0d7683a5de6b9221e7f2d6b'),
  }
  return dsaKeyPairSpec;
}

function testGeneratePubKeySync() {
  let asyKeyPairSpec = genDsa1024KeyPairSpecBigE(); // JS输入必须是大端格式的正数。
  let asyKeyGeneratorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(asyKeyPairSpec);
  try {
    let pubKeyData = asyKeyGeneratorBySpec.generatePubKeySync();
    if (pubKeyData != null) {
      console.info('[Sync]: pub key result: success.');
    } else {
      console.error('[Sync]: get pub key result: fail.');
    }
  } catch (e) {
    console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

## algName

```TypeScript
readonly algName: string
```

非对称密钥生成器的算法名。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGeneratorBySpec-readonly algName: string--><!--Device-AsyKeyGeneratorBySpec-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

