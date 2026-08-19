# createMd

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createMd

```TypeScript
function createMd(algName: string): Md
```

创建消息摘要实例。 <br>支持的规格详见 [MD消息摘要算法规格](../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#支持的算法与规格)。

**起始版本：** 23

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createMd(algName: string): Md--><!--Device-cryptoFramework-function createMd(algName: string): Md-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.MessageDigest
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algName | string | 是 | 指定摘要算法，支持算法请参考 [MD消息摘要算法规格](../../../security/CryptoArchitectureKit/crypto-generate-message-digest-overview.md#支持的算法与规格)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Md](arkts-cryptoarchitecture-cryptoframework-md-i.md) | 返回对应算法的Md实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let md = cryptoFramework.createMd('SHA256');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```

