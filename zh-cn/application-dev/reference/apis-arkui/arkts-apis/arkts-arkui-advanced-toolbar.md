# @ohos.arkui.advanced.ToolBar

## 导入模块

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md) | ToolBarModifier提供设置工具栏高度(height)、背景色(backgroundColor)、左右内边距（padding，仅在子项数量小于5个时生效）、是否显示按压态（stateEffect）的方法。 |
| [ToolBarOption](arkts-arkui-arkui-advanced-toolbar-toolbaroption-c.md) | 定义工具栏的列表内容和属性。 |
| [ToolBarOptions](arkts-arkui-arkui-advanced-toolbar-toolbaroptions-c.md) | 继承于 Array&lt;[ToolBarOption](arkts-arkui-arkui-advanced-toolbar-toolbaroption-c.md)&gt;。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ToolBar](arkts-arkui-arkui-advanced-toolbar-toolbar-s.md) | 工具栏组件，用于展示针对当前界面内容的操作选项，在界面底部显示。适用于需要为用户提供快捷操作入口的场景，如编辑页面的复制、粘贴、分享等操作。底部最多显示5个入口，超过则收纳入“更多”子项中，在最右侧显示。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ToolBarSymbolGlyphOptions](arkts-arkui-arkui-advanced-toolbar-toolbarsymbolglyphoptions-i.md) | ToolBarSymbolGlyphOptions定义图标的属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ItemState](arkts-arkui-arkui-advanced-toolbar-itemstate-e.md) | 定义工具栏子项的当前状态。 |
