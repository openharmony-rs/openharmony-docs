# ChipV2ImageIconConfig

ChipV2ImageIconConfig定义图标的通用属性配置。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipV2ImageIconConfig--><!--Device-unnamed-export interface ChipV2ImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## activatedFillColor

```TypeScript
activatedFillColor?: ColorMetrics
```

ChipV2激活时图标填充颜色。 默认值：\$r('sys.color.chip_active_icon_color')，非SVG图片不应用默认值。 值为undefined时，按默认值处理。 仅在图片格式为SVG时，activatedFillColor属性才生效。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIconConfig-activatedFillColor?: ColorMetrics--><!--Device-ChipV2ImageIconConfig-activatedFillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
fillColor?: ColorMetrics
```

图标填充颜色。 默认值：\$r('sys.color.chip_usually_icon_color')，非SVG图片不应用默认值。 值为undefined时，按默认值处理。 仅在图片格式为SVG时，fillColor属性才生效。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIconConfig-fillColor?: ColorMetrics--><!--Device-ChipV2ImageIconConfig-fillColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## modifier

```TypeScript
modifier?: ImageModifier
```

图标修饰器，用于设置图标的通用属性。当需要通过modifier动态修改图标属性（如opacity、objectFit等）时传入此参数。不传入或传入undefined时，不应用修饰器，图标使用默认属性设置。 默认值：undefined，不应用修饰器。

**类型：** [ImageModifier](../arkts-components/arkts-arkui-imagemodifier-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIconConfig-modifier?: ImageModifier--><!--Device-ChipV2ImageIconConfig-modifier?: ImageModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<LengthMetrics>
```

图标大小，不支持百分比。传入百分比时按默认值处理。 默认值： - 当ChipV2Options.size为ChipV2Size.SMALL时，默认值为：{width: \$r('sys.float.chip_small_icon_size'), height: \$r(' sys.float.chip_small_icon_size')}。 - 当ChipV2Options.size为ChipV2Size.NORMAL时，默认值为：{width: \$r('sys.float.chip_normal_icon_size'), height: \$r(' sys.float.chip_normal_icon_size')}。 单位：vp 值为undefined时，按默认值处理。

**类型：** SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIconConfig-size?: SizeT<LengthMetrics>--><!--Device-ChipV2ImageIconConfig-size?: SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

图标图片或图片地址引用。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2ImageIconConfig-src: ResourceStr--><!--Device-ChipV2ImageIconConfig-src: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

