# MeasureOptions

被计算文本属性。

**起始版本：** 9

<!--Device-unnamed-export interface MeasureOptions--><!--Device-unnamed-export interface MeasureOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { MeasureOptions } from '@kit.ArkUI';
```

## baselineOffset

```TypeScript
baselineOffset?: number | string
```

设置被计算文本基线的偏移量。

默认值：0

**类型：** number \| string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-baselineOffset?: number | string--><!--Device-MeasureOptions-baselineOffset?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constraintWidth

```TypeScript
constraintWidth?: number | string | Resource
```

设置被计算文本布局宽度。

**说明：**

默认单位为vp，不支持设置百分比字符串。若不设置，则文本SizeOptions宽度为单行布局所占最大宽度值，若设置则为设置值。

**类型：** number \| string \| Resource

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-constraintWidth?: number | string | Resource--><!--Device-MeasureOptions-constraintWidth?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

设置被计算文本字体列表。默认字体'HarmonyOS Sans'，且当前只支持这种字体。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-fontFamily?: string | Resource--><!--Device-MeasureOptions-fontFamily?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置被计算文本字体大小，fontSize为number类型时，使用vp单位。

默认值：16

**说明：**

不支持设置百分比字符串。

从API version 12开始，fontSize为number类型时，使用fp单位。

**类型：** number \| string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-fontSize?: number | string | Resource--><!--Device-MeasureOptions-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: number | FontStyle
```

设置被计算文本字体样式。

默认值：FontStyle.Normal

number类型取值范围为[0,1]，取值间隔为1，依次对应FontStyle中的枚举值。

**类型：** number \| FontStyle

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-fontStyle?: number | FontStyle--><!--Device-MeasureOptions-fontStyle?: number | FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | string | FontWeight
```

设置被计算文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Normal

**类型：** number \| string \| FontWeight

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-fontWeight?: number | string | FontWeight--><!--Device-MeasureOptions-fontWeight?: number | string | FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

设置被计算文本字符间距。

默认值：0

**类型：** number \| string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-letterSpacing?: number | string--><!--Device-MeasureOptions-letterSpacing?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

设置被计算文本行高。

**类型：** number \| string \| Resource

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-lineHeight?: number | string | Resource--><!--Device-MeasureOptions-lineHeight?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

设置被计算文本最大行数。

取值范围：[0, INT32_MAX]

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-maxLines?: number--><!--Device-MeasureOptions-maxLines?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: number | TextOverflow
```

设置被计算文本超长时的截断方式。

默认值：1

number类型取值范围为[0,3]，取值间隔为1，依次对应TextOverflow中的枚举值。

**类型：** number \| TextOverflow

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-overflow?: number | TextOverflow--><!--Device-MeasureOptions-overflow?: number | TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: number | TextAlign
```

设置被计算文本水平方向的对齐方式。

默认值：TextAlign.Start

number类型取值范围为[0,3]，取值间隔为1，依次对应TextAlign中的枚举值。

**类型：** number \| TextAlign

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-textAlign?: number | TextAlign--><!--Device-MeasureOptions-textAlign?: number | TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textCase

```TypeScript
textCase?: number | TextCase
```

设置被计算文本大小写。

默认值：TextCase.Normal

number类型取值范围为[0,2]，取值间隔为1，依次对应TextCase中的枚举值。

**类型：** number \| TextCase

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-textCase?: number | TextCase--><!--Device-MeasureOptions-textCase?: number | TextCase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textContent

```TypeScript
textContent: string | Resource
```

设置被计算文本内容。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-textContent: string | Resource--><!--Device-MeasureOptions-textContent: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: number | string
```

设置首行文本缩进，默认值为0。

**类型：** number \| string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-textIndent?: number | string--><!--Device-MeasureOptions-textIndent?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置断行规则。

默认值：WordBreak.BREAK_WORD

**说明：**

WordBreak.BREAK_ALL与{overflow: TextOverflow.Ellipsis}，`maxLines`组合使用可实现英文单词按字母截断，超出部分以省略号显示。

**类型：** WordBreak

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MeasureOptions-wordBreak?: WordBreak--><!--Device-MeasureOptions-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

