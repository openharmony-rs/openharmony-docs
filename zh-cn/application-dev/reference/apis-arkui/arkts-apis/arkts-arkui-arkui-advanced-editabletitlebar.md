# @ohos.arkui.advanced.EditableTitleBar

## 导入模块

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md) |  |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBar](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebar-s.md) | 编辑型标题栏组件，提供标准的编辑界面标题栏实现，支持自定义左侧按钮类型（返回/取消）、头像显示、右侧菜单项、背景模糊样式等功能。适用于需要进行内容编辑、多选操作的场景，如相册多选编辑、文本编辑器、表单编辑等界面。该组件封装了编辑场景常用的UI交互模式（左叉右勾），开发者无需自行实现标题栏布局和交互逻辑，可快速构建符合设计规范的编辑界面，提升开发效率并保证UI一致性。同时支持无障碍属性配置，满足可访问性要求。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBarOptions](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebaroptions-i.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EditableLeftIconType](arkts-arkui-arkui-advanced-editabletitlebar-editablelefticontype-e.md) |  |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBarItem](arkts-arkui-editabletitlebaritem-t.md) | Declaration of the image item . |

## 示例

```TypeScript
### 示例1（右侧图标自定义标题栏）

该示例主要演示EditableTitleBar设置左侧图标、主标题及自定义右侧图标区的效果。


```

```TypeScript
### 示例2（头像与背景模糊标题栏）

该示例主要演示EditableTitleBar设置背景模糊、头像、取消右侧保存图标及自定义标题栏外边距的效果。


```

```TypeScript
### 示例3（右侧自定义按钮播报）

从API version 18开始，该示例通过设置标题栏的右侧自定义按钮属性accessibilityText、accessibilityDescription、accessibilityLevel自定义屏幕朗读播报文本。


```

```TypeScript
### 示例4（左侧图标设置为默认焦点）

在获焦状态下，该示例通过设置标题栏属性leftIconDefaultFocus使左侧图标默认获焦。

从API version 18开始，在[EditableTitleBar](#editabletitlebar-1)中新增leftIconDefaultFocus接口。


```

```TypeScript
### 示例5（右侧自定义图标设置为默认焦点）

在获焦状态下，该示例通过设置标题栏右侧图标属性defaultFocus使右侧图标默认获焦。

从API version 18开始，在[EditableTitleBarMenuItem](arkts-arkui-arkui-advanced-editabletitlebar-editabletitlebarmenuitem-c.md)中新增defaultFocus接口。


```

```TypeScript
### 示例6（设置Symbol类型图标）

从API version 18开始，该示例通过设置EditableTitleBarMenuItem的属性symbolStyle，展示了自定义Symbol类型图标。
```
