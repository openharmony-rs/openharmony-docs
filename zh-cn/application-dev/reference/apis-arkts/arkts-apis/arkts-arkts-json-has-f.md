# has

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## has

```TypeScript
function has(obj: object, property: string): boolean
```

检查ArkTS对象中是否包含某个键。此API可用于[JSON.parse](arkts-arkts-json-parse-f.md#parse)解析JSON字符串后的相关操作。仅支持最外层为字典格式（大括号而非中括号）的有效JSON字符串。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function has(obj: object, property: string): boolean--><!--Device-json-function has(obj: object, property: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ArkTS对象。 |
| property | string | 是 | 待检查的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果对象中包含该键返回true，否则返回false。 |

