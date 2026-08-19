# createKeyAgreement

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createKeyAgreement

```TypeScript
function createKeyAgreement(algName: string): KeyAgreement
```

创建密钥协商实例。 <br>支持的规格详见[密钥协商规格](../../../security/CryptoArchitectureKit/crypto-key-agreement-overview.md)。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createKeyAgreement(algName: string): KeyAgreement--><!--Device-cryptoFramework-function createKeyAgreement(algName: string): KeyAgreement-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.KeyAgreement
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定密钥协商算法：目前仅支持ECDH，从API version 11开始，增加支持X25519和DH。<br>支持的规格详见 [密钥协商规格](../../../security/CryptoArchitectureKit/crypto-key-agreement-overview.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [KeyAgreement](arkts-cryptoarchitecture-cryptoframework-keyagreement-i.md) | 返回对应算法的KeyAgreement实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let keyAgreement = cryptoFramework.createKeyAgreement('ECC256');
```

