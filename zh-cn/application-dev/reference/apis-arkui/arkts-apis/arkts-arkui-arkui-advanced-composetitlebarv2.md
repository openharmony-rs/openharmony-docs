# @ohos.arkui.advanced.ComposeTitleBarV2

## 导入模块

```TypeScript
import { ComposeTitleBarV2, ComposeTitleBarV2MenuItem, ComposeTitleBarV2MenuItemParams } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ComposeTitleBarV2MenuItem](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitem-c.md) | 菜单项类，用于定义标题栏左侧头像或右侧菜单项。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ComposeTitleBarV2](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2-s.md) | ComposeTitleBarV2组件是一种标题栏，支持设置标题、头像（可选）和副标题（可选），可用于一级页面、二级及其以上界面配置返回键。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ComposeTitleBarV2MenuItemParams](arkts-arkui-arkui-advanced-composetitlebarv2-composetitlebarv2menuitemparams-i.md) | 菜单项参数接口，用于创建ComposeTitleBarV2MenuItem实例。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | 点击菜单项时触发的回调函数类型。 |

## 示例

```TypeScript
### 示例1（简单的标题栏）

从API版本26.0.0开始，可以使用ComposeTitleBarV2接口实现简单的标题栏，该示例展示了ComposeTitleBarV2的基本用法。


```

```TypeScript
### 示例2（右侧自定义按钮播报）

从API版本26.0.0开始，通过设置标题栏右侧自定义按钮的以下属性接口accessibilityText、accessibilityDescription、accessibilityLevel，实现自定义屏幕朗读播报文本。


```

```TypeScript
### 示例3（设置Symbol类型图标）

从API版本26.0.0开始，通过设置ComposeTitleBarV2MenuItem的属性接口symbolStyle，实现Symbol类型图标的配置。
```
