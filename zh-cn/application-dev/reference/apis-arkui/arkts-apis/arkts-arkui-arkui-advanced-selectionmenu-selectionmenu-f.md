# SelectionMenu

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## SelectionMenu

```TypeScript
export declare function SelectionMenu(options: SelectionMenuOptions): void
```

入参为空时，文本选择菜单组件SelectionMenu内容区大小及组件大小为零。例如，富文本组件RichEditor使用 bindSelectionMenu接口绑定一个SelectionMenu的右键菜单，则右键富文本组件区域时无任何菜单弹出。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SelectionMenuOptions](arkts-arkui-arkui-advanced-selectionmenu-selectionmenuoptions-i.md) | 是 | 文本选择菜单配置选项，用于配置编辑菜单、扩展下拉菜单、富文本控制器以及复制粘贴剪切等回调事件。 |
