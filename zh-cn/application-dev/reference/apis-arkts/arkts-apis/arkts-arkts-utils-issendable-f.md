# isSendable

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## isSendable

```TypeScript
function isSendable(value: Object | null | undefined): boolean
```

检查ArkTS值是否为Sendable。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-utils-function isSendable(value: Object | null | undefined): boolean--><!--Device-utils-function isSendable(value: Object | null | undefined): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object \| null \| undefined | 是 | 要检查的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果值为Sendable则返回true，否则返回false。 |

