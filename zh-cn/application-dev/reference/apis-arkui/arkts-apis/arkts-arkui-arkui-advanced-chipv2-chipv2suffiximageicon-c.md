# ChipV2SuffixImageIcon

定义后缀图标。

**继承/实现关系：** ChipV2SuffixImageIcon extends [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ChipV2SuffixImageIcon extends ChipV2ImageIcon--><!--Device-unnamed-export declare class ChipV2SuffixImageIcon extends ChipV2ImageIcon-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2SuffixSymbolIconConfig, ChipV2Label, ChipV2PrefixSymbolIconConfig, IChipV2OptionsConfig, ChipV2SymbolIcon, ChipV2SuffixImageIconConfig, ChipV2LocalizedLabelMarginConfig, ChipV2SymbolIconConfig, ChipV2LabelConfig, ChipV2SuffixSymbolIcon, ChipV2AccessibilityConfig, ChipV2Icon, ChipV2Size, ChipV2CloseConfig, ChipV2SuffixImageIcon, ChipV2Accessibility, ChipV2Options, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2PrefixImageIcon, ChipV2LabelMarginConfig, ChipV2PrefixSymbolIcon, ChipV2, ChipV2CloseIcon, ChipV2PrefixImageIconConfig, ChipV2AccessibilitySelectedType } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(config: ChipV2SuffixImageIconConfig)
```

ChipV2SuffixImageIcon的构造函数

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIcon-constructor(config: ChipV2SuffixImageIconConfig)--><!--Device-ChipV2SuffixImageIcon-constructor(config: ChipV2SuffixImageIconConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md) | 是 | 后缀图标的配置 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

设置辅助功能描述。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIcon-public accessibilityDescription?: ResourceStr--><!--Device-ChipV2SuffixImageIcon-public accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

设置可访问级别。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIcon-public accessibilityLevel?: string--><!--Device-ChipV2SuffixImageIcon-public accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

设置辅助功能文本。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIcon-public accessibilityText?: ResourceStr--><!--Device-ChipV2SuffixImageIcon-public accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
public action?: VoidCallback
```

当单击后缀图标时调用的回调。

**类型：** VoidCallback

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIcon-public action?: VoidCallback--><!--Device-ChipV2SuffixImageIcon-public action?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

