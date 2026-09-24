# MeasureOptions

```TypeScript
export interface MeasureOptions
```

被计算文本属性。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { MeasureText, MeasureOptions } from '@kit.ArkUI';
```

## baselineOffset

```TypeScript
baselineOffset?: number | string
```

设置被计算文本基线的偏移量。

默认值：0。单位：vp。string类型支持带单位的字符串，如'10px'、'10vp'。

**说明：** 正数表示基线向上偏移，负数表示基线向下偏移。

**类型：** number &#124; string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constraintWidth

```TypeScript
constraintWidth?: number | string | Resource
```

设置被计算文本布局宽度。取值范围：[0, +∞)。

**说明：** 

默认单位为vp，不支持设置百分比字符串。此参数仅在measureTextSize接口中生效，若不设置，则文本宽度为单行布局的最大宽度。若设置则为设置值，同时会影响文本的换行方式和高度计算结果。

**类型：** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

设置被计算文本字体列表。默认字体'HarmonyOS Sans'，且当前只支持这种字体。设置其他字体名称时使用默认字体'HarmonyOS Sans'。

**类型：** string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置被计算文本字体大小。取值范围：[0, +∞)，超出取值范围会导致计算结果异常。

默认值：16

**说明：** 

不支持设置百分比字符串。

fontSize为number类型时，从API version 12开始，使用fp单位，在API version 12之前使用vp单位。

**类型：** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: number | FontStyle
```

设置被计算文本字体样式。

默认值：FontStyle.Normal

number类型取值范围为[0,1]，取值间隔为1，依次对应FontStyle中的枚举值。超出范围时使用默认值FontStyle.Normal。

**类型：** number &#124; [FontStyle](arkts-arkui-fontstyle-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | string | FontWeight
```

设置被计算文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。超出范围或不在间隔值上时使用默认值400。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Normal

**类型：** number &#124; string &#124; [FontWeight](arkts-arkui-fontweight-e.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

设置被计算文本字符间距。

默认值：0

**说明：** 

默认单位为vp。string类型支持带单位的字符串，如'10px'、'10vp'。

**类型：** number &#124; string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

设置被计算文本行高，影响多行文本的高度计算结果和行间距，数值越大行间距越大。

取值范围：[0, +∞)。string类型支持带单位的字符串，如'10px'、'10vp'。

默认值：系统默认行高

默认单位为vp

**类型：** number &#124; string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

设置被计算文本最大行数，当文本实际行数超过此值时，measureTextSize的计算结果将基于最大行数进行测算，超出部分不计入高度计算。

取值范围：[0, INT32_MAX]，传入负数或超出范围时使用默认值。

默认值：不限制

**说明：** 可配合overflow: TextOverflow.Ellipsis和wordBreak.BREAK_ALL使用，实现英文单词按字母截断，超出部分以省略号显示。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: number | TextOverflow
```

设置被计算文本超长时的截断方式，需与maxLines配合使用才能生效。

默认值：1

number类型取值范围为[0,3]，取值间隔为1，依次对应TextOverflow中的枚举值。超出范围时使用默认值1。

**说明：** 当设置为TextOverflow.Ellipsis时，可配合wordBreak.BREAK_ALL和maxLines使用，实现英文单词按字母截断，超出部分以省略号显示。

**类型：** number &#124; [TextOverflow](arkts-arkui-textoverflow-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: number | TextAlign
```

设置被计算文本水平方向的对齐方式。

默认值：TextAlign.Start

number类型取值范围为[0,3]，取值间隔为1，依次对应TextAlign中的枚举值。超出范围时使用默认值TextAlign.Start。

**类型：** number &#124; [TextAlign](arkts-arkui-textalign-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textCase

```TypeScript
textCase?: number | TextCase
```

设置被计算文本大小写。

默认值：TextCase.Normal

number类型取值范围为[0,2]，取值间隔为1，依次对应TextCase中的枚举值。超出范围时使用默认值TextCase.Normal。

**类型：** number &#124; [TextCase](arkts-arkui-textcase-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textContent

```TypeScript
textContent: string | Resource
```

设置被计算文本内容。

**类型：** string &#124; [Resource](arkts-arkui-resource-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: number | string
```

设置首行文本缩进。取值范围：[0, +∞)，超出范围时使用默认值0。

默认值：0。

**说明：** 

默认单位为vp。string类型支持带单位的字符串，如'10px'、'10vp'。

**类型：** number &#124; string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置断行规则。

默认值：WordBreak.BREAK_WORD

**说明：** 

WordBreak.BREAK_ALL与overflow: TextOverflow.Ellipsis、maxLines组合使用可实现英文单词按字母截断，超出部分以省略号显示。

**类型：** [WordBreak](arkts-arkui-wordbreak-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
