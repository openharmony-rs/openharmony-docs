# ChipV2

```TypeScript
export declare struct ChipV2
```

创建ChipV2组件。

**起始版本：** 26.0.0

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ChipV2--><!--Device-unnamed-export declare struct ChipV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## build

```TypeScript
build(): void
```

build函数用于构造ChipV2高级组件的UI结构。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ChipV2-build(): void--><!--Device-ChipV2-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## chipV2Options

```TypeScript
readonly chipV2Options: ChipV2Options
```

定义ChipV2组件的参数，用于自定义ChipV2组件的外观和行为，包含label、prefixIcon、suffixIcon、allowClose、activated、backgroundColor、size等配置项。

**类型：** [ChipV2Options](arkts-arkui-arkui-advanced-chipv2-chipv2options-c.md)

**起始版本：** 26.0.0

**装饰器类型：** @Require

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-ChipV2-readonly chipV2Options: ChipV2Options--><!--Device-ChipV2-readonly chipV2Options: ChipV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
