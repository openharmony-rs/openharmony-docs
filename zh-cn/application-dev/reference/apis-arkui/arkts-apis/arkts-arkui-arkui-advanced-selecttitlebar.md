# @ohos.arkui.advanced.SelectTitleBar

## 导入模块

```TypeScript
import { SelectTitleBar, SelectTitleBarMenuItem } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SelectTitleBarMenuItem](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebarmenuitem-c.md) | Declaration of the menu item on the right side. |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [SelectTitleBar](arkts-arkui-arkui-advanced-selecttitlebar-selecttitlebar-s.md) | 下拉菜单标题栏是一个包含下拉菜单的标题栏组件，支持页面间的快速切换，可配置返回按钮和右侧菜单项。该组件适用于需要在不同视图或页面间进行导航切换的场景，支持一级页面、二级及其以上界面。使用该组件可以方便用户快速访问和切换不同的内容视图，提升页面导航的便捷性和用户体验。 |

## 示例

```TypeScript
### 示例1（下拉菜单标题栏）

该示例实现了简单的下拉菜单标题栏，带有返回箭头的下拉菜单标题栏和带有右侧菜单项目列表的下拉菜单标题栏。


```

```TypeScript
### 示例2（右侧自定义按钮播报）

从API version 18开始，该示例通过设置标题栏右侧自定义按钮属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API version 18开始，该示例通过设置SelectTitleBarMenuItem的属性symbolStyle，展示了自定义Symbol类型图标。
```
