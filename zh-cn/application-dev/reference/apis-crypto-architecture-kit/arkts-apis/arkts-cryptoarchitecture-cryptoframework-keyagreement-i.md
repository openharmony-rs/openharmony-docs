# KeyAgreement

密钥协商接口，定义基于非对称密钥对生成共享密钥的方法。调用前，需通过 [createKeyAgreement(algName: string): KeyAgreement](arkts-cryptoarchitecture-cryptoframework-createkeyagreement-f.md#createKeyAgreement)方法创建一个 KeyAgreement实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface KeyAgreement--><!--Device-cryptoFramework-interface KeyAgreement-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.KeyAgreement
- API版本9-11：SystemCapability.Security.CryptoFramework

## generateSecret

```TypeScript
generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback<DataBlob>): void
```

基于传入的私钥与公钥进行密钥协商。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyAgreement-generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback<DataBlob>): void--><!--Device-KeyAgreement-generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback<DataBlob>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.KeyAgreement
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 设置密钥协商的私钥输入。 |
| pubKey | [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 是 | 设置密钥协商的公钥输入。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;DataBlob&gt; | 是 | 回调函数。当密钥协商成功时，err为undefined，data为协商的共享密钥；否则为 错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |

## generateSecret

```TypeScript
generateSecret(priKey: PriKey, pubKey: PubKey): Promise<DataBlob>
```

基于传入的私钥与公钥进行密钥协商。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyAgreement-generateSecret(priKey: PriKey, pubKey: PubKey): Promise<DataBlob>--><!--Device-KeyAgreement-generateSecret(priKey: PriKey, pubKey: PubKey): Promise<DataBlob>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.KeyAgreement
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 设置密钥协商的私钥输入。 |
| pubKey | [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 是 | 设置密钥协商的公钥输入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob&gt; | Promise对象，返回密钥协商的共享密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |

## generateSecretSync

```TypeScript
generateSecretSync(priKey: PriKey, pubKey: PubKey): DataBlob
```

基于传入的私钥与公钥进行密钥协商，通过同步返回共享密钥。 &lt;br&gt;&lt;br&gt;**说明：** &lt;br&gt;建议优先使用异步API，generateSecret。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。 因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-KeyAgreement-generateSecretSync(priKey: PriKey, pubKey: PubKey): DataBlob--><!--Device-KeyAgreement-generateSecretSync(priKey: PriKey, pubKey: PubKey): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.KeyAgreement

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 设置密钥协商的私钥输入。 |
| pubKey | [PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md) | 是 | 设置密钥协商的公钥输入。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 共享密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateSecret() {
  let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
  let globalKeyPair = await eccGen.generateKeyPair();
  let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
  keyAgreement.generateSecret(globalKeyPair.priKey, globalKeyPair.pubKey, (err, secret) => {
    if (err) {
      console.error(`keyAgreement failed, errCode: ${err.code}, errMsg: ${err.message}`);
      return;
    }
    console.info('keyAgreement output = ' + secret.data);
  });
}
```

ArkTS-Sta示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateSecret() {
  let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
  let globalKeyPair = await eccGen.generateKeyPair();
  let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
  keyAgreement.generateSecret(globalKeyPair.priKey, globalKeyPair.pubKey, (err, secret) => {
    if (err) {
      console.error("keyAgreement error.");
    }
    if (secret != undefined) {
      console.info('keyAgreement output is ' + secret.data);
    }
  });
}
```

ArkTS-Dyn示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function testGenerateSecret() {
  let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
  let globalKeyPair = await eccGen.generateKeyPair();
  let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
  let keyAgreementPromise = keyAgreement.generateSecret(globalKeyPair.priKey, globalKeyPair.pubKey);
  keyAgreementPromise.then(secret => {
    console.info('keyAgreement output = ' + secret.data);
  }).catch((error: BusinessError) => {
    console.error(`keyAgreement failed: errCode: ${error.code}, errMsg: ${error.message}`);
  });
}
```

ArkTS-Sta示例：

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@ohos.base';

async function testGenerateSecret() {
  try {
    let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
    let globalKeyPair = await eccGen.generateKeyPair();
    let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
    let keyAgreementPromise = await keyAgreement.generateSecret(globalKeyPair.priKey, globalKeyPair.pubKey);
    console.info('keyAgreement output is ' + keyAgreementPromise.data);
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`keyAgreement error, ${e.code}, ${e.message}`);
  }
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateSecretSync() {
  let eccGen = cryptoFramework.createAsyKeyGenerator('ECC256');
  let globalKeyPair = await eccGen.generateKeyPair();
  let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
  let secret = keyAgreement.generateSecretSync(globalKeyPair.priKey, globalKeyPair.pubKey);
  console.info('[Sync]keyAgreement output = ' + secret.data);
}
```

## algName

```TypeScript
readonly algName: string
```

密钥协商的算法名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyAgreement-readonly algName: string--><!--Device-KeyAgreement-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.KeyAgreement
- API版本9-11：SystemCapability.Security.CryptoFramework

