# @ohos.arkui.components.SelectionContainer

## 导入模块

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | 支持[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)。 |
| [SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md) | SelectionContainer组件的控制器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [SelectionContainerEditMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainereditmenuoptions-i.md) | SelectionContainer自定义编辑菜单选项。 |
| [SelectionContainerInterface](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerinterface-i.md) | 创建一个SelectionContainer组件。 |
| [SelectionContainerMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainermenuoptions-i.md) | 配置选择菜单中的选项。 |
| [SelectionContainerOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontaineroptions-i.md) | 组件初始化配置项。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SelectionContainerTextJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainertextjoinstyle-e.md) | 文本聚合拼接方式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnMenuItemClickWithTextCallback](arkts-arkui-onmenuitemclickwithtextcallback-t.md) | 点击菜单项时触发，可拦截系统默认菜单项（如复制、粘贴菜单项）的执行行为。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [SelectionContainer](arkts-arkui-arkui-components-selectioncontainer-con.md) | SelectionContainer组件用于为多个文本节点提供跨节点文本选中、复制及菜单扩展能力，支持统一配置选中文本的手柄颜色和底板颜色，支持灵活的文本拼接策略，支持自定义选择菜单和扩展菜单选项。适用于需要跨多个Text组件实现文本连续选中、统一复制、样式自定义及菜单扩展的场景，解决了多Text组件场景下文本选择体验割裂的问题，提升了用户在复杂文本布局中的交互体验。 |
| [SelectionContainerInstance](arkts-arkui-arkui-components-selectioncontainer-con.md#selectioncontainerinstance) | 定义SelectionContainer组件实例。 |

## 示例

```TypeScript
### 示例1（跨节点选中文本并复制）

该示例通过[SelectionContainer](#接口)、copyOption、[textJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md#textjoinstyle)、onTextSelectionChange、onWillCopy、onCopy接口展示跨多个Text组件选中文本、拼接选中文本并处理复制回调的能力。

从API版本26.0.0开始，新增SelectionContainer组件和copyOption等接口。


```

```TypeScript
### 示例2（绑定自定义选择菜单）

该示例通过bindSelectionMenu接口实现了跨节点选中文本时绑定自定义菜单的功能。

从API版本26.0.0开始，新增bindSelectionMenu属性。


```

```TypeScript
### 示例3（扩展菜单选项）

该示例通过editMenuOptions接口实现了去除系统菜单中的翻译和搜索菜单项，并添加5个自定义菜单项的功能。同时在[onMenuItemClick](arkts-arkui-onmenuitemclickwithtextcallback-t.md)回调中展示拦截系统复制操作（return true）和不拦截全选操作（return false）的差异。

从API版本26.0.0开始，新增editMenuOptions属性。


```

```TypeScript
### 示例4（通过控制器关闭选择菜单与清除文本选中）

该示例通过[SelectionContainer](#接口)传入[SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md)，调用closeSelectionMenu和[clearTextSelection](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md#cleartextselection)接口展示关闭选择菜单和清除选中文本的能力。

从API版本26.0.0开始，新增[SelectionContainerController](arkts-arkui-arkui-components-selectioncontainer-selectioncontainercontroller-c.md)和[SelectionContainerOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontaineroptions-i.md)接口。
```
