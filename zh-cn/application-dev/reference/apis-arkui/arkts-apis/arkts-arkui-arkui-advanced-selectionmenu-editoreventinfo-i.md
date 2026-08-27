# EditorEventInfo

选中内容信息。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## content

```TypeScript
content?: RichEditorSelection
```

选中的内容信息，包含选中的文本或图片片段（spans）及选择范围（selection）。

**类型：** [RichEditorSelection](../arkts-components/arkts-arkui-richeditorselection-i.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
