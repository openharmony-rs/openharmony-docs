# PriKey

私钥，是[Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)的子类，在非对称解密、签名、密钥协商时需要将其作为输入使用。

私钥可以通过非对称密钥生成器[AsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md)、[AsyKeyGeneratorBySpec](arkts-cryptoarchitecture-cryptoframework-asykeygeneratorbyspec-i.md)来生成。

**继承/实现关系：** PriKey extends [Key](arkts-cryptoarchitecture-cryptoframework-key-i.md)

**起始版本：** 9

<!--Device-cryptoFramework-interface PriKey extends Key--><!--Device-cryptoFramework-interface PriKey extends Key-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="clearmem"></a>
## clearMem

```TypeScript
clearMem(): void
```

同步方法，清零系统底层内存中的密钥数据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-clearMem(): void--><!--Device-PriKey-clearMem(): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testClearMem() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
  // 使用密钥生成器随机生成非对称密钥对。
  let keyGenPromise = eccGenerator.generateKeyPair();
  keyGenPromise.then(keyPair => {
    let priKey = keyPair.priKey;
    let returnBlob = priKey.getEncodedDer('PKCS8');
    console.info('returnBlob data：' + returnBlob.data);
    priKey.clearMem(); // 对于非对称私钥，clearMem()释放内部密钥结构。执行clearMem后，不支持getEncoded()。
  });
}

```

<a id="getasykeyspec"></a>
## getAsyKeySpec

```TypeScript
getAsyKeySpec(itemType: AsyKeySpecItem): bigint | string | number
```

获取一个密钥参数。此API以同步方式返回结果。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getAsyKeySpec(itemType: AsyKeySpecItem): bigint | string | int--><!--Device-PriKey-getAsyKeySpec(itemType: AsyKeySpecItem): bigint | string | int-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeySpecItem](arkts-cryptoarchitecture-cryptoframework-asykeyspecitem-e.md) | 是 | 指定的密钥参数类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 获取的密钥参数内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

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
  let key = keyPair.priKey;
  let p = key.getAsyKeySpec(cryptoFramework.AsyKeySpecItem.ECC_FP_P_BN);
  console.info('ecc item --- p: ' + p.toString(16));
}

```

<a id="getencodedder"></a>
## getEncodedDer

```TypeScript
getEncodedDer(format: string): DataBlob
```

支持根据指定的密钥格式（如采用哪个规范），获取满足ASN.1语法、DER编码的私钥数据。

> **说明：**  
>  
> 本接口和[Key.getEncoded()](arkts-cryptoarchitecture-cryptoframework-key-i.md#getencoded-1)的区别是：  
> 1. 本接口可以指定获取密钥数据的格式。  
> 2. [Key.getEncoded()](arkts-cryptoarchitecture-cryptoframework-key-i.md#getencoded-1)不支持指定获取密钥数据的格式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getEncodedDer(format: string): DataBlob--><!--Device-PriKey-getEncodedDer(format: string): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 用于指定当前密钥格式。支持EC密钥，format取值支持"PKCS8"。<br>从API版本26.0.0开始，支持RSA密钥，format取值支持"PKCS1"和"PKCS8"。<br>从API版本26.0.0开始，支持ML-DSA和ML-KEM密钥，format取值支持"PKCS8"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 返回满足ASN.1语法和DER编码的指定密钥格式的ECC私钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGetEncodedDer() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
  // 使用密钥生成器随机生成非对称密钥对。
  let keyGenPromise = eccGenerator.generateKeyPair();
  keyGenPromise.then(keyPair => {
    let priKey = keyPair.priKey;
    let returnBlob = priKey.getEncodedDer('PKCS8');
    console.info('returnBlob data：' + returnBlob.data);
  });
}

```

<a id="getencodedpem"></a>
## getEncodedPem

```TypeScript
getEncodedPem(format: string): string
```

获取密钥数据。此API以同步方式返回结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getEncodedPem(format: string): string--><!--Device-PriKey-getEncodedPem(format: string): string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 指定的获取密钥字符串的编码格式。支持RSA密钥，format取值支持'PKCS8'或'PKCS1'。<br>自API版本26.0.0起，支持EC密钥，format取值支持'PKCS8'或'EC'。<br>自API版本26.0.0起，支持ML-DSA和ML-KEM密钥，format取值支持'PKCS8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用于获取指定密钥格式的具体内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

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

<a id="getencodedpem-1"></a>
## getEncodedPem

```TypeScript
getEncodedPem(format: string, config: KeyEncodingConfig): string
```

获取密钥数据。此API以同步方式返回结果。目前仅支持RSA密钥。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getEncodedPem(format: string, config: KeyEncodingConfig): string--><!--Device-PriKey-getEncodedPem(format: string, config: KeyEncodingConfig): string-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| format | string | 是 | 指定的获取密钥字符串的编码格式。对于RSA密钥，格式可以是'PKCS8'或'PKCS1'。 |
| config | [KeyEncodingConfig](arkts-cryptoarchitecture-cryptoframework-keyencodingconfig-i.md) | 是 | 指定编码的算法跟口令，对私钥进行编码操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 用于获取指定密钥格式的具体内容。如果填了config参数，则获取编码后的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

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

function TestPriKeyPkcs1Encoded() {
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = rsaGenerator.convertPemKeySync(null, priKeyPkcs1Str1024);
  let options: cryptoFramework.KeyEncodingConfig = {
    password: '123456',
    cipherName: 'AES-128-CBC'
  }
  let priPemKey = keyPair.priKey;
  let priString = priPemKey.getEncodedPem('PKCS1', options);
  console.info('[sync]TestPriKeyPkcs1Encoded priString output = ' + priString);
}

```

<a id="getkeydata"></a>
## getKeyData

```TypeScript
getKeyData(itemType: AsyKeyDataItem): Promise<Uint8Array>
```

指定密钥数据项类型，获取对应类型的私钥数据。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getKeyData(itemType: AsyKeyDataItem): Promise<Uint8Array>--><!--Device-PriKey-getKeyData(itemType: AsyKeyDataItem): Promise<Uint8Array>-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | 是 | 指定密钥数据项类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回指定密钥数据项类型的私钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = await eccGenerator.generateKeyPair();
  let returnBlob = await keyPair.priKey.getKeyData(cryptoFramework.AsyKeyDataItem.EC_PRIVATE_04_X_Y_K);
  console.info('EC_PRIVATE_04_X_Y_K data: ' + returnBlob);
}

```

<a id="getkeydatasync"></a>
## getKeyDataSync

```TypeScript
getKeyDataSync(itemType: AsyKeyDataItem): Uint8Array
```

根据指定的密钥数据类型获取私钥数据。此API以同步方式返回结果。

<br><br>**说明：**<br>建议优先使用异步API{@link getKeyData}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getKeyDataSync(itemType: AsyKeyDataItem): Uint8Array--><!--Device-PriKey-getKeyDataSync(itemType: AsyKeyDataItem): Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [AsyKeyDataItem](arkts-cryptoarchitecture-cryptoframework-asykeydataitem-e.md) | 是 | 指定密钥数据项类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 返回指定密钥数据项类型的私钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function eccGetKeyDataTest() {
  let eccGenerator = cryptoFramework.createAsyKeyGenerator('ECC_BrainPoolP256r1');
  let keyPair = eccGenerator.generateKeyPairSync();
  let returnBlob = keyPair.priKey.getKeyDataSync(cryptoFramework.AsyKeyDataItem.EC_PRIVATE_04_X_Y_K);
  console.info('EC_PRIVATE_04_X_Y_K data: ' + returnBlob);
}

```

<a id="getpubkey"></a>
## getPubKey

```TypeScript
getPubKey(): Promise<PubKey>
```

从私钥对象中获取公钥对象。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getPubKey(): Promise<PubKey>--><!--Device-PriKey-getPubKey(): Promise<PubKey>-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PubKey&gt; | Promise对象，返回公钥对象PubKey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function compareUint8Array(a: Uint8Array, b: Uint8Array): boolean {
  let buf1 = buffer.from(a);
  let buf2 = buffer.from(b);
  if (buf1.compare(buf2, 0, b.length, 0, a.length) == 0) {
    return true;
  } else {
    return false;
  }
}

async function generateAsyKey() {
  let skData =
    new Uint8Array([48, 130, 2, 119, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 97, 48,
      130, 2, 93, 2, 1, 0, 2, 129, 129, 0, 199, 32, 218, 8, 4, 63, 103, 229, 64, 128, 83, 31, 23, 156, 30, 168, 101, 22,
      80, 100, 197, 243, 217, 60, 127, 110, 127, 242, 8, 251, 87, 127, 235, 38, 226, 149, 149, 108, 54, 202, 53, 1, 21,
      91, 118, 246, 97, 93, 147, 117, 162, 71, 215, 70, 9, 175, 205, 241, 230, 187, 64, 170, 154, 67, 67, 254, 71, 1,
      114, 10, 91, 195, 34, 199, 85, 172, 255, 87, 95, 159, 43, 117, 73, 73, 199, 97, 198, 117, 217, 7, 188, 196, 30,
      248, 9, 181, 150, 243, 41, 145, 91, 8, 226, 161, 251, 12, 120, 28, 36, 146, 3, 196, 48, 243, 136, 201, 207, 131,
      171, 22, 15, 7, 12, 172, 135, 196, 30, 93, 2, 3, 1, 0, 1, 2, 129, 128, 109, 100, 83, 194, 225, 170, 127, 134, 6,
      184, 56, 113, 181, 67, 179, 231, 232, 152, 168, 147, 163, 215, 193, 56, 165, 252, 235, 86, 232, 174, 67, 52, 103,
      215, 149, 212, 125, 32, 212, 188, 162, 255, 180, 94, 233, 236, 146, 50, 153, 6, 159, 158, 253, 217, 97, 10, 238,
      133, 124, 174, 211, 232, 165, 19, 100, 186, 218, 62, 46, 124, 30, 19, 251, 3, 206, 105, 255, 236, 224, 178, 148,
      103, 44, 132, 71, 83, 28, 221, 27, 189, 72, 44, 59, 253, 139, 232, 234, 14, 112, 121, 43, 142, 193, 179, 140, 200,
      97, 234, 110, 63, 205, 24, 88, 116, 86, 184, 8, 19, 254, 204, 77, 84, 66, 238, 240, 69, 72, 21, 2, 65, 0, 233,
      103, 239, 11, 215, 10, 103, 66, 46, 155, 193, 79, 37, 64, 90, 12, 167, 189, 129, 8, 131, 94, 195, 8, 210, 236, 87,
      158, 140, 2, 82, 105, 80, 253, 13, 26, 140, 202, 194, 117, 59, 57, 197, 108, 50, 20, 46, 89, 248, 132, 120, 30,
      149, 180, 135, 134, 196, 156, 160, 123, 38, 253, 15, 7, 2, 65, 0, 218, 103, 122, 117, 154, 149, 213, 110, 24, 149,
      175, 208, 136, 249, 88, 91, 89, 180, 30, 243, 69, 130, 97, 252, 177, 216, 55, 46, 67, 15, 124, 56, 113, 57, 242,
      233, 185, 193, 254, 218, 76, 165, 184, 16, 109, 190, 93, 195, 227, 37, 58, 110, 243, 142, 152, 252, 226, 91, 59,
      145, 218, 35, 106, 123, 2, 65, 0, 210, 131, 88, 58, 32, 144, 148, 131, 63, 144, 97, 112, 165, 211, 125, 164, 110,
      97, 224, 16, 50, 148, 116, 105, 239, 251, 20, 39, 190, 117, 149, 168, 193, 80, 10, 210, 136, 107, 147, 169, 178,
      106, 47, 162, 159, 36, 78, 141, 253, 52, 85, 54, 152, 165, 131, 154, 204, 151, 203, 178, 103, 126, 212, 95, 2, 65,
      0, 193, 254, 80, 3, 205, 255, 112, 200, 142, 5, 199, 88, 207, 145, 203, 45, 185, 12, 8, 193, 196, 231, 254, 233,
      89, 126, 215, 228, 187, 164, 49, 142, 96, 228, 60, 35, 230, 223, 173, 227, 113, 89, 113, 153, 6, 33, 165, 95, 173,
      143, 15, 204, 37, 130, 111, 217, 143, 165, 193, 207, 215, 150, 197, 169, 2, 64, 7, 37, 152, 14, 232, 168, 102,
      169, 167, 97, 161, 33, 86, 178, 77, 140, 12, 114, 78, 129, 47, 103, 87, 217, 177, 80, 156, 91, 240, 149, 254, 90,
      69, 232, 10, 56, 232, 63, 59, 148, 254, 101, 63, 146, 66, 96, 25, 31, 37, 154, 77, 145, 201, 213, 122, 245, 90,
      251, 219, 42, 131, 248, 148, 151
  ])
  let expectPkdata =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 199, 32, 218, 8, 4, 63, 103, 229, 64, 128, 83, 31, 23, 156, 30, 168, 101, 22, 80, 100, 197, 243,
      217, 60, 127, 110, 127, 242, 8, 251, 87, 127, 235, 38, 226, 149, 149, 108, 54, 202, 53, 1, 21, 91, 118, 246, 97,
      93, 147, 117, 162, 71, 215, 70, 9, 175, 205, 241, 230, 187, 64, 170, 154, 67, 67, 254, 71, 1, 114, 10, 91, 195,
      34, 199, 85, 172, 255, 87, 95, 159, 43, 117, 73, 73, 199, 97, 198, 117, 217, 7, 188, 196, 30, 248, 9, 181, 150,
      243, 41, 145, 91, 8, 226, 161, 251, 12, 120, 28, 36, 146, 3, 196, 48, 243, 136, 201, 207, 131, 171, 22, 15, 7, 12,
      172, 135, 196, 30, 93, 2, 3, 1, 0, 1
  ])
  let skDataBlob: cryptoFramework.DataBlob = { data: skData };
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  try {
    let keyPair = rsaGenerator.convertKeySync(null, skDataBlob);
    let priKey = keyPair.priKey;
    let pubkey = await priKey.getPubKey();
    let pkBlob = pubkey.getEncoded();
    console.info('pk1 bin data ' + pkBlob.data);
    let ret: boolean = compareUint8Array(pkBlob.data, expectPkdata);
    console.info('result = ' + ret);
  } catch (e) {
    console.error(`get pubkey from prikey failed, ${e.code}, ${e.message}`);
  }
}

```

<a id="getpubkeysync"></a>
## getPubKeySync

```TypeScript
getPubKeySync(): PubKey
```

以同步方式，从私钥对象中获取公钥对象。

<br><br>**说明：**<br>建议优先使用异步API{@link getPubKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PriKey-getPubKeySync(): PubKey--><!--Device-PriKey-getPubKeySync(): PubKey-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 公钥对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function compareUint8Array(a: Uint8Array, b: Uint8Array): boolean {
  let buf1 = buffer.from(a);
  let buf2 = buffer.from(b);
  if (buf1.compare(buf2, 0, b.length, 0, a.length) == 0) {
    return true;
  } else {
    return false;
  }
}

function generateAsyKey() {
  let skData =
    new Uint8Array([48, 130, 2, 119, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 97, 48,
      130, 2, 93, 2, 1, 0, 2, 129, 129, 0, 199, 32, 218, 8, 4, 63, 103, 229, 64, 128, 83, 31, 23, 156, 30, 168, 101, 22,
      80, 100, 197, 243, 217, 60, 127, 110, 127, 242, 8, 251, 87, 127, 235, 38, 226, 149, 149, 108, 54, 202, 53, 1, 21,
      91, 118, 246, 97, 93, 147, 117, 162, 71, 215, 70, 9, 175, 205, 241, 230, 187, 64, 170, 154, 67, 67, 254, 71, 1,
      114, 10, 91, 195, 34, 199, 85, 172, 255, 87, 95, 159, 43, 117, 73, 73, 199, 97, 198, 117, 217, 7, 188, 196, 30,
      248, 9, 181, 150, 243, 41, 145, 91, 8, 226, 161, 251, 12, 120, 28, 36, 146, 3, 196, 48, 243, 136, 201, 207, 131,
      171, 22, 15, 7, 12, 172, 135, 196, 30, 93, 2, 3, 1, 0, 1, 2, 129, 128, 109, 100, 83, 194, 225, 170, 127, 134, 6,
      184, 56, 113, 181, 67, 179, 231, 232, 152, 168, 147, 163, 215, 193, 56, 165, 252, 235, 86, 232, 174, 67, 52, 103,
      215, 149, 212, 125, 32, 212, 188, 162, 255, 180, 94, 233, 236, 146, 50, 153, 6, 159, 158, 253, 217, 97, 10, 238,
      133, 124, 174, 211, 232, 165, 19, 100, 186, 218, 62, 46, 124, 30, 19, 251, 3, 206, 105, 255, 236, 224, 178, 148,
      103, 44, 132, 71, 83, 28, 221, 27, 189, 72, 44, 59, 253, 139, 232, 234, 14, 112, 121, 43, 142, 193, 179, 140, 200,
      97, 234, 110, 63, 205, 24, 88, 116, 86, 184, 8, 19, 254, 204, 77, 84, 66, 238, 240, 69, 72, 21, 2, 65, 0, 233,
      103, 239, 11, 215, 10, 103, 66, 46, 155, 193, 79, 37, 64, 90, 12, 167, 189, 129, 8, 131, 94, 195, 8, 210, 236, 87,
      158, 140, 2, 82, 105, 80, 253, 13, 26, 140, 202, 194, 117, 59, 57, 197, 108, 50, 20, 46, 89, 248, 132, 120, 30,
      149, 180, 135, 134, 196, 156, 160, 123, 38, 253, 15, 7, 2, 65, 0, 218, 103, 122, 117, 154, 149, 213, 110, 24, 149,
      175, 208, 136, 249, 88, 91, 89, 180, 30, 243, 69, 130, 97, 252, 177, 216, 55, 46, 67, 15, 124, 56, 113, 57, 242,
      233, 185, 193, 254, 218, 76, 165, 184, 16, 109, 190, 93, 195, 227, 37, 58, 110, 243, 142, 152, 252, 226, 91, 59,
      145, 218, 35, 106, 123, 2, 65, 0, 210, 131, 88, 58, 32, 144, 148, 131, 63, 144, 97, 112, 165, 211, 125, 164, 110,
      97, 224, 16, 50, 148, 116, 105, 239, 251, 20, 39, 190, 117, 149, 168, 193, 80, 10, 210, 136, 107, 147, 169, 178,
      106, 47, 162, 159, 36, 78, 141, 253, 52, 85, 54, 152, 165, 131, 154, 204, 151, 203, 178, 103, 126, 212, 95, 2, 65,
      0, 193, 254, 80, 3, 205, 255, 112, 200, 142, 5, 199, 88, 207, 145, 203, 45, 185, 12, 8, 193, 196, 231, 254, 233,
      89, 126, 215, 228, 187, 164, 49, 142, 96, 228, 60, 35, 230, 223, 173, 227, 113, 89, 113, 153, 6, 33, 165, 95, 173,
      143, 15, 204, 37, 130, 111, 217, 143, 165, 193, 207, 215, 150, 197, 169, 2, 64, 7, 37, 152, 14, 232, 168, 102,
      169, 167, 97, 161, 33, 86, 178, 77, 140, 12, 114, 78, 129, 47, 103, 87, 217, 177, 80, 156, 91, 240, 149, 254, 90,
      69, 232, 10, 56, 232, 63, 59, 148, 254, 101, 63, 146, 66, 96, 25, 31, 37, 154, 77, 145, 201, 213, 122, 245, 90,
      251, 219, 42, 131, 248, 148, 151
    ])
  let expectPkdata =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 199, 32, 218, 8, 4, 63, 103, 229, 64, 128, 83, 31, 23, 156, 30, 168, 101, 22, 80, 100, 197, 243,
      217, 60, 127, 110, 127, 242, 8, 251, 87, 127, 235, 38, 226, 149, 149, 108, 54, 202, 53, 1, 21, 91, 118, 246, 97,
      93, 147, 117, 162, 71, 215, 70, 9, 175, 205, 241, 230, 187, 64, 170, 154, 67, 67, 254, 71, 1, 114, 10, 91, 195,
      34, 199, 85, 172, 255, 87, 95, 159, 43, 117, 73, 73, 199, 97, 198, 117, 217, 7, 188, 196, 30, 248, 9, 181, 150,
      243, 41, 145, 91, 8, 226, 161, 251, 12, 120, 28, 36, 146, 3, 196, 48, 243, 136, 201, 207, 131, 171, 22, 15, 7, 12,
      172, 135, 196, 30, 93, 2, 3, 1, 0, 1
    ])
  let skDataBlob: cryptoFramework.DataBlob = { data: skData };
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  try {
    let keyPair = rsaGenerator.convertKeySync(null, skDataBlob);
    let priKey = keyPair.priKey;
    let pubkey = priKey.getPubKeySync();
    let pkBlob = pubkey.getEncoded();
    console.info('pk1 bin data' + pkBlob.data);
    let ret: boolean = compareUint8Array(pkBlob.data, expectPkdata);
    console.info('result = ' + ret);
  } catch (e) {
    console.error(`get pubkey from prikey failed, ${e.code}, ${e.message}`);
  }
}

```

