# ChipV2LabelConfig

ChipV2LabelConfig定义文本属性配置。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipV2LabelConfig--><!--Device-unnamed-export interface ChipV2LabelConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## activatedFontColor

```TypeScript
activatedFontColor?: ColorMetrics
```

ChipV2激活时的文字颜色。 默认值：\$r('sys.color.chip_activated_fontcolor') 值为undefined时，按默认值处理。 值为非法值时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-activatedFontColor?: ColorMetrics--><!--Device-ChipV2LabelConfig-activatedFontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ColorMetrics
```

文字颜色。 默认值：\$r('sys.color.chip_font_color') 值为undefined时，按默认值处理。 值为非法值时，按默认值处理。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-fontColor?: ColorMetrics--><!--Device-ChipV2LabelConfig-fontColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

文字字体。 默认值："HarmonyOS Sans" 值为undefined时，按默认值处理。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-fontFamily?: string--><!--Device-ChipV2LabelConfig-fontFamily?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

文字字号，不支持百分比。传入百分比时按默认值处理。 默认值： size为ChipV2Size.SMALL时，默认值：\$r('sys.float.chip_small_font_size')。 其他情况下，默认值：\$r('sys.float.chip_normal_font_size') 单位：fp 值为undefined时，按默认值处理。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-fontSize?: LengthMetrics--><!--Device-ChipV2LabelConfig-fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: ChipV2LabelMarginConfig
```

文本与左右侧图标之间间距。 默认值： size为ChipV2Size.SMALL时，默认值：{ left: 4, right: 4 }。 size为ChipV2Size.NORMAL时，默认值：{ left: 6, right: 6 }。 值为undefined时，按默认值处理。

**类型：** [ChipV2LabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2labelmarginconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-labelMargin?: ChipV2LabelMarginConfig--><!--Device-ChipV2LabelConfig-labelMargin?: ChipV2LabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig
```

本地化文本与左右侧图标之间间距。 默认值： size为ChipV2Size.SMALL时，默认值： `{ start: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')) }`。 size为ChipV2Size.NORMAL时，默认值： `{ start: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')) }`。 值为undefined时，按默认值处理。

**类型：** [ChipV2LocalizedLabelMarginConfig](arkts-arkui-arkui-advanced-chipv2-chipv2localizedlabelmarginconfig-i.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig--><!--Device-ChipV2LabelConfig-localizedLabelMargin?: ChipV2LocalizedLabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
modifier?: TextModifier
```

文本修饰器，用于设置文本的通用属性。当需要通过modifier动态修改文本属性（如fontWeight、fontStyle等）时传入此参数。不传入或传入undefined时，不应用修饰器，文本使用默认属性设置。 默认值：undefined，不应用修饰器。

**类型：** TextModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-modifier?: TextModifier--><!--Device-ChipV2LabelConfig-modifier?: TextModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

文本文字内容。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelConfig-text: string--><!--Device-ChipV2LabelConfig-text: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

