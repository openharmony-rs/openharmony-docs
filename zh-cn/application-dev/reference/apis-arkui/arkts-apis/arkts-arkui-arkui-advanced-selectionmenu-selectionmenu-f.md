# SelectionMenu

## 导入模块

```TypeScript
import { EditorMenuOptions, SelectionMenuOptions, EditorEventInfo, SelectionMenu, ExpandedMenuOptions } from '@kit.ArkUI';
```

<a id="selectionmenu"></a>
## SelectionMenu

```TypeScript
export declare function SelectionMenu(options: SelectionMenuOptions): void
```

入参为空时，文本选择菜单组件SelectionMenu内容区大小及组件大小为零。表现例如，富文本组件[RichEditor](../arkts-components/arkts-arkui-richeditor.md)使用[bindSelectionMenu](RichEditorAttribute#bindSelectionMenu)接口绑定一个SelectionMenu的右键菜单，则右键富文本组件区域时无任何菜单弹出。

**起始版本：** 11

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function SelectionMenu(options: SelectionMenuOptions): void--><!--Device-unnamed-export declare function SelectionMenu(options: SelectionMenuOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | 是 | 文本选择菜单可选项。 |

