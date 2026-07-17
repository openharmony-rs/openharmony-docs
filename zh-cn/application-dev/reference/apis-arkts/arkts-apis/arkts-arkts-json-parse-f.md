# parse

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null
```

将JSON字符串解析为ArkTS对象或null。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null--><!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串。 |
| reviver | [Transformer](arkts-arkts-ason-transformer-t.md) | 否 | 转换函数，可用于修改解析后生成的值。默认值为undefined。 |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 否 | 解析选项，用于控制解析结果的类型。默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 返回与JSON文本对应的Object、数组、字符串、数字、布尔值或null值。 |

