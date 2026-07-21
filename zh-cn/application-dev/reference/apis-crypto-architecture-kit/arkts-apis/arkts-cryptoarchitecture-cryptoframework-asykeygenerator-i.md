# AsyKeyGenerator

非对称密钥生成器。在使用该类的方法前，需要先使用[createAsyKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createasykeygenerator-f.md#createasykeygenerator-1)方法构建一个AsyKeyGenerator实例。

**起始版本：** 9

<!--Device-cryptoFramework-interface AsyKeyGenerator--><!--Device-cryptoFramework-interface AsyKeyGenerator-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="convertkey"></a>
## convertKey

```TypeScript
convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback<KeyPair>): void
```

将非对称密钥数据转换为密钥对对象。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback<KeyPair>): void--><!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback<KeyPair>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 公钥材料。 |
| priKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 私钥材料。 |
| callback | AsyncCallback&lt;KeyPair&gt; | 是 | 回调函数。当生成非对称密钥成功时，err为undefined，data为获取到的KeyPair；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

<a id="convertkey-1"></a>
## convertKey

```TypeScript
convertKey(pubKey: DataBlob | null, priKey: DataBlob | null, callback: AsyncCallback<KeyPair>): void
```

获取指定数据生成非对称密钥。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob | null, priKey: DataBlob | null, callback: AsyncCallback<KeyPair>): void--><!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob | null, priKey: DataBlob | null, callback: AsyncCallback<KeyPair>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| priKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定的私钥材料。如果私钥不需要转换，请传入null。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| callback | AsyncCallback&lt;KeyPair&gt; | 是 | 回调函数。当生成非对称密钥成功时，err为undefined，data为获取到的KeyPair；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let pubKeyArray =
  new Uint8Array([48, 89, 48, 19, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7, 3, 66, 0, 4,
    83, 96, 142, 9, 86, 214, 126, 106, 247, 233, 92, 125, 4, 128, 138, 105, 246, 162, 215, 71, 81, 58, 202, 121, 26,
    105, 211, 55, 130, 45, 236, 143, 55, 16, 248, 75, 167, 160, 167, 106, 2, 152, 243, 44, 68, 66, 0, 167, 99, 92, 235,
    215, 159, 239, 28, 106, 124, 171, 34, 145, 124, 174, 57, 92]);
let priKeyArray =
  new Uint8Array([48, 49, 2, 1, 1, 4, 32, 115, 56, 137, 35, 207, 0, 60, 191, 90, 61, 136, 105, 210, 16, 27, 4, 171, 57,
    10, 61, 123, 40, 189, 28, 34, 207, 236, 22, 45, 223, 10, 189, 160, 10, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7]);
let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyArray }; // 公钥二进制数据。
let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyArray }; // 私钥二进制数据。
let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
asyKeyGenerator.convertKey(pubKeyBlob, priKeyBlob, (err, keyPair) => {
  if (err) {
    console.error(`convertKey failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info('convertKey result: success.');
});

```

<a id="convertkey-2"></a>
## convertKey

```TypeScript
convertKey(pubKey: DataBlob, priKey: DataBlob): Promise<KeyPair>
```

将非对称密钥数据转换为密钥对对象。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob, priKey: DataBlob): Promise<KeyPair>--><!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob, priKey: DataBlob): Promise<KeyPair>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 公钥材料。 |
| priKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 私钥材料。 |

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
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

<a id="convertkey-3"></a>
## convertKey

```TypeScript
convertKey(pubKey: DataBlob | null, priKey: DataBlob | null): Promise<KeyPair>
```

获取指定数据生成非对称密钥。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob | null, priKey: DataBlob | null): Promise<KeyPair>--><!--Device-AsyKeyGenerator-convertKey(pubKey: DataBlob | null, priKey: DataBlob | null): Promise<KeyPair>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| priKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定的私钥材料。如果私钥不需要转换，请传入null。API 10之前只支持DataBlob， API 10之后增加支持null。 |

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
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pubKeyArray =
  new Uint8Array([48, 89, 48, 19, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7, 3, 66, 0, 4,
    83, 96, 142, 9, 86, 214, 126, 106, 247, 233, 92, 125, 4, 128, 138, 105, 246, 162, 215, 71, 81, 58, 202, 121, 26,
    105, 211, 55, 130, 45, 236, 143, 55, 16, 248, 75, 167, 160, 167, 106, 2, 152, 243, 44, 68, 66, 0, 167, 99, 92, 235,
    215, 159, 239, 28, 106, 124, 171, 34, 145, 124, 174, 57, 92]);
let priKeyArray =
  new Uint8Array([48, 49, 2, 1, 1, 4, 32, 115, 56, 137, 35, 207, 0, 60, 191, 90, 61, 136, 105, 210, 16, 27, 4, 171, 57,
    10, 61, 123, 40, 189, 28, 34, 207, 236, 22, 45, 223, 10, 189, 160, 10, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7]);
let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyArray }; // 公钥二进制数据。
let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyArray }; // 私钥二进制数据。
let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
let keyGenPromise = asyKeyGenerator.convertKey(pubKeyBlob, priKeyBlob);
keyGenPromise.then(keyPair => {
  console.info('convertKey result: success.');
}).catch((error: BusinessError) => {
  console.error(`convertKey failed, errCode: ${error.code}, errMsg: ${error.message}`);
});

```

<a id="convertkeysync"></a>
## convertKeySync

```TypeScript
convertKeySync(pubKey: DataBlob | null, priKey: DataBlob | null): KeyPair
```

同步获取指定数据生成非对称密钥。

<br><br>**说明：**<br>建议优先使用异步API{@link convertKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertKeySync(pubKey: DataBlob | null, priKey: DataBlob | null): KeyPair--><!--Device-AsyKeyGenerator-convertKeySync(pubKey: DataBlob | null, priKey: DataBlob | null): KeyPair-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定公钥材料。如果公钥无需转换，请传入null。API 10前仅支持DataBlob，API 10起支持传入null。 |
| priKey | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) \| null | 是 | 指定私钥材料。如果私钥无需转换，请传入null。API 10前仅支持DataBlob，API 10起支持传入null。 |

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
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let pubKeyArray =
  new Uint8Array([48, 89, 48, 19, 6, 7, 42, 134, 72, 206, 61, 2, 1, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7, 3, 66, 0, 4,
    83, 96, 142, 9, 86, 214, 126, 106, 247, 233, 92, 125, 4, 128, 138, 105, 246, 162, 215, 71, 81, 58, 202, 121, 26,
    105, 211, 55, 130, 45, 236, 143, 55, 16, 248, 75, 167, 160, 167, 106, 2, 152, 243, 44, 68, 66, 0, 167, 99, 92, 235,
    215, 159, 239, 28, 106, 124, 171, 34, 145, 124, 174, 57, 92]);
let priKeyArray =
  new Uint8Array([48, 49, 2, 1, 1, 4, 32, 115, 56, 137, 35, 207, 0, 60, 191, 90, 61, 136, 105, 210, 16, 27, 4, 171, 57,
    10, 61, 123, 40, 189, 28, 34, 207, 236, 22, 45, 223, 10, 189, 160, 10, 6, 8, 42, 134, 72, 206, 61, 3, 1, 7]);
let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyArray }; // 公钥二进制数据。
let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyArray }; // 私钥二进制数据。
let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
try {
  let keyPairData = asyKeyGenerator.convertKeySync(pubKeyBlob, priKeyBlob);
  if (keyPairData != null) {
    console.info('[Sync]: key pair result: success.');
  } else {
    console.error('[Sync]: convert key pair result: fail.');
  }
} catch (e) {
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}

```

<a id="convertpemkey"></a>
## convertPemKey

```TypeScript
convertPemKey(pubKey: string | null, priKey: string | null): Promise<KeyPair>
```

获取指定数据生成非对称密钥。使用Promise异步回调。

> **说明：**  
>  
> 1. 使用convertPemKey()将外部字符串转换为Crypto框架定义的非对称密钥对象时，公钥需满足ASN.1语法、X.509规范和PEM编码格式，私钥需  
> 满足ASN.1语法、PKCS#8规范和PEM编码格式。  
> 2. 在convertPemKey()中，可以只传入pubKey或priKey中的一个，也可以两个都传入。如果只传入其中一个，返回的KeyPair实例中只包含从传  
> 入数据转换而来的密钥。  
> 3. 使用convertPemKey将外部字符串转换为Crypto框架定义的非对称密钥对象时，系统不会校验生成的密钥对象规格是否与为非对称密钥生成器指  
> 定的密钥规格相同。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertPemKey(pubKey: string | null, priKey: string | null): Promise<KeyPair>--><!--Device-AsyKeyGenerator-convertPemKey(pubKey: string | null, priKey: string | null): Promise<KeyPair>-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | string \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。 |
| priKey | string \| null | 是 | 指定的私钥材料。如果私钥不需要转换，请传入null。<br>**说明：**公钥和私钥材料不能同时为null或空字符串。 |

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
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
let publicPkcs1Str1024: string =
  '-----BEGIN RSA PUBLIC KEY-----\n'
    + 'MIGJAoGBALAg3eavbX433pOjGdWdpL7HIr1w1EAeIcaCtuMfDpECPdX6X5ZjrwiE\n'
    + 'h7cO51WXMT2gyN45DCQySr/8cLE2UiUVHo7qlrSatdLA9ETtgob3sJ4qTaBg5Lxg\n'
    + 'SHy2gC+bvEpuIuRe64yXGuM/aP+ZvmIj9QBIVI9mJD8jLEOvQBBpAgMBAAE=\n'
    + '-----END RSA PUBLIC KEY-----\n';

async function TestConvertPemKeyByPromise() {
  let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  asyKeyGenerator.convertPemKey(publicPkcs1Str1024, priKeyPkcs1Str1024)
    .then(keyPair => {
      console.info('convertPemKey result: success.');
    }).catch((error: BusinessError) => {
    console.error(`convertPemKey failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}

```

<a id="convertpemkey-1"></a>
## convertPemKey

```TypeScript
convertPemKey(pubKey: string | null, priKey: string | null, password: string): Promise<KeyPair>
```

获取指定数据生成非对称密钥。支持加密的私钥，同步传入私钥口令解密私钥。使用Promise异步回调。

> **说明：**  
>  
> 1. 使用convertPemKey()将外部字符串转换为Crypto框架定义的非对称密钥对象时，公钥需满足ASN.1语法、X.509规范和PEM编码格式，私钥需  
> 满足ASN.1语法、PKCS#8规范和PEM编码格式。  
> 2. 在convertPemKey()中，可以只传入pubKey或priKey中的一个，也可以两个都传入。如果只传入其中一个，返回的KeyPair实例中只包含从传  
> 入数据转换而来的密钥。  
> 3. 使用convertPemKey将外部字符串转换为Crypto框架定义的非对称密钥对象时，系统不会校验生成的密钥对象规格是否与为非对称密钥生成器指  
> 定的密钥规格相同。  
> 4. 如果传入了password参数，可用于解密加密的私钥。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertPemKey(pubKey: string | null, priKey: string | null, password: string): Promise<KeyPair>--><!--Device-AsyKeyGenerator-convertPemKey(pubKey: string | null, priKey: string | null, password: string): Promise<KeyPair>-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | string \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。 |
| priKey | string \| null | 是 | 指定的私钥材料。如果私钥不需要转换，请传入null。<br>**说明：**公钥和私钥材料不能同时为null或空字符串。 |
| password | string | 是 | 指定口令，用于解密私钥。 |

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

let priKeyPkcs1EncodingStr: string =
  '-----BEGIN RSA PRIVATE KEY-----\n'
    + 'Proc-Type: 4,ENCRYPTED\n'
    + 'DEK-Info: AES-128-CBC,815A066131BF05CF87CE610A59CC69AE\n\n'
    + '7Jd0vmOmYGFZ2yRY8fqRl3+6rQlFtNcMILvcb5KWHDSrxA0ULmJE7CW0DSRikHoA\n'
    + 't0KgafhYXeQXh0dRy9lvVRAFSLHCLJVjchx90V7ZSivBFEq7+iTozVp4AlbgYsJP\n'
    + 'vx/1sfZD2WAcyMJ7IDmJyft7xnpVSXsyWGTT4f3eaHJIh1dqjwrso7ucAW0FK6rp\n'
    + '/TONyOoXNfXtRbVtxNyCWBxt4HCSclDZFvS9y8fz9ZwmCUV7jei/YdzyQI2wnE13\n'
    + 'W8cKlpzRFL6BWi8XPrUtAw5MWeHBAPUgPWMfcmiaeyi5BJFhQCrHLi+Gj4EEJvp7\n'
    + 'mP5cbnQAx6+paV5z9m71SKrI/WSc4ixsYYdVmlL/qwAK9YliFfoPl030YJWW6rFf\n'
    + 'T7J9BUlHGUJ0RB2lURNNLakM+UZRkeE9TByzCzgTxuQtyv5Lwsh2mAk3ia5x0kUO\n'
    + 'LHg3Eoabhdh+YZA5hHaxnpF7VjspB78E0F9Btq+A41rSJ6zDOdToHey4MJ2nxdey\n'
    + 'Z3bi81TZ6Fp4IuROrvZ2B/Xl3uNKR7n+AHRKnaAO87ywzyltvjwSh2y3xhJueiRs\n'
    + 'BiYkyL3/fnocD3pexTdN6h3JgQGgO5GV8zw/NrxA85mw8o9im0HreuFObmNj36T9\n'
    + 'k5N+R/QIXW83cIQOLaWK1ThYcluytf0tDRiMoKqULiaA6HvDMigExLxuhCtnoF8I\n'
    + 'iOLN1cPdEVQjzwDHLqXP2DbWW1z9iRepLZlEm1hLRLEmOrTGKezYupVv306SSa6J\n'
    + 'OA55lAeXMbyjFaYCr54HWrpt4NwNBX1efMUURc+1LcHpzFrBTTLbfjIyq6as49pH\n'
    + '-----END RSA PRIVATE KEY-----\n'

async function TestConvertPemKeyByPromise() {
  let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  asyKeyGenerator.convertPemKey(null, priKeyPkcs1EncodingStr, '123456')
    .then(keyPair => {
      console.info('convertPemKey result: success.');
    }).catch((error: BusinessError) => {
    console.error(`convertPemKey failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}

```

<a id="convertpemkeysync"></a>
## convertPemKeySync

```TypeScript
convertPemKeySync(pubKey: string | null, priKey: string | null): KeyPair
```

同步获取指定数据，生成非对称密钥。

> **说明：**  
> convertPemKeySync接口与convertPemKey接口注意事项相同，见  
> [convertPemKey](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md#convertpemkey-1)  
> 接口说明。

<br><br>**说明：**<br>建议优先使用异步API{@link convertPemKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertPemKeySync(pubKey: string | null, priKey: string | null): KeyPair--><!--Device-AsyKeyGenerator-convertPemKeySync(pubKey: string | null, priKey: string | null): KeyPair-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | string \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。 |
| priKey | string \| null | 是 | 指定私钥材料。私钥无需转换时，请传入null。<br>**说明：**公钥和私钥材料不能同时为null或空字符串。 |

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
let publicPkcs1Str1024: string =
  '-----BEGIN RSA PUBLIC KEY-----\n'
    + 'MIGJAoGBALAg3eavbX433pOjGdWdpL7HIr1w1EAeIcaCtuMfDpECPdX6X5ZjrwiE\n'
    + 'h7cO51WXMT2gyN45DCQySr/8cLE2UiUVHo7qlrSatdLA9ETtgob3sJ4qTaBg5Lxg\n'
    + 'SHy2gC+bvEpuIuRe64yXGuM/aP+ZvmIj9QBIVI9mJD8jLEOvQBBpAgMBAAE=\n'
    + '-----END RSA PUBLIC KEY-----\n';

function TestConvertPemKeyBySync() {
  let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  try {
    let keyPairData = asyKeyGenerator.convertPemKeySync(publicPkcs1Str1024, priKeyPkcs1Str1024);
    if (keyPairData != null) {
      console.info('[Sync]: convert pem key pair result: success.');
    } else {
      console.error('[Sync]: convert pem key pair result: fail.');
    }
  } catch (e) {
    console.error(`Sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

<a id="convertpemkeysync-1"></a>
## convertPemKeySync

```TypeScript
convertPemKeySync(pubKey: string | null, priKey: string | null, password: string): KeyPair
```

获取指定数据生成非对称密钥。支持加密的私钥，同步传入私钥口令解密私钥。使用同步方法。

> **说明：**  
> convertPemKeySync接口与convertPemKey接口注意事项相同，见  
> [convertPemKey](arkts-cryptoarchitecture-cryptoframework-asykeygenerator-i.md#convertpemkey-1)  
> 接口说明。

<br><br>**说明：**<br>建议优先使用异步API{@link convertPemKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-convertPemKeySync(pubKey: string | null, priKey: string | null, password: string): KeyPair--><!--Device-AsyKeyGenerator-convertPemKeySync(pubKey: string | null, priKey: string | null, password: string): KeyPair-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.AsymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | string \| null | 是 | 指定的公钥材料。如果公钥不需要转换，请传入null。 |
| priKey | string \| null | 是 | 指定私钥材料。若无需转换，请传入 null。注意：公钥与私钥材料不可同时为 null。 |
| password | string | 是 | 指定口令，用于解密私钥。 |

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

let priKeyPkcs1EncodingStr: string =
  '-----BEGIN RSA PRIVATE KEY-----\n'
    + 'Proc-Type: 4,ENCRYPTED\n'
    + 'DEK-Info: AES-128-CBC,815A066131BF05CF87CE610A59CC69AE\n\n'
    + '7Jd0vmOmYGFZ2yRY8fqRl3+6rQlFtNcMILvcb5KWHDSrxA0ULmJE7CW0DSRikHoA\n'
    + 't0KgafhYXeQXh0dRy9lvVRAFSLHCLJVjchx90V7ZSivBFEq7+iTozVp4AlbgYsJP\n'
    + 'vx/1sfZD2WAcyMJ7IDmJyft7xnpVSXsyWGTT4f3eaHJIh1dqjwrso7ucAW0FK6rp\n'
    + '/TONyOoXNfXtRbVtxNyCWBxt4HCSclDZFvS9y8fz9ZwmCUV7jei/YdzyQI2wnE13\n'
    + 'W8cKlpzRFL6BWi8XPrUtAw5MWeHBAPUgPWMfcmiaeyi5BJFhQCrHLi+Gj4EEJvp7\n'
    + 'mP5cbnQAx6+paV5z9m71SKrI/WSc4ixsYYdVmlL/qwAK9YliFfoPl030YJWW6rFf\n'
    + 'T7J9BUlHGUJ0RB2lURNNLakM+UZRkeE9TByzCzgTxuQtyv5Lwsh2mAk3ia5x0kUO\n'
    + 'LHg3Eoabhdh+YZA5hHaxnpF7VjspB78E0F9Btq+A41rSJ6zDOdToHey4MJ2nxdey\n'
    + 'Z3bi81TZ6Fp4IuROrvZ2B/Xl3uNKR7n+AHRKnaAO87ywzyltvjwSh2y3xhJueiRs\n'
    + 'BiYkyL3/fnocD3pexTdN6h3JgQGgO5GV8zw/NrxA85mw8o9im0HreuFObmNj36T9\n'
    + 'k5N+R/QIXW83cIQOLaWK1ThYcluytf0tDRiMoKqULiaA6HvDMigExLxuhCtnoF8I\n'
    + 'iOLN1cPdEVQjzwDHLqXP2DbWW1z9iRepLZlEm1hLRLEmOrTGKezYupVv306SSa6J\n'
    + 'OA55lAeXMbyjFaYCr54HWrpt4NwNBX1efMUURc+1LcHpzFrBTTLbfjIyq6as49pH\n'
    + '-----END RSA PRIVATE KEY-----\n'

function TestConvertPemKeyBySync() {
  let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  try {
    let keyPairData = asyKeyGenerator.convertPemKeySync(null, priKeyPkcs1EncodingStr, '123456');
    if (keyPairData != null) {
      console.info('[Sync]: convert pem key pair result: success.');
    } else {
      console.error('[Sync]: convert pem key pair result: fail.');
    }
  } catch (e) {
    console.error(`Sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

<a id="generatekeypair"></a>
## generateKeyPair

```TypeScript
generateKeyPair(callback: AsyncCallback<KeyPair>): void
```

获取非对称密钥生成器随机生成的密钥。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-generateKeyPair(callback: AsyncCallback<KeyPair>): void--><!--Device-AsyKeyGenerator-generateKeyPair(callback: AsyncCallback<KeyPair>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

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

let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
asyKeyGenerator.generateKeyPair((err, keyPair) => {
  if (err) {
    console.error(`generateKeyPair failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info('generateKeyPair result: success.');
})

```

<a id="generatekeypair-1"></a>
## generateKeyPair

```TypeScript
generateKeyPair(): Promise<KeyPair>
```

获取非对称密钥生成器随机生成的密钥。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-generateKeyPair(): Promise<KeyPair>--><!--Device-AsyKeyGenerator-generateKeyPair(): Promise<KeyPair>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

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

let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
let keyGenPromise = asyKeyGenerator.generateKeyPair();
keyGenPromise.then(keyPair => {
  console.info('generateKeyPair result: success.');
}).catch((error: BusinessError) => {
  console.error(`generateKeyPair failed, ${error.code}, ${error.message}`);
});

```

<a id="generatekeypairsync"></a>
## generateKeyPairSync

```TypeScript
generateKeyPairSync(): KeyPair
```

同步获取非对称密钥生成器随机生成的密钥。

<br><br>**说明：**<br>建议优先使用异步API{@link generateKeyPair}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-generateKeyPairSync(): KeyPair--><!--Device-AsyKeyGenerator-generateKeyPairSync(): KeyPair-End-->

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

let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ECC256');
try {
  let keyPairData = asyKeyGenerator.generateKeyPairSync();
  if (keyPairData != null) {
    console.info('[Sync]: key pair result: success.');
  } else {
    console.error('[Sync]: get key pair result: fail.');
  }
} catch (e) {
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}

```

## algName

```TypeScript
readonly algName: string
```

非对称密钥生成器指定的算法名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AsyKeyGenerator-readonly algName: string--><!--Device-AsyKeyGenerator-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.AsymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

