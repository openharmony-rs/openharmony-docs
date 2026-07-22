# ChipV2Options

定义Chip选项类。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export class ChipV2Options--><!--Device-unnamed-export class ChipV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2SuffixSymbolIconConfig, ChipV2Label, ChipV2PrefixSymbolIconConfig, IChipV2OptionsConfig, ChipV2SymbolIcon, ChipV2SuffixImageIconConfig, ChipV2LocalizedLabelMarginConfig, ChipV2SymbolIconConfig, ChipV2LabelConfig, ChipV2SuffixSymbolIcon, ChipV2AccessibilityConfig, ChipV2Icon, ChipV2Size, ChipV2CloseConfig, ChipV2SuffixImageIcon, ChipV2Accessibility, ChipV2Options, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2PrefixImageIcon, ChipV2LabelMarginConfig, ChipV2PrefixSymbolIcon, ChipV2, ChipV2CloseIcon, ChipV2PrefixImageIconConfig, ChipV2AccessibilitySelectedType } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: IChipV2OptionsConfig)
```

ChipV2Options的构造函数

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-constructor(config: IChipV2OptionsConfig)--><!--Device-ChipV2Options-constructor(config: IChipV2OptionsConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [IChipV2OptionsConfig](arkts-arkui-arkui-advanced-chipv2-ichipv2optionsconfig-i.md) | 是 | Chip的选项 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

为Chip设置无障碍描述

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public accessibilityDescription?: ResourceStr--><!--Device-ChipV2Options-public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

设置Chip的无障碍级别。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public accessibilityLevel?: string--><!--Device-ChipV2Options-public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySelectedType

```TypeScript
public accessibilitySelectedType?: ChipV2AccessibilitySelectedType
```

为Chip设置无障碍选择类型。

**类型：** ChipV2AccessibilitySelectedType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public accessibilitySelectedType?: ChipV2AccessibilitySelectedType--><!--Device-ChipV2Options-public accessibilitySelectedType?: ChipV2AccessibilitySelectedType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activated

```TypeScript
public activated?: boolean
```

设置Chip是否处于活动状态。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public activated?: boolean--><!--Device-ChipV2Options-public activated?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundColor

```TypeScript
public activatedBackgroundColor?: ColorMetrics
```

Chip激活时的背景色。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public activatedBackgroundColor?: ColorMetrics--><!--Device-ChipV2Options-public activatedBackgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedBackgroundSystemMaterial

```TypeScript
public activatedBackgroundSystemMaterial?: uiMaterial.Material
```

为激活的组件设置系统样式材质。不同的材料有不同的效果，它可以影响组件的背景颜色、边框、阴影和其他视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public activatedBackgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipV2Options-public activatedBackgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowClose

```TypeScript
public allowClose?: boolean
```

显示关闭图标。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public allowClose?: boolean--><!--Device-ChipV2Options-public allowClose?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
public backgroundColor?: ColorMetrics
```

Chip背景色。

**类型：** ColorMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public backgroundColor?: ColorMetrics--><!--Device-ChipV2Options-public backgroundColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
public backgroundSystemMaterial?: uiMaterial.Material
```

为组件设置系统样式材质。不同的材料有不同的效果，会影响组件的背景颜色、边框、阴影和其他视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public backgroundSystemMaterial?: uiMaterial.Material--><!--Device-ChipV2Options-public backgroundSystemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
public borderRadius?: LengthMetrics
```

Chip半径。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public borderRadius?: LengthMetrics--><!--Device-ChipV2Options-public borderRadius?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeIcon

```TypeScript
public closeIcon?: ChipV2CloseIcon
```

当'allowClose'为true时，为默认关闭图标设置config。

**类型：** ChipV2CloseIcon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public closeIcon?: ChipV2CloseIcon--><!--Device-ChipV2Options-public closeIcon?: ChipV2CloseIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
public direction?: Direction
```

当前Chip方向属性

**类型：** Direction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public direction?: Direction--><!--Device-ChipV2Options-public direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
public enabled?: boolean
```

Chip使能。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public enabled?: boolean--><!--Device-ChipV2Options-public enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
public fontSize?: LengthMetrics
```

设置标签文本和关闭图标的字体大小。

**类型：** LengthMetrics

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public fontSize?: LengthMetrics--><!--Device-ChipV2Options-public fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
public label: ChipV2Label
```

Chip前缀图标。

**类型：** ChipV2Label

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public label: ChipV2Label--><!--Device-ChipV2Options-public label: ChipV2Label-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxFontScale

```TypeScript
public maxFontScale?: number | Resource
```

Chip的最大字体比例。

**类型：** number \| Resource

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public maxFontScale?: number | Resource--><!--Device-ChipV2Options-public maxFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minFontScale

```TypeScript
public minFontScale?: number | Resource
```

Chip的最小字体比例。

**类型：** number \| Resource

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public minFontScale?: number | Resource--><!--Device-ChipV2Options-public minFontScale?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClicked

```TypeScript
public onClicked?: Callback<void>
```

点击Chip时触发的回调。

**类型：** Callback&lt;void&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public onClicked?: Callback<void>--><!--Device-ChipV2Options-public onClicked?: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
public onClose?: VoidCallback
```

关闭Chip时触发的回调。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public onClose?: VoidCallback--><!--Device-ChipV2Options-public onClose?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## padding

```TypeScript
public padding?: LocalizedPadding
```

Chip填充大小。

**类型：** LocalizedPadding

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public padding?: LocalizedPadding--><!--Device-ChipV2Options-public padding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## prefixIcon

```TypeScript
public prefixIcon?: ChipV2Icon
```

Chip前缀图标。

**类型：** ChipV2Icon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public prefixIcon?: ChipV2Icon--><!--Device-ChipV2Options-public prefixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
public size?: ChipV2Size | SizeT<LengthMetrics>
```

Chip尺寸。

**类型：** ChipV2Size \| SizeT&lt;LengthMetrics&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public size?: ChipV2Size | SizeT<LengthMetrics>--><!--Device-ChipV2Options-public size?: ChipV2Size | SizeT<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## suffixIcon

```TypeScript
public suffixIcon?: ChipV2Icon
```

Chip后缀图标。

**类型：** ChipV2Icon

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2Options-public suffixIcon?: ChipV2Icon--><!--Device-ChipV2Options-public suffixIcon?: ChipV2Icon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

