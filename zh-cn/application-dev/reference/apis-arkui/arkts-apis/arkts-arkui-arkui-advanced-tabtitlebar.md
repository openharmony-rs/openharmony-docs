# @ohos.arkui.advanced.TabTitleBar

## 导入模块

```TypeScript
import { TabTitleBar, TabTitleBarMenuItem, TabTitleBarTabItem } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [TabTitleBarMenuItem](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebarmenuitem-c.md) |  |
| [TabTitleBarTabItem](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebartabitem-c.md) | Declaration of the tab item. |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [TabTitleBar](arkts-arkui-arkui-advanced-tabtitlebar-tabtitlebar-s.md) | TabTitleBar是页签型标题栏组件，支持页签列表与关联内容的联动切换，并可配置右侧菜单项。适用于需要通过页签切换页面内容的场景，如顶部导航栏等。该组件通过页签和菜单项的灵活配置，可满足不同的交互需求。仅支持一级页面的页签切换。 |

## 示例

```TypeScript
### 示例1（简单的页签型标题栏）

该示例实现了带有左侧页签和右侧菜单列表的页签型标题栏。


```

```TypeScript
### 示例2（右侧自定义按钮播报）

从API version 18开始，该示例通过设置标题栏右侧控制按钮属性accessibilityText、accessibilityDescription、accessibilityLevel控制屏幕朗读播报文本。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置TabTitleBarTabItem、TabTitleBarMenuItem的属性symbolStyle，展示了自定义Symbol类型图标。
```
