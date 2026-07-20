# IChipV2OptionsConfig

定义ChipV2选项接口。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface IChipV2OptionsConfig--><!--Device-unnamed-export interface IChipV2OptionsConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2SuffixSymbolIconConfig, ChipV2Label, ChipV2PrefixSymbolIconConfig, IChipV2OptionsConfig, ChipV2SymbolIcon, ChipV2SuffixImageIconConfig, ChipV2LocalizedLabelMarginConfig, ChipV2SymbolIconConfig, ChipV2LabelConfig, ChipV2SuffixSymbolIcon, ChipV2AccessibilityConfig, ChipV2Icon, ChipV2Size, ChipV2CloseConfig, ChipV2SuffixImageIcon, ChipV2Accessibility, ChipV2Options, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2PrefixImageIcon, ChipV2LabelMarginConfig, ChipV2PrefixSymbolIcon, ChipV2, ChipV2CloseIcon, ChipV2PrefixImageIconConfig, ChipV2AccessibilitySelectedType } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

为Chip设置无障碍描述

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-accessibilityDescription?: ResourceStr--><!--Device-IChipV2OptionsConfig-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

设置Chip的无障碍级别。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-accessibilityLevel?: string--><!--Device-IChipV2OptionsConfig-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
accessibilitySelectedType?: ChipV2AccessibilitySelectedType
```

为Chip设置无障碍选择类型。

**类型：** ChipV2AccessibilitySelectedType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-accessibilitySelectedType?: ChipV2AccessibilitySelectedType--><!--Device-IChipV2OptionsConfig-accessibilitySelectedType?: ChipV2AccessibilitySelectedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
activated?: boolean
```

设置Chip是否处于活动状态。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-activated?: boolean--><!--Device-IChipV2OptionsConfig-activated?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
activatedBackgroundColor?: ColorMetrics
```

Chip激活时的背景色。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-activatedBackgroundColor?: ColorMetrics--><!--Device-IChipV2OptionsConfig-activatedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
activatedBackgroundSystemMaterial?: uiMaterial.Material
```

为激活的组件设置系统样式材质。不同的材料有不同的效果，它可以影响组件的背景颜色、边框、阴影和其他视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-activatedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-IChipV2OptionsConfig-activatedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
allowClose?: boolean
```

显示关闭图标。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-allowClose?: boolean--><!--Device-IChipV2OptionsConfig-allowClose?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ColorMetrics
```

Chip背景色。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-backgroundColor?: ColorMetrics--><!--Device-IChipV2OptionsConfig-backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

为组件设置系统样式材质。不同的材料有不同的效果，会影响组件的背景颜色、边框、阴影和其他视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-backgroundSystemMaterial?: uiMaterial.Material--><!--Device-IChipV2OptionsConfig-backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Chip半径。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-borderRadius?: LengthMetrics--><!--Device-IChipV2OptionsConfig-borderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
closeIcon?: ChipV2CloseIcon
```

当'allowClose'为true时，为默认关闭图标设置config。

**类型：** ChipV2CloseIcon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-closeIcon?: ChipV2CloseIcon--><!--Device-IChipV2OptionsConfig-closeIcon?: ChipV2CloseIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

当前Chip方向属性

**类型：** Direction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-direction?: Direction--><!--Device-IChipV2OptionsConfig-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Chip使能。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-enabled?: boolean--><!--Device-IChipV2OptionsConfig-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

设置标签文本和关闭图标的字体大小。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-fontSize?: LengthMetrics--><!--Device-IChipV2OptionsConfig-fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label: ChipV2Label
```

芯片标签。

**类型：** ChipV2Label

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-label: ChipV2Label--><!--Device-IChipV2OptionsConfig-label: ChipV2Label-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
maxFontScale?: number | Resource
```

Chip的最大字体比例。

**类型：** number \| Resource

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-maxFontScale?: number | Resource--><!--Device-IChipV2OptionsConfig-maxFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
minFontScale?: number | Resource
```

Chip的最小字体比例。

**类型：** number \| Resource

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-minFontScale?: number | Resource--><!--Device-IChipV2OptionsConfig-minFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
onClicked?: Callback<void>
```

点击Chip时触发的回调。

**类型：** Callback&lt;void&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-onClicked?: Callback<void>--><!--Device-IChipV2OptionsConfig-onClicked?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
onClose?: VoidCallback
```

关闭Chip时触发的回调。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-onClose?: VoidCallback--><!--Device-IChipV2OptionsConfig-onClose?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
padding?: LocalizedPadding
```

Chip填充大小。

**类型：** LocalizedPadding

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-padding?: LocalizedPadding--><!--Device-IChipV2OptionsConfig-padding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
prefixIcon?: ChipV2Icon
```

Chip前缀图标。

**类型：** ChipV2Icon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-prefixIcon?: ChipV2Icon--><!--Device-IChipV2OptionsConfig-prefixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: ChipV2Size | SizeT<LengthMetrics>
```

Chip尺寸。

**类型：** ChipV2Size \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-IChipV2OptionsConfig-size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
suffixIcon?: ChipV2Icon
```

Chip后缀图标。

**类型：** ChipV2Icon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-IChipV2OptionsConfig-suffixIcon?: ChipV2Icon--><!--Device-IChipV2OptionsConfig-suffixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

