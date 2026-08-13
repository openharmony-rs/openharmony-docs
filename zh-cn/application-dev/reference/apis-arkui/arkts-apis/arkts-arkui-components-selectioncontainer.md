# @ohos.arkui.components.SelectionContainer

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | 支持[通用属性](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)。 支持[通用事件](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)。 |
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
| [SelectionContainer](arkts-arkui-arkui-components-selectioncontainer-con.md#SelectionContainer) | SelectionContainer组件用于为多个文本节点提供跨节点文本选中、复制及菜单扩展能力，支持统一配置选中文本的手柄颜色和底板颜色，支持灵活的文本拼接策略，支持自定义选择菜单和扩展菜单选项。适用于需要跨多个Text组件实现文本 连续选中、统一复制、样式自定义及菜单扩展的场景，解决了多Text组件场景下文本选择体验割裂的问题，提升了用户在复杂文本布局中的交互体验。 @internal/component/ets/text}组件的从上到下显示顺序进行拼接。 > > - 本组件默认布局走Stack，如有其他容器布局需求请在SelectionContainer内放置一个容器组件。 > > - SelectionContainer内跨节点选中文本时不显示放大镜，也不支持[getMagnifier](arkts-arkui-arkui-uicontext-uicontext-c.md#getMagnifier)主动设置放大镜。 > > - 仅Text组件中的文本内容参与跨节点选中与文本拼接。 |
| [SelectionContainerInstance](arkts-arkui-arkui-components-selectioncontainer-con.md#SelectionContainerInstance) | 定义SelectionContainer组件实例。 |

