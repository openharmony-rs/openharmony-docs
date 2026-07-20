# parse

## 导入模块

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

<a id="parse"></a>
## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null
```

将JavaScript对象表示法（JSON）字符串转换为ArkTS值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ASON-function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null--><!--Device-ASON-function parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 有效的JSON字符串。 |
| reviver | [Transformer](arkts-arkts-ason-transformer-t.md) | 否 | 转换结果的函数。 |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | 否 | 解析的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ISendable](arkts-arkts-ason-isendable-t.md) | 返回ArkTS值。 |

