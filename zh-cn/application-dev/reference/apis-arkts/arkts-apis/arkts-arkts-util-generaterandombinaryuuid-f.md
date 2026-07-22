# generateRandomBinaryUUID

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## generateRandomBinaryUUID

```TypeScript
function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array
```

使用安全随机数生成器生成 RFC 4122 版本 4 的随机通用唯一识别码（UUID）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array--><!--Device-util-function generateRandomBinaryUUID(entropyCache?: boolean): Uint8Array-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entropyCache | boolean | 否 | 是否使用缓存的 uuid。值为 **true** 表示使用缓存的 uuid，值为 **false** 表示相反的情况。默认值为 **true**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 表示所生成 uuid 的 Uint8Array 值。 |

**示例：**

```TypeScript
let uuid = util.generateRandomBinaryUUID(true);
console.info(JSON.stringify(uuid));
// 输出随机生成的UUID

```

