# ParagraphStyle

段落样式。

**起始版本：** 12

<!--Device-text-interface ParagraphStyle--><!--Device-text-interface ParagraphStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## align

```TypeScript
align?: TextAlign
```

文本对齐方式，默认为START。若同时配置tab属性，制表符对齐方式将失效。

**类型：** TextAlign

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-align?: TextAlign--><!--Device-ParagraphStyle-align?: TextAlign-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## autoSpace

```TypeScript
autoSpace?: boolean
```

设置文本排版时是否使能自动间距。true表示使能自动间距，则会在文本排版时自动调整CJK（中文字符、日文字符、韩文字符）与西文（拉丁字母、西里尔字母、希腊字母）、CJK与数字、CJK与版权符号、版权符号与数字、版权符号与西文之间的间距。false表示不使能自动间距，默认值为false。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-autoSpace?: boolean--><!--Device-ParagraphStyle-autoSpace?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## breakStrategy

```TypeScript
breakStrategy?: BreakStrategy
```

断行策略，默认为GREEDY。

**类型：** BreakStrategy

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-breakStrategy?: BreakStrategy--><!--Device-ParagraphStyle-breakStrategy?: BreakStrategy-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## compressHeadPunctuation

```TypeScript
compressHeadPunctuation?: boolean
```

设置文本排版时是否使能行首标点压缩。true表示使能行首标点压缩，false表示不使能行首标点压缩，默认值为false。

**说明：**

1. 需要字体文件支持[FontFeature](arkts-arkgraphics2d-text-fontfeature-i.md)中的"ss08"特性，否则无法压缩。2. 在行首标点压缩范围内的标点才在本特性作用范围内。行首压缩的标点范围:  
| 标点 | Unicode码位 | Unicode名称 |  
|---------|---------|-------------|  
| 「 | U+300C | LEFT CORNER BRACKET |  
| 『 | U+300E | LEFT WHITE CORNER BRACKET |  
| " | U+201C | LEFT DOUBLE QUOTATION MARK |  
| ' | U+2018 | LEFT SINGLE QUOTATION MARK |  
| （ | U+FF08 | FULLWIDTH LEFT PARENTHESIS |  
| 《 | U+300A | LEFT DOUBLE ANGLE BRACKET |  
| 〈 | U+3008 | LEFT ANGLE BRACKET |  
| 【 | U+3010 | LEFT BLACK LENTICULAR BRACKET |  
| 〖 | U+3016 | LEFT WHITE LENTICULAR BRACKET |  
| 〔 | U+3014 | LEFT TORTOISE SHELL BRACKET |  
| ［ | U+FF3B | FULLWIDTH LEFT SQUARE BRACKET |  
| ｛ | U+FF5B | FULLWIDTH LEFT CURLY BRACKET |

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-compressHeadPunctuation?: boolean--><!--Device-ParagraphStyle-compressHeadPunctuation?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing?: boolean
```

设置文本排版时是否使能行高回退，当设置的行高小于实际行高时，将行高回退为实际行高。true表示使能行高回退，false表示不使能行高回退，默认值为false。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-fallbackLineSpacing?: boolean--><!--Device-ParagraphStyle-fallbackLineSpacing?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## firstLineHeadIndent

```TypeScript
firstLineHeadIndent?: number
```

设置段落首行缩进，缩进值需大于等于0，默认值为0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-firstLineHeadIndent?: double--><!--Device-ParagraphStyle-firstLineHeadIndent?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## headIndents

```TypeScript
headIndents?: Array<number>
```

设置行首缩进数组，数组中每个元素代表一行缩进值，当实际文本行数超过缩进数组个数时，超过行的缩进为数组最后一个值，缩进值需全大于等于0，默认为空数组。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-headIndents?: Array<double>--><!--Device-ParagraphStyle-headIndents?: Array<double>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## includeFontPadding

```TypeScript
includeFontPadding?: boolean
```

设置文本排版时是否使能首尾行padding。true表示使能首尾行padding，false表示不使能首尾行padding，默认值为false。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-includeFontPadding?: boolean--><!--Device-ParagraphStyle-includeFontPadding?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## lineSpacing

```TypeScript
lineSpacing?: number
```

行间距，单位为物理像素px，默认值为0。lineSpacing不受[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中lineHeightMaximum和lineHeightMinimum限制。尾行默认保留行间距，可通过设置[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).textHeightBehavior为DISABLE_ALL或DISABLE_LAST_ASCENT禁用尾行行间距。

**类型：** number

**起始版本：** 21

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-lineSpacing?: double--><!--Device-ParagraphStyle-lineSpacing?: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## maxLines

```TypeScript
maxLines?: number
```

最大行数限制，整数，默认为1e9。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-maxLines?: int--><!--Device-ParagraphStyle-maxLines?: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## orphanCharOptimization

```TypeScript
orphanCharOptimization?: boolean
```

设置文本排版时是否使能孤字优化。孤字优化通过更高效地处理孤立字符（段落尾行首字符）来改善文本布局。使能后，它会调整换行点以尽可能避免孤立字符。孤字优化特性需在[wordBreak](arkts-arkgraphics2d-text-wordbreak-e.md)为非BREAK_ALL并且待排版文本首个[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)的[locale](arkts-arkgraphics2d-text-textstyle-i.md)为“zh-Hans”或“zh-Hant”时生效。true表示使能孤字优化，false表示不使能孤字优化，默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-orphanCharOptimization?: boolean--><!--Device-ParagraphStyle-orphanCharOptimization?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## punctuationOverflow

```TypeScript
punctuationOverflow?: boolean
```

尾行标点悬挂

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-punctuationOverflow?: boolean--><!--Device-ParagraphStyle-punctuationOverflow?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## strutStyle

```TypeScript
strutStyle?: StrutStyle
```

支柱样式，默认为初始的StrutStyle。

**类型：** StrutStyle

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-strutStyle?: StrutStyle--><!--Device-ParagraphStyle-strutStyle?: StrutStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## tab

```TypeScript
tab?: TextTab
```

表示段落中文本制表符后的文本对齐方式及位置，默认将制表符替换为一个空格。此参数与文本对齐方式（align属性）或省略号样式（[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)中的ellipsis属性）共同配置时无效。

**类型：** TextTab

**起始版本：** 18

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-tab?: TextTab--><!--Device-ParagraphStyle-tab?: TextTab-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## tailIndents

```TypeScript
tailIndents?: Array<number>
```

设置行尾缩进数组，数组中每个元素代表一行缩进值，当实际文本行数超过缩进数组个数时，超过行的缩进为数组最后一个值，缩进值需全大于等于0，默认为空数组。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-tailIndents?: Array<double>--><!--Device-ParagraphStyle-tailIndents?: Array<double>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## textDirection

```TypeScript
textDirection?: TextDirection
```

文本方向，默认为LTR。

**类型：** TextDirection

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-textDirection?: TextDirection--><!--Device-ParagraphStyle-textDirection?: TextDirection-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## textHeightBehavior

```TypeScript
textHeightBehavior?: TextHeightBehavior
```

文本高度修饰符模式，默认为ALL。

**类型：** TextHeightBehavior

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-textHeightBehavior?: TextHeightBehavior--><!--Device-ParagraphStyle-textHeightBehavior?: TextHeightBehavior-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## textStyle

```TypeScript
textStyle?: TextStyle
```

作用于整个段落的文本样式，默认为初始的文本样式。

**类型：** TextStyle

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-textStyle?: TextStyle--><!--Device-ParagraphStyle-textStyle?: TextStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## trailingSpaceOptimized

```TypeScript
trailingSpaceOptimized?: boolean
```

表示文本排版时是否考虑行尾空格的对齐影响。true表示忽略行尾空格的对齐影响，false表示考虑行尾空格的对齐影响，默认值为false。

**类型：** boolean

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-trailingSpaceOptimized?: boolean--><!--Device-ParagraphStyle-trailingSpaceOptimized?: boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## verticalAlign

```TypeScript
verticalAlign?: TextVerticalAlign
```

文本垂直对齐方式，开启行高缩放（即设置[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)的heightScale）或行内不同字号（即设置[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)的fontSize）文本混排时生效。若行内有上下标文本（即设置[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)的badgeType属性文本），上下标文本将与普通文本一样参与垂直对齐。

**类型：** TextVerticalAlign

**起始版本：** 20

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-verticalAlign?: TextVerticalAlign--><!--Device-ParagraphStyle-verticalAlign?: TextVerticalAlign-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

断词类型，默认为BREAK_WORD。

**类型：** WordBreak

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-wordBreak?: WordBreak--><!--Device-ParagraphStyle-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.Graphics.Drawing

