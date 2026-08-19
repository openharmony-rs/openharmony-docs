# has

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## has

```TypeScript
function has(obj: object, property: string): boolean
```

检查ArkTS对象是否包含某种属性，可用于[JSON.parse](arkts-arkts-json-parse-f.md)解析JSON字符串之后。 has接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串，传入非字典形式的对象时无法正确判断属性是否存在。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function has(obj: object, property: string): boolean--><!--Device-json-function has(obj: object, property: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | object | 是 | ArkTS对象，仅支持最外层为字典形式（即大括号而非中括号包围）的合法JSON串解析后的对象。 |
| property | string | 是 | 要检查的属性名称，用于指定需在ArkTS对象中查找是否存在的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回ArkTS对象是否包含指定属性的结果。true表示对象包含指定属性；false表示对象不包含指定属性。 |

