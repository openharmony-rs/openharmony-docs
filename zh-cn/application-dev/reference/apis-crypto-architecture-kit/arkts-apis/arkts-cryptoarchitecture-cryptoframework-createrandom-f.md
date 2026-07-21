# createRandom

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="createrandom"></a>
## createRandom

```TypeScript
function createRandom(): Random
```

生成Random实例，用于进行随机数的计算与设置种子。

**起始版本：** 9

**模型约束：** 
- API版本12+：此接口可在Stage模型和FA模型下使用。
- API版本9-11：此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createRandom(): Random--><!--Device-cryptoFramework-function createRandom(): Random-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Rand
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Random](arkts-cryptoarchitecture-cryptoframework-random-i.md) | 返回由输入算法指定生成的[Random](arkts-cryptoarchitecture-cryptoframework-random-i.md)对象。<br>支持的规格详见框架概述[随机数算法规格](../../../security/CryptoArchitectureKit/crypto-generate-random-number.md#支持的算法与规格)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

**示例：**

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

