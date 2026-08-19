# stringify

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## stringify

```TypeScript
function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string
```

该方法将一个ArkTS对象或数组转换为JSON字符串，支持线性容器的转换，不支持非线性容器（传入非线性容器时无法正确序列化）。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | ArkTS对象或数组，支持线性容器的转换，不支持非线性容器。 |
| replacer | (number \| string)[] \| null | 否 | 用于筛选序列化属性。当参数为string[]时，只有包含在该数组中的对象属性名才会被序列化； 当参数为number[]时，只有对应索引的数组元素才会被序列化；当参数为null或者未提供时，则对象所有的属性都会被序列化。默认值是undefined。 |
| space | string \| number | 否 | 指定缩进用的空格或字符串，用于美化输出。当参数是数字时表示缩进空格数，取值需为非负整数；当参数是字符串时表示缩进字符；无参数则无缩进。默认值是空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示对象或数组经序列化处理后生成的JSON格式文本字符串。 |


## stringify

```TypeScript
function stringify(value: Object, replacer?: Transformer, space?: string | number): string
```

该方法将一个ArkTS对象或数组转换为JSON字符串，支持线性容器的转换，不支持非线性容器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Object | 是 | ArkTS对象或数组，支持线性容器的转换，不支持非线性容器。 |
| replacer | Transformer | 否 | 在序列化过程中，被序列化的值的每个属性都会经过该函数的转换和处理。 当参数未提供时，则对象所有的属性都会被直接序列化，不经过转换处理。默认值是undefined。 |
| space | string \| number | 否 | 指定缩进用的空格或字符串，用于美化输出。当参数是数字时表示缩进空格数；当参数是字符串时表示缩进字符；无参数则无缩进。默认值是空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 表示对象或数组经序列化处理后生成的JSON格式文本字符串。 |

