# ToolBarOption

定义工具栏的列表内容和属性。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

工具栏子项点击事件。不传入时点击子项不会触发任何操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityDescription

```TypeScript
accessibilityDescription?: ResourceStr
```

工具栏子项的无障碍描述。用于向用户详细解释当前组件的功能和操作后果，特别是当这些信息无法仅从组件文本直接获知时。组件被选中时，将依次播报文本属性和无障碍说明属性的内容。默认值为“单指双击即可执行”。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilityLevel

```TypeScript
accessibilityLevel?: string
```

工具栏子项无障碍重要性。用于控制当前项是否可被无障碍辅助服务所识别。支持的值为："auto"：当前组件会转换为"yes"。"yes"：当前组件可被无障碍辅助服务所识别。"no"：当前组件不可被无障碍辅助服务所识别。"no-hide-descendants"：当前组件及其所有子组件不可被无障碍辅助服务所识别。默认值："auto"

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

工具栏子项的无障碍文本属性。当组件不包含文本属性时，屏幕朗读选中此组件时不播报。开发人员可为不包含文字信息的组件设置无障碍文本，使屏幕朗读选中此组件时播报该文本内容。默认值为当前项content属性内容。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedIconColor

```TypeScript
activatedIconColor?: ResourceColor
```

工具栏子项激活态的图标填充颜色。默认值为\$r('sys.color.icon_emphasize')。当设置了toolBarSymbolOptions属性时，该参数不生效。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedTextColor

```TypeScript
activatedTextColor?: ResourceColor
```

工具栏子项激活态的文本颜色。默认值为\$r('sys.color.font_emphasize')。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

工具栏子项的文本。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: Resource
```

工具栏子项的图标。默认不设置或者设置为undefined，图标不显示。当设置了toolBarSymbolOptions属性时，icon属性将不生效。

**类型：** Resource

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconColor

```TypeScript
iconColor?: ResourceColor
```

工具栏子项的图标填充颜色。默认值为\$r('sys.color.icon_primary')。当设置了toolBarSymbolOptions属性时，该参数不生效。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state?: ItemState
```

工具栏子项的状态。默认为ItemState.ENABLE。

**类型：** [ItemState](arkts-arkui-arkui-advanced-toolbar-itemstate-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textColor

```TypeScript
textColor?: ResourceColor
```

工具栏子项的文本颜色。默认值为\$r('sys.color.font_primary')。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toolBarSymbolOptions

```TypeScript
toolBarSymbolOptions?: ToolBarSymbolGlyphOptions
```

工具栏子项的图标属性，symbol类型。设置此参数后，icon属性将不生效。

**类型：** [ToolBarSymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbar-toolbarsymbolglyphoptions-i.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
