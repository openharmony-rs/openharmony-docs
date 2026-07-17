# SuffixIconOptions

SuffixIconOptions定义后缀图标的属性。

继承于[IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md)。

**继承/实现关系：** SuffixIconOptions extends [IconCommonOptions](arkts-arkui-arkui-advanced-chip-iconcommonoptions-i.md)

**起始版本：** 11

<!--Device-unnamed-export interface SuffixIconOptions extends IconCommonOptions--><!--Device-unnamed-export interface SuffixIconOptions extends IconCommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SuffixIconOptions, CloseOptions, ChipSymbolGlyphOptions, Chip, AccessibilitySelectedType, LabelMarginOptions, LabelOptions, PrefixIconOptions, IconCommonOptions, ChipOptions, ChipSuffixSymbolGlyphOptions, ChipSize, AccessibilityOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

后缀图标的无障碍描述。此描述用于向用户详细解释后缀图标，开发人员应为后缀图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从后缀图标的属性和无障碍文本中直接获知时。如果后缀图标同时具备文本属性和无障碍说明属性，当后缀图标被选中时，系统将首先播报后缀图标的文本属性，随后播报无障碍说明属性的内容。

默认值：''

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SuffixIconOptions-accessibilityDescription?: ResourceStr--><!--Device-SuffixIconOptions-accessibilityDescription?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

后缀图标的无障碍重要性。用于控制后缀图标是否可被无障碍辅助服务识别。

支持的值为:

"auto"：当前组件存在action时转化为"yes"，不存在action时，转化为"no"。

"yes"：当前组件可被无障碍辅助服务所识别。

"no"：当前组件不可被无障碍辅助服务所识别。

"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。

默认值："auto"。

值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SuffixIconOptions-accessibilityLevel?: string--><!--Device-SuffixIconOptions-accessibilityLevel?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

后缀图标无障碍文本属性。当后缀图标不包含文本属性时，屏幕朗读选中后缀图标时不播报，使用者无法清楚地知道当前是否选中了后缀图标。为了解决此场景，开发人员可为不包含文字信息的后缀图标设置无障碍文本，当屏幕朗读选中后缀图标时播报无障碍文本的内容，帮助屏幕朗读的使用者清楚地知道自己是否选中了后缀图标。

默认值：''

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-SuffixIconOptions-accessibilityText?: ResourceStr--><!--Device-SuffixIconOptions-accessibilityText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

后缀图标设定事件。

值为undefined时，不设定后缀图标事件。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SuffixIconOptions-action?: () => void--><!--Device-SuffixIconOptions-action?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

