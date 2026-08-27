# createRandom

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createRandom

```TypeScript
function createRandom(): Random
```

创建随机数实例。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Random](arkts-cryptoarchitecture-cryptoframework-random-i.md) | 返回Random实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let rand = cryptoFramework.createRandom();
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```
