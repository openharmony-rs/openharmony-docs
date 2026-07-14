# Kem

提供KEM密钥封装和解封装操作的API。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## decapsulate

```TypeScript
decapsulate(priKey: PriKey, wrappedKey: Uint8Array): Promise<Uint8Array>
```

密钥解封装操作。使用接收方的私钥，由接收方执行，从密文中解封装出共享密钥。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | PriKey | 是 | 接收方的私钥。 |
| wrappedKey | Uint8Array | 是 | KEM封装的密钥。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise对象，返回共享密钥。 |

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
import { BusinessError } from '@kit.BasicServicesKit';

async function kemDecapsulate() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = await asyKeyGenerator.generateKeyPair();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = await kem.encapsulate(keyPair.pubKey, null);
    let sharedSecret = await kem.decapsulate(keyPair.priKey, encapResult.wrappedKey);
    console.info('decapsulate success');
    console.info('sharedSecret length: ' + sharedSecret.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`decapsulate failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

## decapsulateSync

```TypeScript
decapsulateSync(priKey: PriKey, wrappedKey: Uint8Array): Uint8Array
```

密钥解封装操作。使用接收方的私钥，由接收方执行，从密文中解封装出共享密钥。使用同步回调。

<br><br>**说明：**
<br>建议优先使用异步API{@link decapsulate}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | PriKey | 是 | 接收方的私钥。 |
| wrappedKey | Uint8Array | 是 | KEM封装的密钥。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 共享密钥。 |

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
import { BusinessError } from '@kit.BasicServicesKit';

function kemDecapsulateSync() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = asyKeyGenerator.generateKeyPairSync();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = kem.encapsulateSync(keyPair.pubKey, null);
    let sharedSecret = kem.decapsulateSync(keyPair.priKey, encapResult.wrappedKey);
    console.info('decapsulateSync success');
    console.info('sharedSecret length: ' + sharedSecret.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`decapsulateSync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

## encapsulate

```TypeScript
encapsulate(pubKey: PubKey, ikme: Uint8Array | null): Promise<KemEncapResult>
```

密钥封装操作。使用接收方的公钥，由发送方执行，生成并封装一个共享密钥。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | PubKey | 是 | 接收方的公钥。 |
| ikme | Uint8Array \| null | 是 | 随机数种子，用于替代算法内部的随机数。对于ML-KEM算法，随机数种子是32字节。建议传null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KemEncapResult&gt; | Promise对象，返回KEM封装结果。 |

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
import { BusinessError } from '@kit.BasicServicesKit';

async function kemEncapsulate() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = await asyKeyGenerator.generateKeyPair();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = await kem.encapsulate(keyPair.pubKey, null);
    console.info('encapsulate success');
    console.info('sharedSecret length: ' + encapResult.sharedSecret.length);
    console.info('wrappedKey length: ' + encapResult.wrappedKey.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`encapsulate failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

## encapsulateSync

```TypeScript
encapsulateSync(pubKey: PubKey, ikme: Uint8Array | null): KemEncapResult
```

密钥封装操作。使用接收方的公钥，由发送方执行，生成并封装一个共享密钥。使用同步回调。

<br><br>**说明：**
<br>建议优先使用异步API{@link encapsulate}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | PubKey | 是 | 接收方的公钥。 |
| ikme | Uint8Array \| null | 是 | 随机数种子，用于替代算法内部的随机数。对于ML-KEM算法，随机数种子是32字节。建议传null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| KemEncapResult | KEM封装结果。 |

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
import { BusinessError } from '@kit.BasicServicesKit';

function kemEncapsulateSync() {
  try {
    let asyKeyGenerator = cryptoFramework.createAsyKeyGenerator('ML-KEM-768');
    let keyPair = asyKeyGenerator.generateKeyPairSync();
    let kem = cryptoFramework.createKem(cryptoFramework.KemAlgNameId.ML_KEM_768);
    let encapResult = kem.encapsulateSync(keyPair.pubKey, null);
    console.info('encapsulateSync success');
    console.info('sharedSecret length: ' + encapResult.sharedSecret.length);
    console.info('wrappedKey length: ' + encapResult.wrappedKey.length);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`encapsulateSync failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

