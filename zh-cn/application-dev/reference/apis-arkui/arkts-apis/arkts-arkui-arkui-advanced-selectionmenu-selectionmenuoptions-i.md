# SelectionMenuOptions

```TypeScript
export interface SelectionMenuOptions
```

SelectionMenuOptions定义SelectionMenu的可选菜单类型项及其配置参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## onCopy

```TypeScript
onCopy?: (event?: EditorEventInfo) => void
```

替代内置系统菜单复制项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置复制功能。

**说明：** 

event为返回信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | 否 |  |

## onCut

```TypeScript
onCut?: (event?: EditorEventInfo) => void
```

替代内置系统菜单剪切项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置剪切功能。

**说明：** 

event为返回信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | 否 |  |

## onPaste

```TypeScript
onPaste?: (event?: EditorEventInfo) => void
```

替代内置系统菜单粘贴项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置粘贴功能。

**说明：** 

event为返回信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | 否 |  |

## onSelectAll

```TypeScript
onSelectAll?: (event?: EditorEventInfo) => void
```

替代内置系统菜单全选项的事件回调。

生效前提是一定要有controller参数，有系统默认菜单才能替换内置全选功能。

**说明：** 

event为返回信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EditorEventInfo](arkts-arkui-arkui-advanced-selectionmenu-editoreventinfo-i.md) | 否 |  |

## backgroundSystemMaterial

```TypeScript
backgroundSystemMaterial?: uiMaterial.Material
```

菜单背景板使用的系统材质，用于实现菜单背景的视觉效果（如模糊、透明度等）。不同系统材质包含不同的属性，影响最终的显示效果。具体材质类型及属性请参考[uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)。默认值：undefined，无材质效果。

**类型：** [uiMaterial.Material](arkts-arkui-uimaterial-material-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: RichEditorController
```

富文本控制器不为空时显示默认系统菜单（包含剪切复制粘贴等部分）且默认菜单功能内置。

controller为空时不显示更多按钮，expandedMenuOptions参数不为空则在下拉菜单中显示。

系统默认只支持复制粘贴富文本内容，图文混排需要应用自定义onCopy、onPaste接口。应用自行配置onCopy | onPaste接口时，系统菜单默认复制粘贴失效，调用应用自定义函数。

**说明：** 

点击自定义文本选择菜单内置复制功能选项后，自定义菜单消失选中文本高亮保留。

点击自定义文本选择菜单内置全选功能选项后，自定义菜单消失文本全选高亮。

点击自定义文本选择菜单内置粘贴功能选项后，空白处粘贴或者选中文本替换粘贴均是保留被复制文本的样式。

当富文本组件[RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md#rich_editor)的copyOptions属性设置为`CopyOptions.None`时，内置的复制剪切功能会被限制。

**类型：** [RichEditorController](../arkts-components/arkts-arkui-richeditor-comp-richeditorcontroller-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editorMenuOptions

```TypeScript
editorMenuOptions?: Array<EditorMenuOptions>
```

编辑菜单。

editorMenuOptions未配置时，不显示编辑菜单。

同时配置EditorMenuOptions中action和builder时，点击图标会同时响应。

点击编辑菜单图标默认不关闭整个菜单，应用可以通过action接口配置RichEditorController的closeSelectionMenu主动关闭菜单。

**类型：** Array&lt;[EditorMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-editormenuoptions-i.md)&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expandedMenuOptions

```TypeScript
expandedMenuOptions?: Array<ExpandedMenuOptions>
```

扩展下拉菜单。

expandedMenuOptions参数为空时无更多按钮，不显示扩展下拉菜单。

expandedMenuOptions参数不为空时显示更多按钮，配置菜单项收起在更多按钮中，点击更多按钮展示。

controller为空时不显示更多按钮，expandedMenuOptions参数不为空则在下拉菜单中显示。

**类型：** Array&lt;[ExpandedMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-expandedmenuoptions-i.md)&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
