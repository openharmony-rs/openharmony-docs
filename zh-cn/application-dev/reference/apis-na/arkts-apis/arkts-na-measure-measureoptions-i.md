# MeasureOptions

被计算文本属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface MeasureOptions--><!--Device-unnamed-export interface MeasureOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## baselineOffset

```TypeScript
baselineOffset?: double | string
```

设置被计算文本基线的偏移量。 默认值：0

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-baselineOffset?: double | string--><!--Device-MeasureOptions-baselineOffset?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constraintWidth

```TypeScript
constraintWidth?: double | string | Resource
```

设置被计算文本布局宽度。 **说明：** 默认单位为vp，不支持设置百分比字符串。若不设置，则文本SizeOptions宽度为单行布局所占最大宽度值，若设置则为设置值。

**类型：** double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-constraintWidth?: double | string | Resource--><!--Device-MeasureOptions-constraintWidth?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string | Resource
```

设置被计算文本字体列表。

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-fontFamily?: string | Resource--><!--Device-MeasureOptions-fontFamily?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: double | string | Resource
```

设置被计算文本字体大小，fontSize为number类型时，使用vp单位。 默认值：16 **说明：** 不支持设置百分比字符串。 从API version 12开始，fontSize为number类型时，使用fp单位。

**类型：** double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-fontSize?: double | string | Resource--><!--Device-MeasureOptions-fontSize?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: int | FontStyle
```

设置被计算文本字体样式。 默认值：FontStyle.Normal int类型取值范围为[0,1]，取值间隔为1，依次对应FontStyle中的枚举值。

**类型：** int \| [FontStyle](arkts-na-enums-fontstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-fontStyle?: int | FontStyle--><!--Device-MeasureOptions-fontStyle?: int | FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: int | string | FontWeight
```

设置被计算文本的字体粗细，int类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持int类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、" lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。 默认值：FontWeight.Normal

**类型：** int \| string \| [FontWeight](arkts-na-enums-fontweight-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-fontWeight?: int | string | FontWeight--><!--Device-MeasureOptions-fontWeight?: int | string | FontWeight-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: double | string
```

设置被计算文本字符间距。 默认值：0

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-letterSpacing?: double | string--><!--Device-MeasureOptions-letterSpacing?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: double | string | Resource
```

设置被计算文本行高。

**类型：** double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-lineHeight?: double | string | Resource--><!--Device-MeasureOptions-lineHeight?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: int
```

设置被计算文本最大行数。 取值范围：[0, INT32_MAX]

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-maxLines?: int--><!--Device-MeasureOptions-maxLines?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: int | TextOverflow
```

设置被计算文本超长时的截断方式。 默认值：1 int类型取值范围为[0,3]，取值间隔为1，依次对应TextOverflow中的枚举值。

**类型：** int \| [TextOverflow](arkts-na-enums-textoverflow-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-overflow?: int | TextOverflow--><!--Device-MeasureOptions-overflow?: int | TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: int | TextAlign
```

设置被计算文本水平方向的对齐方式。 默认值：TextAlign.Start int类型取值范围为[0,3]，取值间隔为1，依次对应TextAlign中的枚举值。

**类型：** int \| [TextAlign](arkts-na-enums-textalign-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-textAlign?: int | TextAlign--><!--Device-MeasureOptions-textAlign?: int | TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textCase

```TypeScript
textCase?: int | TextCase
```

设置被计算文本大小写。 默认值：TextCase.Normal int类型取值范围为[0,2]，取值间隔为1，依次对应TextCase中的枚举值。

**类型：** int \| [TextCase](arkts-na-enums-textcase-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-textCase?: int | TextCase--><!--Device-MeasureOptions-textCase?: int | TextCase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textContent

```TypeScript
textContent: string | Resource
```

设置被计算文本内容。

**类型：** string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-textContent: string | Resource--><!--Device-MeasureOptions-textContent: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: double | string
```

设置首行文本缩进，默认值为0。

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-textIndent?: double | string--><!--Device-MeasureOptions-textIndent?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置断行规则。 默认值：WordBreak.BREAK_WORD **说明：** WordBreak.BREAK_ALL与{overflow: TextOverflow.Ellipsis}，`maxLines`组合使用可实现英文单词按字母截断，超出部分以省略号显示。

**类型：** [WordBreak](arkts-na-enums-wordbreak-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MeasureOptions-wordBreak?: WordBreak--><!--Device-MeasureOptions-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

