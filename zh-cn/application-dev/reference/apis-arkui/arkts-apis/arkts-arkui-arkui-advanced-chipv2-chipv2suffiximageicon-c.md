# ChipV2SuffixImageIcon

ChipV2SuffixImageIcon定义后缀图标类。继承自[ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)。

**继承/实现关系：** ChipV2SuffixImageIcon extends [ChipV2ImageIcon](arkts-arkui-arkui-advanced-chipv2-chipv2imageicon-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipV2Size, ChipV2AccessibilitySelectedType, ChipV2ImageIconConfig, ChipV2ImageIcon, ChipV2SuffixImageIconConfig, ChipV2SuffixImageIcon, ChipV2Icon, ChipV2PrefixImageIconConfig, ChipV2PrefixImageIcon, ChipV2AccessibilityConfig, ChipV2Accessibility, ChipV2CloseConfig, ChipV2CloseIcon, ChipV2SymbolIconConfig, ChipV2SymbolIcon, ChipV2PrefixSymbolIconConfig, ChipV2PrefixSymbolIcon, ChipV2SuffixSymbolIconConfig, ChipV2SuffixSymbolIcon, ChipV2LabelMarginConfig, ChipV2LocalizedLabelMarginConfig, ChipV2LabelConfig, ChipV2Label, IChipV2OptionsConfig, ChipV2Options, ChipV2 } from '@kit.ArkUI';
```

## action

```TypeScript
public action?: VoidCallback
```

后缀图标点击事件回调函数。当需要为后缀图标绑定点击事件并执行自定义操作时传入此回调函数（如触发特定功能、打开弹窗等）。点击后缀图标时调用此回调函数。默认值：undefined，不设定后缀图标事件。不传入或传入undefined时，点击后缀图标无自定义响应。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config: ChipV2SuffixImageIconConfig)
```

ChipV2SuffixImageIcon的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipV2SuffixImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2suffiximageiconconfig-i.md) | 是 | 后缀图标属性配置，用于设置后缀Image图标的显示属性、无障碍功能和点击事件，继承自ChipV2ImageIconConfig和 ChipV2AccessibilityConfig，包含src、size、accessibilityLevel、action等配置项。 |

## accessibilityDescription

```TypeScript
public accessibilityDescription?: ResourceStr
```

无障碍描述。此描述用于向用户详细解释当前组件，开发人员应提供详尽的文本说明，以协助用户理解即将执行的操作及其后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果组件同时具备文本属性和无障碍说明属性，当组件被选中 时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
public accessibilityLevel?: string
```

无障碍重要性。用于控制后缀图标是否可被无障碍辅助服务所识别。支持的值为："auto"：当前组件会转换为"yes"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。默认值："auto"值为undefined时，按默认值处理。

**类型：** string

**默认值：** auto

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
public accessibilityText?: ResourceStr
```

无障碍文本属性。当组件无文本属性时，屏幕朗读选中此组件不会播报，导致使用者无法清楚了解当前选中的组件。开发人员可为此类组件设置无障碍文本，屏幕朗读时将播报该文本，帮助使用者明确选中了什么组件。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
