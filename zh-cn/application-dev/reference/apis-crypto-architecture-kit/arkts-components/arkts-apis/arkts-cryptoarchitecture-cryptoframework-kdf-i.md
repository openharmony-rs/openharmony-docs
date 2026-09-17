# Kdf

密钥派生函数（KDF）接口，定义基于密钥派生参数派生密钥的方法。调用前，需通过[createKdf](arkts-cryptoarchitecture-cryptoframework-createkdf-f.md)方法创建一个Kdf实例。

**起始版本：** 11

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## generateSecret

```TypeScript
generateSecret(params: KdfSpec, callback: AsyncCallback<DataBlob>): void
```

基于传入的密钥派生参数进行密钥派生。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 是 | 设置密钥派生函数的参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | 是 | 回调函数。当密钥派生成功时，err为undefined，data为派生的密钥；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Invalid key length in the params; <br>2. Invalid info length in the params; <br>3. Invalid keySize in the params.<br>**适用版本：** 22+ |

**示例**

```TypeScript
PBKDF2算法
```

```TypeScript
HKDF算法
```

## generateSecret

```TypeScript
generateSecret(params: KdfSpec): Promise<DataBlob>
```

基于传入的密钥派生参数进行密钥派生。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

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
| Promise&lt;[DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md)&gt; | Promise对象，返回派生的密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Invalid key length in the params; <br>2. Invalid info length in the params; <br>3. Invalid keySize in the params.<br>**适用版本：** 22+ |

**示例**

参见 [generateSecret](#generatesecret)

## generateSecretSync

```TypeScript
generateSecretSync(params: KdfSpec): DataBlob
```

基于传入的密钥派生参数进行密钥派生，通过同步方式返回派生得到的密钥。

<br><br>**说明：** <br>建议优先使用异步API，generateSecret。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md) | 是 | 设置密钥派生函数的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](arkts-cryptoarchitecture-cryptoframework-datablob-i.md) | 用于获取派生得到的密钥DataBlob数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | Failed to obtain the native object or convert parameters. |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | Crypto operation error. |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | Parameter check failed. Possible causes:<br>1. Invalid key length in the params; <br>2. Invalid info length in the params; <br>3. Invalid keySize in the params.<br>**适用版本：** 22+ |

**示例**

```TypeScript
PBKDF2算法
```

```TypeScript
HKDF算法
```

## algName

```TypeScript
readonly algName: string
```

密钥派生函数的算法名称。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Kdf
- API版本11：SystemCapability.Security.CryptoFramework
