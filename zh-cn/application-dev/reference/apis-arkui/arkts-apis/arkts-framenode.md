# FrameNode

typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。

使用typeNode创建[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)、[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)、[Select](../arkts-components/arkts-arkui-select.md)、[Toggle](../arkts-components/arkts-arkui-toggle.md)节点时，当传入的
[UIContext](arkts-arkui-uicontext.md)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [typeNode](arkts-arkui-typenode-n.md) | typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。使用typeNode创建[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)、[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)、[Select](../arkts-components/arkts-arkui-select.md)、[Toggle](../arkts-components/arkts-arkui-toggle.md)节点时，当传入的[UIContext](arkts-arkui-uicontext.md)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | 定义FrameNode。 |
| [NodeAdapter](arkts-arkui-nodeadapter-c.md) | NodeAdapter提供FrameNode的数据懒加载能力，通过[LazyForEach](../arkts-components/arkts-arkui-lazyforeach.md)实现接口功能。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-crosslanguageoptions-i.md) | 该接口用于配置或查询FrameNode的跨语言访问权限。例如，针对ArkTS语言创建的节点，可通过该接口控制是否允许通过非ArkTS语言进行属性访问或修改。 |
| [InteractionEventBindingInfo](arkts-arkui-interactioneventbindinginfo-i.md) | 组件的交互事件绑定状态信息。如果当前节点上绑定了所要查询的交互事件，调用查询接口时返回一个InteractionEventBindingInfo对象，指示事件绑定详细信息。 |
| [LayoutConstraint](arkts-arkui-layoutconstraint-i.md) | 描述组件的布局约束。 |
| [TypedFrameNode](arkts-arkui-typedframenode-i.md) | TypedFrameNode继承自[FrameNode](arkts-arkui-framenode-c.md)，用于声明具体类型的FrameNode。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChildrenCountMode](arkts-arkui-childrencountmode-e.md) | 子节点计数模式枚举。用于指定获取子节点数量时的计数方式。 |
| [ExpandMode](arkts-arkui-expandmode-e.md) | 子节点展开模式枚举。 |
| [UIState](arkts-arkui-uistate-e.md) | 多态样式状态枚举，用于处理多态样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | 当UI状态发生变化时触发的回调。接收回调触发时的[UIState](arkts-arkui-uistate-e.md)状态，该参数的取值为UIState状态枚举值或其运算结果。 |

