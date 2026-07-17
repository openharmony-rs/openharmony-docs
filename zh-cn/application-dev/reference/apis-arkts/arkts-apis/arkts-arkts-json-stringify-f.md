# stringify

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## stringify

```TypeScript
function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string
```

将ArkTS对象或数组转换为JSON字符串。对于容器，支持线性容器，但不支持非线性容器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | ArkTS对象或数组。对于容器，支持线性容器，但不支持非线性容器。 |
| replacer | (number \| string)[] \| null | 否 | 如果传入数组，则只序列化数组中包含的键到最终的JSON字符串中。如果传入null，则序列化对象的所有键。默认值为undefined。 |
| space | string \| number | 否 | 为提高可读性，添加到输出JSON字符串中的空白或字符串。如果是数字，表示缩进的空格数；如果是字符串，表示缩进字符。如果不提供参数，则没有缩进。默认值为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回JSON文本。 |


## stringify

```TypeScript
function stringify(value: Object, replacer?: Transformer, space?: string | number): string
```

将ArkTS对象或数组转换为JSON字符串。对于容器，支持线性容器，但不支持非线性容器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | ArkTS对象或数组。对于容器，支持线性容器，但不支持非线性容器。 |
| replacer | [Transformer](arkts-arkts-ason-transformer-t.md) | 否 | 序列化期间，序列化值的每个键都由此函数转换和处理。默认值为undefined。 |
| space | string \| number | 否 | 为提高可读性，添加到输出JSON字符串中的缩进、空白或换行字符。如果是数字，表示作为缩进的空格字符数。如果是字符串，该字符串将插入到输出JSON字符串之前。如果传入null，不使用任何空白字符。默认值为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回JSON文本。 |

