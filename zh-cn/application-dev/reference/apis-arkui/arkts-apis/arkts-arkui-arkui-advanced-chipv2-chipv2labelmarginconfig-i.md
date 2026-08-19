# ChipV2LabelMarginConfig

ChipV2LabelMarginConfig定义文本与左右侧图标之间间距配置。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipV2LabelMarginConfig--><!--Device-unnamed-export interface ChipV2LabelMarginConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## left

```TypeScript
left?: LengthMetrics
```

文本与左侧图标之间间距，不支持百分比。传入百分比时按默认值处理。 默认值： 无左侧图标时，left默认值：0。 有左侧图标且size为ChipV2Size.SMALL时，left默认值：4。 有左侧图标且size为ChipV2Size.NORMAL时，left默认值：6。 单位：vp 超出取值范围按默认值处理。 取值范围：[0, +∞)

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelMarginConfig-left?: LengthMetrics--><!--Device-ChipV2LabelMarginConfig-left?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: LengthMetrics
```

文本与右侧图标之间间距，不支持百分比。传入百分比时按默认值处理。 默认值： 无右侧图标时，right默认值：0。 有右侧图标且size为ChipV2Size.SMALL时，right默认值：4。 有右侧图标且size为ChipV2Size.NORMAL时，right默认值：6。 单位：vp 超出取值范围按默认值处理。 取值范围：[0, +∞)

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2LabelMarginConfig-right?: LengthMetrics--><!--Device-ChipV2LabelMarginConfig-right?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

