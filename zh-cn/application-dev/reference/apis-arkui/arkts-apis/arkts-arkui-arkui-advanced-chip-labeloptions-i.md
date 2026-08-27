# LabelOptions

LabelOptions定义文本属性。

> **说明：**
> 
> 从API版本26.0.0开始，backgroundSystemMaterial设置自动反色的系统材质时，fontColor使用支持反色的特殊系统资源，文字颜色自动适配到材质背景色的反色；
> activatedBackgroundSystemMaterial设置自动反色的系统材质时，activatedFontColor使用支持反色的特殊系统资源，Chip激活时的文字颜色自动适配到材质背景色的反色。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## activatedFontColor

```TypeScript
activatedFontColor?: ResourceColor
```

Chip激活时的文字颜色。默认值：\$r('sys.color.ohos_id_color_text_primary_contrary')值为undefined时，按默认值处理。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文字颜色。默认值：\$r('sys.color.ohos_id_color_text_primary')值为undefined时，按默认值处理。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: string
```

设置Chip组件文本的字体样式。默认值："HarmonyOS Sans"值为undefined时，按默认值处理。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

字体大小，不支持百分比，传入百分比时按默认值处理。传入负数时，按默认值处理。默认值：\$r('sys.float.ohos_id_text_size_button2')单位：fp值为undefined时，按默认值处理。

**类型：** [Dimension](arkts-arkui-dimension-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelMargin

```TypeScript
labelMargin?: LabelMarginOptions
```

文本与左右侧图标之间间距。默认值：size为ChipSize.SMALL时，{ left: 4, right: 4 }size为ChipSize.NORMAL时，{ left: 6, right: 6 }单位：vp值为undefined时，按默认值处理。

**类型：** [LabelMarginOptions](arkts-arkui-arkui-advanced-chip-labelmarginoptions-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localizedLabelMargin

```TypeScript
localizedLabelMargin?: LocalizedLabelMarginOptions
```

本地化文本与左右侧图标之间间距。默认值：size为ChipSize.SMALL时，`{ start: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_small_text_margin')) }`size为ChipSize.NORMAL时，`{ start: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')), end: LengthMetrics.resource(\$r('sys.float.chip_normal_text_margin')) }`值为undefined时，按默认值处理。

**类型：** [LocalizedLabelMarginOptions](arkts-arkui-arkui-advanced-chip-localizedlabelmarginoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string
```

Chip组件显示的文本内容。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
