# createRandom

## createRandom

```TypeScript
function createRandom(): Random
```

生成Random实例，用于进行随机数的计算与设置种子。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Rand

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Random | 返回由输入算法指定生成的[Random](arkts-cryptoarchitecture-cryptoframework-random-i.md#Random)对象。<br/><br/>支持的规格详见框架概述[随机数算法规格](../../../../security/CryptoArchitectureKit/crypto-generate-random-number.md#支持的算法与规格)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../../errorcode-universal.md#17620001-内存操作失败) | 内存操作失败。 |

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

