# SelectionMenuOptions

SelectionMenuOptions定义SelectionMenu的可选菜单类型项及其具体配置参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

菜单的背景板的系统材质。不同系统材质包含不同的属性影响效果。默认值：undefined，无材质效果。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: RichEditorController
```

扩展下拉菜单。

expandedMenuOptions参数为空时无更多按钮，不显示扩展下拉菜单。

expandedMenuOptions参数不为空时显示更多按钮，配置菜单项收起在更多按钮中，点击更多按钮展示。

**类型：** RichEditorController

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editorMenuOptions

```TypeScript
editorMenuOptions?: Array<EditorMenuOptions>
```

编辑菜单。

editorMenuOptions未配置时，不显示编辑菜单。

同时配置EditorMenuOptions中action和builder时，点击图标会同时响应。

点击编辑菜单图标默认不关闭整个菜单，应用可以通过action接口配置RichEditorController的closeSelectionMenu主动关闭菜单。

**类型：** Array<EditorMenuOptions>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expandedMenuOptions

```TypeScript
expandedMenuOptions?: Array<ExpandedMenuOptions>
```

扩展下拉菜单。

expandedMenuOptions参数为空时无更多按钮，不显示扩展下拉菜单。

expandedMenuOptions参数不为空时显示更多按钮，配置菜单项收起在更多按钮中，点击更多按钮展示。

**类型：** Array<ExpandedMenuOptions>

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCopy

```TypeScript
onCopy?: (event?: EditorEventInfo) => void
```

替代内置系统菜单复制项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置复制功能。

**说明：**

event为返回信息。

**类型：** (event?: EditorEventInfo) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCut

```TypeScript
onCut?: (event?: EditorEventInfo) => void
```

替代内置系统菜单剪切项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置剪切功能。

**说明：**

event为返回信息。

**类型：** (event?: EditorEventInfo) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPaste

```TypeScript
onPaste?: (event?: EditorEventInfo) => void
```

替代内置系统菜单粘贴项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置粘贴功能。

**说明：**

event为返回信息。

**类型：** (event?: EditorEventInfo) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onSelectAll

```TypeScript
onSelectAll?: (event?: EditorEventInfo) => void
```

替代内置系统菜单全选项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置全选功能。

**说明：**

event为返回信息。

**类型：** (event?: EditorEventInfo) => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

