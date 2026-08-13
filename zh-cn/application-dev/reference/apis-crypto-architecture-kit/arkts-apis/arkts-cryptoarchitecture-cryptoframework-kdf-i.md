# Kdf

密钥派生函数（KDF）接口，定义基于密钥派生参数派生密钥的方法。调用前，需通过 [createKdf](arkts-cryptoarchitecture-cryptoframework-createkdf-f.md#createKdf)方法创建一个Kdf实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface Kdf--><!--Device-cryptoFramework-interface Kdf-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## generateSecret

```TypeScript
generateSecret(params: KdfSpec, callback: AsyncCallback<DataBlob>): void
```

基于传入的密钥派生参数进行密钥派生。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Kdf-generateSecret(params: KdfSpec, callback: AsyncCallback<DataBlob>): void--><!--Device-Kdf-generateSecret(params: KdfSpec, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 是 | 设置密钥派生函数的参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;DataBlob&gt; | 是 | 回调函数。当密钥派生成功时，err为undefined，data为派生的密钥；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因： &lt;br&gt;1. 参数中的密钥长度无效； &lt;br&gt;2. 参数中的info长度无效； &lt;br&gt;3. 参数中的keySize无效。<br>**适用版本：** 22+ |

## 示例

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let spec: cryptoFramework.PBKDF2Spec = {
  algName: 'PBKDF2',
  password: '123456',
  salt: new Uint8Array(16),
  iterations: 10000,
  keySize: 32
};
let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
kdf.generateSecret(spec, (err, secret) => {
  if (err) {
    console.error(`key derivation failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info('key derivation output = ' + secret.data);
});
```

HKDF算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let spec: cryptoFramework.HKDFSpec = {
  algName: 'HKDF',
  key: '123456',
  salt: new Uint8Array(16),
  info: new Uint8Array(16),
  keySize: 32
};
let kdf = cryptoFramework.createKdf('HKDF|SHA256|EXTRACT_AND_EXPAND');
kdf.generateSecret(spec, (err, secret) => {
  if (err) {
    console.error(`key derivation failed, errCode: ${err.code}, errMsg: ${err.message}`);
    return;
  }
  console.info('key derivation output = ' + secret.data);
});
```

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@ohos.base';

function TestGenerateSecret() {
  let spec: cryptoFramework.PBKDF2Spec = {
    algName: 'PBKDF2',
    password: '123456',
    salt: new Uint8Array(16),
    iterations: 10000,
    keySize: 32
  };
  let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
  kdf.generateSecret(spec, (err, secret) => {
    if (err) {
      console.error("generateSecret error.");
      return;
    }
    if (secret != undefined) {
      console.info('generateSecret output is ' + secret.data);
    }
  });
}
```

HKDF算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function TestGenerateSecret() {
  let spec: cryptoFramework.HKDFSpec = {
    algName: 'HKDF',
    key: '123456',
    salt: new Uint8Array(16),
    info: new Uint8Array(16),
    keySize: 32
  };
  let kdf = cryptoFramework.createKdf('HKDF|SHA256|EXTRACT_AND_EXPAND');
  kdf.generateSecret(spec, (err, secret) => {
    if (err) {
      console.error("generateSecret error.");
      return;
    }
    if (secret != undefined) {
      console.info('generateSecret output is ' + secret.data);
    }
  });
}
```

## generateSecret

```TypeScript
generateSecret(params: KdfSpec): Promise<DataBlob>
```

基于传入的密钥派生参数进行密钥派生。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Kdf-generateSecret(params: KdfSpec): Promise<DataBlob>--><!--Device-Kdf-generateSecret(params: KdfSpec): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 是 | 设置密钥派生函数的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回派生的密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因： &lt;br&gt;1. 参数中的密钥长度无效； &lt;br&gt;2. 参数中的info长度无效； &lt;br&gt;3. 参数中的keySize无效。<br>**适用版本：** 22+ |

## 示例

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let spec: cryptoFramework.PBKDF2Spec = {
  algName: 'PBKDF2',
  password: '123456',
  salt: new Uint8Array(16),
  iterations: 10000,
  keySize: 32
};
let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
let kdfPromise = kdf.generateSecret(spec);
kdfPromise.then(secret => {
  console.info('key derivation output = ' + secret.data);
}).catch((error: BusinessError) => {
  console.error(`key derivation failed: errCode: ${error.code}, errMsg: ${error.message}`);
});
```

HKDF算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let spec: cryptoFramework.HKDFSpec = {
  algName: 'HKDF',
  key: '123456',
  salt: new Uint8Array(16),
  info: new Uint8Array(16),
  keySize: 32
};
let kdf = cryptoFramework.createKdf('HKDF|SHA256|EXTRACT_AND_EXPAND');
let kdfPromise = kdf.generateSecret(spec);
kdfPromise.then(secret => {
  console.info('key derivation output = ' + secret.data);
}).catch((error: BusinessError) => {
  console.error(`key derivation failed: errCode: ${error.code}, errMsg: ${error.message}`);
});
```

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@ohos.base';

async function TestGenerateSecret() {
  let spec: cryptoFramework.PBKDF2Spec = {
    algName: 'PBKDF2',
    password: '123456',
    salt: new Uint8Array(16),
    iterations: 10000,
    keySize: 32
  };
  try {
    let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
    let kdfPromise = await kdf.generateSecret(spec);
    console.info('generateSecret output = ' + kdfPromise.data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error("TestGenerateSecret failed, " + e.message);
  }
}
```

HKDF算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@ohos.base';

async function TestGenerateSecret() {
  let spec: cryptoFramework.HKDFSpec = {
    algName: 'HKDF',
    key: '123456',
    salt: new Uint8Array(16),
    info: new Uint8Array(16),
    keySize: 32
  };
  try {
    let kdf = cryptoFramework.createKdf('HKDF|SHA256|EXTRACT_AND_EXPAND');
    let kdfPromise = await kdf.generateSecret(spec);
    console.info('generateSecret output = ' + kdfPromise.data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error("TestGenerateSecret failed, " + e.message);
  }
}
```

## generateSecretSync

```TypeScript
generateSecretSync(params: KdfSpec): DataBlob
```

基于传入的密钥派生参数进行密钥派生，通过同步方式返回派生得到的密钥。 &lt;br&gt;&lt;br&gt;**说明：** &lt;br&gt;建议优先使用异步API，generateSecret。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。 因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-Kdf-generateSecretSync(params: KdfSpec): DataBlob--><!--Device-Kdf-generateSecretSync(params: KdfSpec): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 是 | 设置密钥派生函数的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 用于获取派生得到的密钥DataBlob数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因： &lt;br&gt;1. 参数中的密钥长度无效； &lt;br&gt;2. 参数中的info长度无效； &lt;br&gt;3. 参数中的keySize无效。<br>**适用版本：** 22+ |

## 示例

PBKDF2算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let spec: cryptoFramework.PBKDF2Spec = {
  algName: 'PBKDF2',
  password: '123456',
  salt: new Uint8Array(16),
  iterations: 10000,
  keySize: 32
};
let kdf = cryptoFramework.createKdf('PBKDF2|SHA256');
let secret = kdf.generateSecretSync(spec);
console.info('[Sync]key derivation output = ' + secret.data);
```

HKDF算法

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let spec: cryptoFramework.HKDFSpec = {
  algName: 'HKDF',
  key: '123456',
  salt: new Uint8Array(16),
  info: new Uint8Array(16),
  keySize: 32
};
let kdf = cryptoFramework.createKdf('HKDF|SHA256|EXTRACT_AND_EXPAND');
let secret = kdf.generateSecretSync(spec);
console.info('[Sync]key derivation output = ' + secret.data);
```

## algName

```TypeScript
readonly algName: string
```

密钥派生函数的算法名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Kdf-readonly algName: string--><!--Device-Kdf-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

