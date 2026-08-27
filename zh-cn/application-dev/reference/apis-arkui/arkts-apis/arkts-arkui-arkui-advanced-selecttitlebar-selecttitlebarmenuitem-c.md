# SelectTitleBarMenuItem

Declaration of the menu item on the right side.

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

右侧自定义按钮被点击时执行的回调函数。开发者可在此定义按钮点击后需要执行的自定义操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

标题栏右侧自定义按钮的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如 果组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。默认值为“单指双击即可执行”。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

标题栏右侧自定义按钮无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。支持的值为："auto"：当前组件根据具体情况自动转换为"yes"或"no"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。默认值："auto"。

**类型：** string

**默认值：** "auto"

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityText

```TypeScript
accessibilityText?: ResourceStr
```

标题栏右侧自定义按钮的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报，使用者无法清楚地知道当前选中了什么组件。为了解决此场景，开发人员可为不包含文字信息的组件设置无障碍文本，当屏幕朗读选中此组件时播报无障碍文本 的内容，帮助屏幕朗读的使用者清楚地知道自己选中了什么组件。默认值：设置了label时默认值为当前项label属性内容，未设置label时默认值为空格字符。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

是否启用。默认值：false。true：启用该菜单项，false：禁用该菜单项（置灰且不可点击）。

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

图标标签描述，可作为accessibilityText的默认值。同时设置label和accessibilityText时，accessibilityText优先级更高。不设置时，默认无标签。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源，优先级大于value。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

图标资源，用于设置标题栏右侧菜单项的图标，支持通过\$r引用资源。当同时设置symbolStyle时，symbolStyle优先。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
