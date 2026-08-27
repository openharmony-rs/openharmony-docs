# IconItemOptions

定义了尾部builder接口，用于配置尾部图标及其背景区域的显示属性。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

后缀图标的无障碍描述。此描述用于向用户详细解释后缀图标，开发人员应为后缀图标的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果，特别是当这些后果无法仅从后缀图标的属性和无障碍文本中直接获知时。如果后缀 图标同时具备文本属性和无障碍说明属性，当后缀图标被选中时，系统将首先播报后缀图标的文本属性，随后播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

后缀图标无障碍重要性。用于控制后缀图标是否可被无障碍辅助服务所识别。当需要为无障碍辅助服务用户提供访问支持，或需要将装饰性图标从无障碍树中排除时设置此参数。支持的值为："auto"：后缀图标存在action时转化为“yes”，不存在action时，转化为“no”，适用于大多数场景。"yes"：后缀图标可被无障碍辅助服务所识别，适用于功能性图标。"no"：后缀图标不可被无障碍辅助服务所识别，适用于纯装饰性图标。"no-hide-descendants"：后缀图标及其所有子组件不可被无障碍辅助服务所识别，适用于需要隐藏整个区域的场景。默认值："auto"值为undefined时，按默认值处理。

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

后缀图标的无障碍文本属性。用于为用户进一步说明后缀图标，开发人员可为后缀图标的该属性设置相对较详细的解释文本，帮助用户理解将要执行的操作。如帮助用户理解将要执行的操作可能导致什么后果，尤其是当这些后果无法从后缀图标本身属性与无障碍 文本中了解到时。若后缀图标既拥有文本属性又拥有无障碍说明属性，则后缀图标被选中时，先播报后缀图标的文本属性，再播报无障碍说明属性的内容。默认值：空字符串。值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: Callback<void>
```

尾部图标点击事件回调，用户点击尾部图标时触发。当需要为尾部图标添加自定义交互功能时设置此参数，如执行特定操作、打开界面等。为undefined时，不触发该回调。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: IconOptions
```

自定义Builder icon。Chip大小是ChipSize.SMALL时，icon的size默认值：{width: '16vp',height: '16vp'}。Chip大小是ChipSize.NORMAL时，icon的size默认值：{width: '24vp',height: '24vp'}。如果想动态修改size，那么必须在引入[IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroup-icongroupsuffix-s.md)时，使用 [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-c.md)类型。值为undefined时，按默认值处理。

**类型：** [IconOptions](arkts-arkui-arkui-advanced-chipgroup-iconoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
