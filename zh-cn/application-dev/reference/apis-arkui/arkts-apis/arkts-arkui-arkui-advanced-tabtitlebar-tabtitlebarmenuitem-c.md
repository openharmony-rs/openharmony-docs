# TabTitleBarMenuItem

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { TabTitleBar, TabTitleBarMenuItem, TabTitleBarTabItem } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

点击菜单项时触发的动作闭包。若不设置，点击菜单项无响应。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

标题栏右侧自定义按钮的无障碍描述。此描述用于向用户详细解释当前组件，开发人员应为组件的这一属性提供较为详尽的文本说明，以协助用户理解即将执行的操作及其可能产生的后果。特别是当这些后果无法仅从组件的属性和无障碍文本中直接获知时。如果 组件同时具备文本属性和无障碍说明属性，当组件被选中时，系统将首先播报组件的文本属性，随后播报无障碍说明属性的内容。默认值为“单指双击即可执行”。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

标题栏右侧自定义按钮无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。支持的值为："auto"：根据组件是否可交互自动判断。若组件可交互，则等同于"yes"；若组件不可交互，则等同于"no"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。默认值："auto"。

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

标题栏右侧自定义按钮的无障碍文本属性，用于为不包含文字信息的组件提供朗读文本。默认值：设置了label属性时，默认值为当前项label属性内容；未设置label属性时，默认值为空格字符。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

是否启用。true：启用，false：禁用。禁用时菜单项不响应点击事件，action不会触发。默认值：false

**类型：** boolean

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

图标标签，用于为菜单项图标提供文字说明。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源，优先级大于value。当需要使用Symbol图标时传入此参数，不传入时使用value参数设置的图标。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

图标资源。若设置了symbolStyle，则该属性不生效。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
