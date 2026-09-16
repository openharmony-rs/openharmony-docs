# @ohos.arkui.advanced.EditableTitleBarV2

## 导入模块

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [EditableLeftIconV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2-c.md) | 左侧图标配置类，使用@ObservedV2装饰器，支持状态观察。 |
| [EditableSaveButtonV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2-c.md) | 保存按钮配置类，使用@ObservedV2装饰器，支持状态观察。 |
| [EditableTitleBarMenuItemV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2-c.md) | 菜单项配置类。 |
| [EditableTitleBarStyleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2-c.md) | 标题栏样式配置类，使用@ObservedV2装饰器，支持状态观察。 |
| [EditableTitleV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2-c.md) | 标题配置类。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBarV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarv2-s.md) | 编辑型标题栏，适用于多选界面或内容编辑界面，一般采取左叉右勾的形式。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EditableLeftIconV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2options-i.md) | 左侧图标配置选项接口。 |
| [EditableSaveButtonV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editablesavebuttonv2options-i.md) | 保存按钮配置选项接口。 |
| [EditableTitleBarMenuItemV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarmenuitemv2options-i.md) | 菜单项配置选项接口。 |
| [EditableTitleBarStyleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2options-i.md) | 标题栏样式配置选项接口。 |
| [EditableTitleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2options-i.md) | 标题配置选项接口。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EditableLeftIconTypeV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticontypev2-e.md) | 左侧图标类型枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EditableTitleBarItemV2](arkts-arkui-editabletitlebaritemv2-t.md) | 左侧图像项类型别名。 |
| [EditableTitleBarItemV2Options](arkts-arkui-editabletitlebaritemv2options-t.md) | 左侧图像项配置选项类型别名。 |
| [OnActionCallback](arkts-arkui-onactioncallback-t.md) | 点击事件的回调函数类型。 |

## 示例

```TypeScript
### 示例1（右侧图标自定义标题栏）

本示例通过EditableTitleBarV2接口实现了编辑型标题栏左侧图标、主标题及自定义右侧图标区内容的展示。

从API版本26.0.0开始，支持EditableTitleBarV2。


```

```TypeScript
### 示例2（头像与背景模糊标题栏）

本示例通过EditableTitleBarV2接口leftIcon、title、saveButton等，实现了编辑型标题栏设置背景模糊、头像、取消右侧保存图标及自定义标题栏外边距的功能。

从API版本26.0.0开始，支持EditableTitleBarV2。


```

```TypeScript
### 示例3（右侧自定义按钮播报）

本示例通过EditableTitleBarV2接口右侧自定义按钮属性接口accessibilityText、accessibilityDescription等，实现了编辑型标题栏屏幕朗读播报文本内容的自定义功能。

从API版本26.0.0开始，支持EditableTitleBarV2。


```

```TypeScript
### 示例4（左侧图标设置为默认焦点）

在获焦状态下，本示例通过EditableTitleBarV2接口配置[EditableLeftIconV2](arkts-arkui-arkui-advanced-editabletitlebarv2-editablelefticonv2-c.md)的defaultFocus属性，实现了编辑型标题栏左侧图标默认获焦功能。

从API版本26.0.0开始，支持EditableTitleBarV2。


```

```TypeScript
### 示例5（右侧自定义图标设置为默认焦点）

在获焦状态下，本示例通过EditableTitleBarV2的右侧图标属性defaultFocus，实现了编辑型标题栏右侧图标默认获焦功能。

从API版本26.0.0开始，支持EditableTitleBarV2。


```

```TypeScript
### 示例6（设置Symbol类型图标）

本示例通过EditableTitleBarV2接口symbolStyle，实现了编辑型标题栏自定义Symbol类型图标功能。

从API版本26.0.0开始，支持EditableTitleBarV2。
```
