# ChipV2PrefixImageIcon

ChipV2PrefixImageIcon定义前缀图标类。 继承自[ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)。

**继承/实现关系：** ChipV2PrefixImageIcon extends [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class ChipV2PrefixImageIcon--><!--Device-unnamed-export declare class ChipV2PrefixImageIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipV2PrefixImageIconConfig)
```

ChipV2PrefixImageIcon的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2PrefixImageIcon-constructor(config: ChipV2PrefixImageIconConfig)--><!--Device-ChipV2PrefixImageIcon-constructor(config: ChipV2PrefixImageIconConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2PrefixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2prefiximageiconconfig-i.md) | 是 | 前缀图标属性配置，用于设置前缀Image图标的显示属性，继承自ChipV2ImageIconConfig，包含src、size、 fillColor等配置项。 |

