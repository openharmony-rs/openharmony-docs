# Sign

签名接口，定义基于私钥对数据进行签名的方法。调用前，需通过[createSign(algName: string): Sign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md)方法创建一个Sign实例。按序调用Sign实例中的init、update（可选）、sign方法完成签名操作。签名操作的示例代码详见[签名验签开发指导](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md)。

<br>Sign实例不支持重复初始化，当业务方需要使用新密钥签名时，需要重新创建新Sign实例并调用init初始化。

<br>业务方使用时，调用createSign接口确定签名的模式，调用init接口设置密钥。

<br>当待签名数据长度较短时，可在初始化后直接调用sign接口传入数据进行签名，无需调用update。

<br>当待签名数据较长时，可通过update接口分段传入切分后的原文数据，最后调用sign接口对整体原文数据进行签名。

<br>当使用update分段传入原文时，sign接口API 10之前只支持传入DataBlob， API 10之后增加支持null。业务方可在循环中调用update接口，循环结束后调用sign进行签名。

<br>使用DSA算法签名时，如果摘要算法设置为NoHash，则不支持update操作，调用update接口将返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## getSignSpec

```TypeScript
getSignSpec(itemType: SignSpecItem): string | number
```

获取签名参数。当前仅支持RSA算法。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | 是 | 用于指定需要获取的签名参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string &#124; number | 返回获取的签名参数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGetSignSpec() {
  let signer = cryptoFramework.createSign('RSA|PSS|SHA256|MGF1_SHA256');
  let setN = 32;
  signer.setSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
  signer.getSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
}
```

## init

```TypeScript
init(priKey: PriKey, callback: AsyncCallback<void>): void
```

使用私钥初始化Sign实例。使用callback异步回调。init、update、sign为三段式接口，需要成组使用。其中init和sign必选，update可选。

<br>Sign实例不支持重复初始化。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 用于Sign的初始化。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当签名初始化成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Incorrect key type.<br>**适用版本：** 26.0.0+ |

## init

```TypeScript
init(priKey: PriKey): Promise<void>
```

使用私钥初始化Sign实例。使用Promise异步回调。init、update、sign为三段式接口，需要成组使用。其中init和sign必选，update可选。

<br>Sign实例不支持重复初始化。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 用于Sign的初始化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Incorrect key type.<br>**适用版本：** 26.0.0+ |

## initSync

```TypeScript
initSync(priKey: PriKey): void
```

使用私钥初始化Sign实例，通过同步方式获取结果。initSync、updateSync、signSync为三段式接口，需要成组使用。其中initSync和signSync必选，updateSync可选。

<br>Sign实例不支持重复调用initSync。

<br><br>**说明：** <br>建议优先使用异步API，init。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| priKey | [PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md) | 是 | 用于Sign的初始化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Incorrect key type.<br>**适用版本：** 26.0.0+ |

## setSignSpec

```TypeScript
setSignSpec(itemType: SignSpecItem, itemValue: number): void
```

设置签名参数。常用签名参数可通过 [createSign](arkts-cryptoarchitecture-cryptoframework-createsign-f.md) 指定，其他参数则通过本接口设置。

<br>当前仅支持RSA算法、SM2算法，从API version11开始，支持SM2算法设置签名参数。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | 是 | 用于指定需要设置的签名参数。 |
| itemValue | number | 是 | 用于指定签名参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testSetSignSpec() {
  let signer = cryptoFramework.createSign('RSA|PSS|SHA256|MGF1_SHA256');
  let setN = 20;
  signer.setSignSpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
}
```

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testSetSignSpec() {
  let signer = cryptoFramework.createSign('ML-DSA');
  signer.setSignSpec(cryptoFramework.SignSpecItem.ML_DSA_DETERMINISTIC_BOOL, true);
}
```

## setSignSpec

```TypeScript
setSignSpec(itemType: SignSpecItem, itemValue: number | Uint8Array): void
```

为Sign实例设置指定参数。

<br>当前仅支持RSA算法中的PSS_SALT_LEN参数和SM2算法中的USER_ID参数。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | 是 | 用于指定需要设置的签名参数类型。 |
| itemValue | number &#124; Uint8Array | 是 | 指定签名参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters.<br>**适用版本：** 26.0.0+ |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | Invalid function call.<br>**适用版本：** 26.0.0+ |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

参见 [setSignSpec](#setsignspec)

## setSignSpec

```TypeScript
setSignSpec(itemType: SignSpecItem, itemValue: number | Uint8Array | boolean): void
```

为Sign实例设置指定参数。

<br>当前仅支持RSA算法中的PSS_SALT_LEN参数、SM2算法中的USER_ID参数以及ML-DSA算法中的ML_DSA_DETERMINISTIC、ML_DSA_MU和ML_DSA_CONTEXT参数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | [SignSpecItem](arkts-cryptoarchitecture-cryptoframework-signspecitem-e.md) | 是 | 用于指定需要设置的签名参数类型。 |
| itemValue | number &#124; Uint8Array &#124; boolean | 是 | 指定签名参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | Invalid function call. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |

**示例**

参见 [setSignSpec](#setsignspec)

## sign

```TypeScript
sign(data: DataBlob, callback: AsyncCallback<DataBlob>): void
```

对数据进行签名，包括更新的数据。使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 待签名的数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | 是 | 回调函数。当签名成功时，err为undefined，data为获取到的签名结果DataBlob；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

## sign

```TypeScript
sign(data: DataBlob | null, callback: AsyncCallback<DataBlob>): void
```

对数据进行签名。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | 是 | 传入的消息。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | 是 | 回调函数。当签名成功时，err为undefined，data为获取到的签名结果DataBlob；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

## sign

```TypeScript
sign(data: DataBlob): Promise<DataBlob>
```

对数据进行签名，包括更新的数据。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 待签名的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise对象，返回签名结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

## sign

```TypeScript
sign(data: DataBlob | null): Promise<DataBlob>
```

对数据进行签名。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise对象，返回签名结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

## signSync

```TypeScript
signSync(data: DataBlob | null): DataBlob
```

对数据进行签名，通过同步方式返回签名结果。

<br><br>**说明：** <br>建议优先使用异步API，[sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md)。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) &#124; null | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 返回签名结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed.<br>**适用版本：** 26.0.0+ |

**示例**

```TypeScript
此外，更多签名验签的完整示例可参考[签名验签开发指导](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md)。
```

## update

```TypeScript
update(data: DataBlob, callback: AsyncCallback<void>): void
```

追加待签名数据，使用callback异步回调完成更新。

<br>必须在对[Sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md)实例使用[init](#init)或[initSync](#initsync)初始化后，才能使用本函数。

> **说明：** 
> 
> 根据数据量，可以不调用update（即[init](#init)完成后直接调用
> [sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md)）或多次调用update。
> 
> 算法库目前没有对update（单次或累计）的数据量设置大小限制，建议对于大数据量的签名操作，采用多次update的方式传入数据，避免一次性申请
> 过大内存。
> 
> 签名使用多次update操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md)，
> 其余算法操作类似。

> OnlySign模式下，不支持update操作，需要直接使用sign传入数据。

> 当使用DSA算法进行签名，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当签名更新成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | Invalid function call.<br>**适用版本：** 26.0.0+ |

## update

```TypeScript
update(data: DataBlob): Promise<void>
```

追加待签名数据，使用Promise异步回调方式完成更新。

<br>在使用本函数前，必须先使用[init](#init)对[Sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md)实例进行初始化。

> **说明：** 
> 
> 根据数据量，可以不调用update（即[init](#init)
> 完成后直接调用[sign](#sign-1)）
> 或多次调用update。
> 
> 算法库不对单次或累计的update数据量设置大小限制。建议在处理大数据量的签名操作时，采用多次update方式传入数据，以避免一次性申请过大内
> 存。
> 签名使用多次update操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md)，
> 其余算法操作类似。
> 
> OnlySign模式下，不支持update操作，需要直接使用sign传入数据。
> 
> 当使用DSA算法进行签名，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | Invalid function call.<br>**适用版本：** 26.0.0+ |

## updateSync

```TypeScript
updateSync(data: DataBlob): void
```

追加待签名数据，通过同步方式完成更新。

<br>必须在对[Sign](arkts-cryptoarchitecture-cryptoframework-sign-i.md)实例使用[initSync()](#initsync)初始化后，才能使用本函数。

> **说明：** 
> 
> 根据数据量，可以不调用updateSync（即[initSync](#initsync)完成后直接调用
> [signSync](#signsync)）或多次调用updateSync。
> 
> 算法库目前没有对updateSync（单次或累计）的数据量设置大小限制，建议对于大数据量的签名操作，采用多次updateSync的方式传入数据，避免
> 一次性申请过大内存。
> 
> 签名使用多次updateSync操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify.md)，
> 其余算法操作类似。
> 
> OnlySign模式下，不支持updateSync操作，需要直接使用signSync传入数据。
> 
> 当使用DSA算法进行签名，并设置了摘要算法为NoHash时，则不支持updateSync操作，updateSync接口会返回错误码ERR_CRYPTO_OPERATION。

<br><br>**说明：** <br>建议优先使用异步API，update。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 是 | 传入的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | Invalid function call.<br>**适用版本：** 26.0.0+ |

## algName

```TypeScript
readonly algName: string
```

签名指定的算法名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework
