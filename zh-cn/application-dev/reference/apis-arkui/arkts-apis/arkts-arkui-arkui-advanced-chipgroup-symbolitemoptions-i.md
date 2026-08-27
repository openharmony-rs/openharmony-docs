# SymbolItemOptions

ChipGroup的后缀图标选项类型。

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action: VoidCallback
```

尾部图标响应事件，用户点击尾部图标时触发回调。当需要为尾部图标添加自定义交互功能时设置此参数，如执行特定操作、打开界面等。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

尾部图标的无障碍描述。此描述用于向用户详细解释尾部图标，开发人员应为尾部图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果，特别是当这些后果无法仅从尾部图标的属性和无障碍文本中直接获知时。如果尾部 图标同时具备文本属性和无障碍说明属性，当尾部图标被选中时，系统将首先播报尾部图标的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

尾部图标无障碍重要性。用于控制尾部图标是否可被无障碍辅助服务所识别。当需要为无障碍辅助服务用户提供访问支持，或需要将装饰性图标从无障碍树中排除时设置此参数。支持的值为："auto"：尾部图标转化为“yes”，适用于大多数场景。"yes"：尾部图标可被无障碍辅助服务所识别，适用于需要明确启用无障碍访问的场景。"no"：尾部图标不可被无障碍辅助服务所识别，适用于纯装饰性图标的场景。"no-hide-descendants"：尾部图标及其所有子组件不可被无障碍辅助服务所识别，适用于需要隐藏整个区域的场景。默认值："auto"。值为undefined时，按默认值处理。

**类型：** string

**默认值：** "auto"

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

尾部图标的无障碍文本属性。用于为用户进一步说明尾部图标，开发人员可为尾部图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从尾部图标本身属性与无障碍 文本中了解到时。若尾部图标既拥有文本属性又拥有无障碍说明属性，则尾部图标被选中时，先播报尾部图标的文本属性，再播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbol

```TypeScript
symbol: SymbolGlyphModifier
```

尾部图标的SymbolGlyphModifier配置对象，用于设置图标的显示样式、渲染模式等。

**类型：** SymbolGlyphModifier

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
