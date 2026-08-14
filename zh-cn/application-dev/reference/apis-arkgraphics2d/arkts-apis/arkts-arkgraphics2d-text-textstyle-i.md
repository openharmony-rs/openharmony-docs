# TextStyle

文本样式，用于控制文本的视觉表现属性，包括字体、颜色、字号、间距、装饰线和阴影等。TextStyle通过[ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md#ParagraphBuilder)的 [pushStyle](arkts-arkgraphics2d-text-paragraphbuilder-c.md#pushStyle)方法应用到后续添加的文本内容，与[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md#ParagraphStyle)（控制段落级 别属性）配合使用。同一段落中可通过多次pushStyle实现对不同文本片段应用不同样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-text-interface TextStyle--><!--Device-text-interface TextStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## backgroundRect

```TypeScript
backgroundRect?: RectStyle
```

文本矩形框样式。当需要为文本添加背景矩形框（如设置背景色、圆角等）时传入。

**类型：** [RectStyle](arkts-arkgraphics2d-text-rectstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-backgroundRect?: RectStyle--><!--Device-TextStyle-backgroundRect?: RectStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## badgeType

```TypeScript
badgeType?: TextBadgeType
```

设置文本排版时是否使能上标或下标。TEXT_SUPERSCRIPT表示使能上标，TEXT_SUBSCRIPT表示使能下标，默认值为TEXT_BADGE_NONE表示不使能。

**类型：** [TextBadgeType](arkts-arkgraphics2d-text-textbadgetype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-badgeType?: TextBadgeType--><!--Device-TextStyle-badgeType?: TextBadgeType-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## baseline

```TypeScript
baseline?: TextBaseline
```

文本基线类型，默认为ALPHABETIC。

**类型：** [TextBaseline](arkts-arkgraphics2d-text-textbaseline-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-baseline?: TextBaseline--><!--Device-TextStyle-baseline?: TextBaseline-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## baselineShift

```TypeScript
baselineShift?: double
```

文本基线的垂直偏移距离，浮点数，单位为物理像素px，默认为0.0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-baselineShift?: double--><!--Device-TextStyle-baselineShift?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## color

```TypeScript
color?: common2D.Color
```

文字颜色，默认为白色。

**类型：** common2D.Color

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-color?: common2D.Color--><!--Device-TextStyle-color?: common2D.Color-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## decoration

```TypeScript
decoration?: Decoration
```

装饰线设置，默认不使用装饰线。

**类型：** [Decoration](arkts-arkgraphics2d-text-decoration-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-decoration?: Decoration--><!--Device-TextStyle-decoration?: Decoration-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## ellipsis

```TypeScript
ellipsis?: string
```

省略号文本，表示省略号生效后使用该字段值替换省略号部分，默认为空字符串，即使用系统默认省略号…（U+2026）。与ParagraphStyle的tab属性共同配置时，tab属性无效。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-ellipsis?: string--><!--Device-TextStyle-ellipsis?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## ellipsisMode

```TypeScript
ellipsisMode?: EllipsisMode
```

省略号类型，默认为END，行尾省略号。

**类型：** EllipsisMode

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-ellipsisMode?: EllipsisMode--><!--Device-TextStyle-ellipsisMode?: EllipsisMode-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontEdging

```TypeScript
fontEdging?: drawing.FontEdging
```

绘制文本的边缘处理方式，默认值为ANTI_ALIAS。

**类型：** drawing.FontEdging

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontEdging?: drawing.FontEdging--><!--Device-TextStyle-fontEdging?: drawing.FontEdging-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontFamilies

```TypeScript
fontFamilies?: Array<string>
```

字体家族名称列表，默认为空，匹配系统字体。使用自定义字体时，需将加载字体时指定的名称填入此列表中。当与fontTypefaces同时设置时，fontTypefaces优先级更高，fontFamilies不生效。

**类型：** Array&lt;string&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontFamilies?: Array<string>--><!--Device-TextStyle-fontFamilies?: Array<string>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontFeatures

```TypeScript
fontFeatures?: Array<FontFeature>
```

文本字体特征数组。当需要启用或禁用特定字体特性（如连字、字距调整等）时传入。

**类型：** Array&lt;FontFeature&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontFeatures?: Array<FontFeature>--><!--Device-TextStyle-fontFeatures?: Array<FontFeature>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontSize

```TypeScript
fontSize?: double
```

字体大小，浮点数，默认为14.0，单位为物理像素px。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontSize?: double--><!--Device-TextStyle-fontSize?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式，默认为常规样式。

**类型：** FontStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontStyle?: FontStyle--><!--Device-TextStyle-fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontTypefaces

```TypeScript
fontTypefaces?: Array<drawing.Typeface>
```

指定排版字体对象数组，用于优先使用指定的字体对象进行文本塑形，跳过字体匹配流程。当数组中某个字体对象无法塑形部分文字时，未能塑形的文字将使用系统字体进行塑形。默认为空数组，表示不指定字体对象，使用默认字体匹配流程。 当fontTypefaces与[TextStyle](#TextStyle).fontFamilies同时设置时，fontTypefaces优先级更高。

**类型：** Array&lt;drawing.Typeface&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontTypefaces?: Array<drawing.Typeface>--><!--Device-TextStyle-fontTypefaces?: Array<drawing.Typeface>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontVariations

```TypeScript
fontVariations?: Array<FontVariation>
```

可变字体属性数组。当需要调整可变字体的可变轴参数（如字重轴、字宽轴等）时传入。

**类型：** Array&lt;FontVariation&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontVariations?: Array<FontVariation>--><!--Device-TextStyle-fontVariations?: Array<FontVariation>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

字重，默认为W400。 在&lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;之前，仅系统字体中的可变字体支持字重调节；从&lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;开 始，系统字体与三方注册字体中的可变字体均支持字重调节。非可变字体设置字重值小于semi-bold（即W600）时字体粗细无变化，设置字重值大于等于semi-bold（即W600）时可能会触发伪加粗效果。

**类型：** FontWeight

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontWeight?: FontWeight--><!--Device-TextStyle-fontWeight?: FontWeight-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fontWidth

```TypeScript
fontWidth?: FontWidth
```

字体宽度，默认为NORMAL。

**类型：** [FontWidth](arkts-arkgraphics2d-text-fontwidth-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-fontWidth?: FontWidth--><!--Device-TextStyle-fontWidth?: FontWidth-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## halfLeading

```TypeScript
halfLeading?: boolean
```

true表示将行间距平分至行的顶部与底部，false则不平分，默认为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-halfLeading?: boolean--><!--Device-TextStyle-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## heightOnly

```TypeScript
heightOnly?: boolean
```

true表示根据字体大小和heightScale设置文本框的高度，false表示根据行高和行距设置文本框高度，默认为false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-heightOnly?: boolean--><!--Device-TextStyle-heightOnly?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## heightScale

```TypeScript
heightScale?: double
```

行高缩放倍数，浮点数，默认为1.0，heightOnly为true时生效。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-heightScale?: double--><!--Device-TextStyle-heightScale?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## letterSpacing

```TypeScript
letterSpacing?: double
```

字符间距，正数拉开字符距离，如果为负数则拉近字符距离，浮点数，单位为物理像素px，默认为0.0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-letterSpacing?: double--><!--Device-TextStyle-letterSpacing?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## lineHeightMaximum

```TypeScript
lineHeightMaximum?: double
```

行高上限，单位为物理像素px。若同时应用行高缩放，行高上限在[TextStyle](#TextStyle).heightScale大于0时生效。取值为正数浮点数，默认值为Number.MAX_VALUE。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-lineHeightMaximum?: double--><!--Device-TextStyle-lineHeightMaximum?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## lineHeightMinimum

```TypeScript
lineHeightMinimum?: double
```

行高下限，单位为物理像素px。若同时应用行高缩放，行高下限在[TextStyle](#TextStyle).heightScale大于0时生效。取值范围为非负浮点数，默认值为0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-lineHeightMinimum?: double--><!--Device-TextStyle-lineHeightMinimum?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## lineHeightStyle

```TypeScript
lineHeightStyle?: LineHeightStyle
```

行高缩放基数样式。默认为FONT_SIZE。

**类型：** LineHeightStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-lineHeightStyle?: LineHeightStyle--><!--Device-TextStyle-lineHeightStyle?: LineHeightStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## locale

```TypeScript
locale?: string
```

语言类型，例如'en-Latn'代表英文(拉丁文字)，'zh-Hans'代表简体中文，'zh-Hant'代表繁体中文。支持language-script格式的两段式语言标签，language遵循ISO 639-1规范， script遵循ISO 15924规范。未指定locale或者设置为空字符串或为undefined时，默认locale为'zh-Hans'。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-locale?: string--><!--Device-TextStyle-locale?: string-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## textShadows

```TypeScript
textShadows?: Array<TextShadow>
```

文本阴影数组。当需要为文本添加阴影效果时传入。

**类型：** Array&lt;[TextShadow](arkts-arkgraphics2d-text-textshadow-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-textShadows?: Array<TextShadow>--><!--Device-TextStyle-textShadows?: Array<TextShadow>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## wordSpacing

```TypeScript
wordSpacing?: double
```

单词间距，浮点数，单位为物理像素px，默认为0.0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyle-wordSpacing?: double--><!--Device-TextStyle-wordSpacing?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

