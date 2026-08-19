# ChipV2SuffixImageIconConfig

ChipV2SuffixImageIconConfig定义后缀图标的属性配置。 继承自[ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md)和[ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)。

**继承/实现关系：** ChipV2SuffixImageIconConfig extends [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md), [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ChipV2SuffixImageIconConfig--><!--Device-unnamed-export interface ChipV2SuffixImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## action

```TypeScript
action?: VoidCallback
```

后缀图标点击事件回调函数。当需要为后缀图标绑定点击事件并执行自定义操作时传入此回调函数（如触发特定功能、打开弹窗等）。点击后缀图标时调用此回调函数。 默认值：undefined，不设定后缀图标事件。不传入或传入undefined时，点击后缀图标无自定义响应。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIconConfig-action?: VoidCallback--><!--Device-ChipV2SuffixImageIconConfig-action?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

