# PubKey

公钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在非对称加密、签名验证、密钥协商时需要将其对象作为输入使用。

公钥可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md)、 [AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md)来生成。

**继承/实现关系：** PubKey extends [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## getAsyKeySpec

```TypeScript
getAsyKeySpec(itemType: AsyKeySpecItem): bigint | string | number
```

获取密钥参数。此API以同步方式返回结果。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeySpecItem](arkts-cryptoarchitecture-cryptoframework-asykeyspecitem-e.md) | 是 | 指定的密钥参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint \| string \| number | 获取的密钥参数内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported.<br>**适用版本：** 12+ |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

// 根据关键规范构造EccCommonSpec结构体。EccCommonSpec结构体定义了ECC私钥和公钥的公共参数。
function genEccCommonSpec(): cryptoFramework.ECCCommonParamsSpec {
  let fieldFp: cryptoFramework.ECFieldFp = {
    fieldType: 'Fp',
    p: BigInt('0xffffffffffffffffffffffffffffffff000000000000000000000001')
  }
  let G: cryptoFramework.Point = {
    x: BigInt('0xb70e0cbd6bb4bf7f321390b94a03c1d356c21122343280d6115c1d21'),
    y: BigInt('0xbd376388b5f723fb4c22dfe6cd4375a05a07476444d5819985007e34')
  }
  let eccCommonSpec: cryptoFramework.ECCCommonParamsSpec = {
    algName: 'ECC',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    field: fieldFp,
    a: BigInt('0xfffffffffffffffffffffffffffffffefffffffffffffffffffffffe'),
    b: BigInt('0xb4050a850c04b3abf54132565044b0b7d7bfd8ba270b39432355ffb4'),
    g: G,
    n: BigInt('0xffffffffffffffffffffffffffff16a2e0b8f03e13dd29455c5c2a3d'),
    h: 1
  }
  return eccCommonSpec;
}

async function testgetAsyKeySpec() {
  let commKeySpec = genEccCommonSpec(); // 使用参数属性，构造ECC公私钥公共密钥参数对象。
  let generatorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(commKeySpec); // 使用密钥参数对象创建生成器。
  let keyPair = await generatorBySpec.generateKeyPair();
  let pubKey = keyPair.pubKey;
  let eccPrimeP = pubKey.getAsyKeySpec(cryptoFramework.AsyKeySpecItem.ECC_FP_P_BN);
  console.info('ecc item --- p: ' + eccPrimeP.toString(16));
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
// 根据关键规范构造EccCommonSpec结构体。EccCommonSpec结构体定义了ECC私钥和公钥的公共参数。
function genEccCommonSpec(): cryptoFramework.ECCCommonParamsSpec {
  let fieldFp: cryptoFramework.ECFieldFp = {
    fieldType: 'Fp',
    p: BigInt('0xffffffffffffffffffffffffffffffff000000000000000000000001')
  }
  let G: cryptoFramework.Point = {
    x: BigInt('0xb70e0cbd6bb4bf7f321390b94a03c1d356c21122343280d6115c1d21'),
    y: BigInt('0xbd376388b5f723fb4c22dfe6cd4375a05a07476444d5819985007e34')
  }
  let eccCommonSpec: cryptoFramework.ECCCommonParamsSpec = {
    algName: 'ECC',
    specType: cryptoFramework.AsyKeySpecType.COMMON_PARAMS_SPEC,
    field: fieldFp,
    a: BigInt('0xfffffffffffffffffffffffffffffffefffffffffffffffffffffffe'),
    b: BigInt('0xb4050a850c04b3abf54132565044b0b7d7bfd8ba270b39432355ffb4'),
    g: G,
    n: BigInt('0xffffffffffffffffffffffffffff16a2e0b8f03e13dd29455c5c2a3d'),
    h: 1
  }
  return eccCommonSpec;
}

async function testgetAsyKeySpec() {
  let commKeySpec = genEccCommonSpec(); // 使用参数属性，构造ECC公私钥公共密钥参数对象。
  let generatorBySpec = cryptoFramework.createAsyKeyGeneratorBySpec(commKeySpec); // 使用密钥参数对象创建生成器。
  let keyPair = await generatorBySpec.generateKeyPair();
  let pirKey = keyPair.priKey;
  let eccPrimeP = pirKey.getAsyKeySpec(cryptoFramework.AsyKeySpecItem.ECC_FP_P_BN);
  console.info('ecc item --- p: ' + eccPrimeP.toString(16));
}
```

## getEncodedDer

```TypeScript
getEncodedDer(format: string): DataBlob
```

支持根据指定的密钥格式（如规范、压缩状态等），获取符合ASN.1语法和DER编码的公钥数据。

> **说明：**
> 
> 本接口和[Key.getEncoded()](arkts-cryptoarchitecture-cryptoframework-key-i.md#getencoded)的区别是：
> 1. 本接口可以指定获取密钥数据的格式。
> 2. [Key.getEncoded()](arkts-cryptoarchitecture-cryptoframework-key-i.md#getencoded)不支持指定获取密钥数据的格式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 用于指定当前密钥格式。支持EC密钥，format取值支持"X509\|COMPRESSED"和"X509\|UNCOMPRESSED"。 从API版本26.0.0开始，支持RSA密钥，format取值支持"PKCS1"和"X509"。 从API版本26.0.0开始，支持ML-DSA和ML-KEM密钥，format取值支持"X509"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | DER编码的公钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGetEncodedDer() {
  let pkData = new Uint8Array([48, 90, 48, 20, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 9, 43, 36, 3, 3, 2, 8, 1, 1, 7, 3, 66, 0, 4, 143, 39, 57, 249, 145, 50, 63, 222, 35, 70, 178, 121, 202, 154, 21, 146, 129, 75, 76, 63, 8, 195, 157, 111, 40, 217, 215, 148, 120, 224, 205, 82, 83, 92, 185, 21, 211, 184, 5, 19, 114, 33, 86, 85, 228, 123, 242, 206, 200, 98, 178, 184, 130, 35, 232, 45, 5, 202, 189, 11, 46, 163, 156, 152]);
  let pubKeyBlob: cryptoFramework.DataBlob = { data: pkData };
  let generator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = await generator.convertKey(pubKeyBlob, null);
  let key = keyPair.pubKey;
  let returnBlob = key.getEncodedDer('X509|UNCOMPRESSED');
  console.info('returnBlob data: ' + returnBlob.data);
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGetEncodedDer() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
  // 使用密钥生成器随机生成非对称密钥对。
  let keyGenPromise = eccGenerator.generateKeyPair();
  keyGenPromise.then(keyPair => {
    let priKey = keyPair.priKey;
    let returnBlob = priKey.getEncodedDer('PKCS8');
    console.info('returnBlob data: ' + returnBlob.data);
  });
}
```

## getEncodedPem

```TypeScript
getEncodedPem(format: string): string
```

获取PEM编码的密钥数据。此API以同步方式返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 指定的获取密钥字符串的编码格式。支持RSA密钥，format取值支持"X509"或"PKCS1"。 自API版本26.0.0起，支持EC、ML-DSA和ML-KEM密钥，format取值支持"X509"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | PEM编码的公钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let publicPkcs1Str1024: string =
  '-----BEGIN RSA PUBLIC KEY-----\n'
    + 'MIGJAoGBALAg3eavbX433pOjGdWdpL7HIr1w1EAeIcaCtuMfDpECPdX6X5ZjrwiE\n'
    + 'h7cO51WXMT2gyN45DCQySr/8cLE2UiUVHo7qlrSatdLA9ETtgob3sJ4qTaBg5Lxg\n'
    + 'SHy2gC+bvEpuIuRe64yXGuM/aP+ZvmIj9QBIVI9mJD8jLEOvQBBpAgMBAAE=\n'
    + '-----END RSA PUBLIC KEY-----\n';

function TestPubKeyPkcs1ToX509BySync1024() {
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = rsaGenerator.convertPemKeySync(publicPkcs1Str1024, null);
  let pubPemKey = keyPair.pubKey;
  let pubString = pubPemKey.getEncodedPem('X509');
  console.info('[sync]TestPubKeyPkcs1ToX509BySync1024 pubString output = ' + pubString);
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let priKeyPkcs1Str1024: string =
  '-----BEGIN RSA PRIVATE KEY-----\n'
    + 'MIICXQIBAAKBgQCwIN3mr21+N96ToxnVnaS+xyK9cNRAHiHGgrbjHw6RAj3V+l+W\n'
    + 'Y68IhIe3DudVlzE9oMjeOQwkMkq//HCxNlIlFR6O6pa0mrXSwPRE7YKG97CeKk2g\n'
    + 'YOS8YEh8toAvm7xKbiLkXuuMlxrjP2j/mb5iI/UASFSPZiQ/IyxDr0AQaQIDAQAB\n'
    + 'AoGAEvBFzBNa+7J4PXnRQlYEK/tvsd0bBZX33ceacMubHl6WVZbphltLq+fMTBPP\n'
    + 'LjXmtpC+aJ7Lvmyl+wTi/TsxE9vxW5JnbuRT48rnZ/Xwq0eozDeEeIBRrpsr7Rvr\n'
    + '7ctrgzr4m4yMHq9aDgpxj8IR7oHkfwnmWr0wM3FuiVlj650CQQDineeNZ1hUTkj4\n'
    + 'D3O+iCi3mxEVEeJrpqrmSFolRMb+iozrIRKuJlgcOs+Gqi2fHfOTTL7LkpYe8SVg\n'
    + 'e3JxUdVLAkEAxvcZXk+byMFoetrnlcMR13VHUpoVeoV9qkv6CAWLlbMdgf7uKmgp\n'
    + 'a1Yp3QPDNQQqkPvrqtfR19JWZ4uy1qREmwJALTU3BjyBoH/liqb6fh4HkWk75Som\n'
    + 'MzeSjFIOubSYxhq5tgZpBZjcpvUMhV7Zrw54kwASZ+YcUJvmyvKViAm9NQJBAKF7\n'
    + 'DyXSKrem8Ws0m1ybM7HQx5As6l3EVhePDmDQT1eyRbKp+xaD74nkJpnwYdB3jyyY\n'
    + 'qc7A1tj5J5NmeEFolR0CQQCn76Xp8HCjGgLHw9vg7YyIL28y/XyfFyaZAzzK+Yia\n'
    + 'akNwQ6NeGtXSsuGCcyyfpacHp9xy8qXQNKSkw03/5vDO\n'
    + '-----END RSA PRIVATE KEY-----\n';

function TestPriKeyPkcs1ToPkcs8BySync1024() {
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = rsaGenerator.convertPemKeySync(null, priKeyPkcs1Str1024);
  let priPemKey = keyPair.priKey;
  let priString = priPemKey.getEncodedPem('PKCS8');
  console.info('[sync]TestPriKeyPkcs1ToPkcs8BySync1024 priString output = ' + priString);
}
```

## getKeyData

```TypeScript
getKeyData(itemType: AsyKeyDataItem): Promise<Uint8Array>
```

获取指定的密钥数据类型对应的公钥数据。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | 是 | 指定密钥数据项类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Uint8Array&gt; | Promise对象，返回指定密钥数据项类型的公钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = await eccGenerator.generateKeyPair();
  let returnBlob = await keyPair.pubKey.getKeyData(cryptoFramework.AsyKeyDataItem.EC_PUBLIC_X_Y);
  console.info('EC_PUBLIC_X_Y data: ' + returnBlob);
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = await eccGenerator.generateKeyPair();
  let returnBlob = await keyPair.priKey.getKeyData(cryptoFramework.AsyKeyDataItem.EC_PRIVATE_04_X_Y_K);
  console.info('EC_PRIVATE_04_X_Y_K data: ' + returnBlob);
}
```

## getKeyDataSync

```TypeScript
getKeyDataSync(itemType: AsyKeyDataItem): Uint8Array
```

获取指定的密钥数据类型对应的公钥数据。此API以同步方式返回结果。

**说明：** 建议优先使用异步API，getKeyData。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。 因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | 是 | 指定密钥数据项类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回指定密钥数据项类型的公钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = eccGenerator.generateKeyPairSync();
  let returnBlob = keyPair.pubKey.getKeyDataSync(cryptoFramework.AsyKeyDataItem.EC_PUBLIC_X_Y);
  console.info('EC_PUBLIC_X_Y data: ' + returnBlob);
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = eccGenerator.generateKeyPairSync();
  let returnBlob = keyPair.priKey.getKeyDataSync(cryptoFramework.AsyKeyDataItem.EC_PRIVATE_04_X_Y_K);
  console.info('EC_PRIVATE_04_X_Y_K data: ' + returnBlob);
}
```
