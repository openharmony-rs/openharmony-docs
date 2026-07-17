# LabelOptions

LabelOptions定义文本属性。

**起始版本：** 11

<!--Device-unnamed-export interface LabelOptions--><!--Device-unnamed-export interface LabelOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SuffixIconOptions, CloseOptions, ChipSymbolGlyphOptions, Chip, AccessibilitySelectedType, LabelMarginOptions, LabelOptions, PrefixIconOptions, IconCommonOptions, ChipOptions, ChipSuffixSymbolGlyphOptions, ChipSize, AccessibilityOptions } from '@kit.ArkUI';
```

## activatedFontColor

```TypeScript
activatedFontColor?: ResourceColor
```

操作块激活时的文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary_contrary')

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-activatedFontColor?: ResourceColor--><!--Device-LabelOptions-activatedFontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文字颜色。

默认值：$r('sys.color.ohos_id_color_text_primary')

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-fontColor?: ResourceColor--><!--Device-LabelOptions-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

文字字体。

默认值："HarmonyOS Sans"

值为undefined时，按默认值处理。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-fontFamily?: string--><!--Device-LabelOptions-fontFamily?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

文字字号，不支持百分比。

默认值：$r('sys.float.ohos_id_text_size_button2')

值为undefined时，按默认值处理。

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-fontSize?: Dimension--><!--Device-LabelOptions-fontSize?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: LabelMarginOptions
```

文本与左右侧图标之间间距。

默认值：

size为ChipSize.SMALL时，默认值：{ left: 4, right: 4 }

size为ChipSize.NORMAL时，默认值：{ left: 6, right: 6 }

单位：vp

值为undefined时，按默认值处理。

**类型：** LabelMarginOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-labelMargin?: LabelMarginOptions--><!--Device-LabelOptions-labelMargin?: LabelMarginOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: LocalizedLabelMarginOptions
```

本地化文本与左右侧图标之间间距。

默认值：

size为ChipSize.SMALL时，默认值：

`{ start: LengthMetrics.resource($r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_small_text_margin')) }`

size为ChipSize.NORMAL时，默认值：

`{ start: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource($r('sys.float.chip_normal_text_margin')) }`

值为undefined时，按默认值处理。

**类型：** LocalizedLabelMarginOptions

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-localizedLabelMargin?: LocalizedLabelMarginOptions--><!--Device-LabelOptions-localizedLabelMargin?: LocalizedLabelMarginOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

文本文字内容。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-LabelOptions-text: string--><!--Device-LabelOptions-text: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

