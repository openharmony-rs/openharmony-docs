# FrameNode

typeNode提供创建具体类型的FrameNode能力，可通过FrameNode的基础接口进行自定义的挂载，使用占位容器进行显示。适用于需要通过代码动态创建具体类型组件节点并进行自定义挂载的场景。 使用typeNode创建Text、Image、 Select、Toggle节点时，当传入的 [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#UIContext)对应的UI实例销毁后，调用该接口会返回一个无效的FrameNode节点，无法正常挂载和显示。

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FrameNode](arkts-arkui-framenode-c.md) | FrameNode表示组件树的实体节点，支持节点树操作、自定义绘制与布局、位置查询、动画等能力。[NodeController](../../apis-na/arkts-apis/arkts-na-nodecontroller-c.md#NodeController)可通过 BuilderNode持有的FrameNode将其挂载到NodeContainer上， 也可通过FrameNode获取[RenderNode](arkts-arkui-rendernode-c.md#RenderNode)，挂载到其他FrameNode上。适用于需要通过代码动态创建和管理组件节点树的场景，可实现声明式组件无法直接满足的灵活 UI组合与自定义渲染需求。&lt;!--RP2--&gt;&lt;!--RP2End--&gt; |
| [NodeAdapter](arkts-arkui-framenode-nodeadapter-c.md) | NodeAdapter提供FrameNode的数据懒加载能力，通过LazyForEach实现接口功能。适用于长列表等需要按需加载节点数 据的场景，可提升渲染性能并降低内存占用。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-arkui-framenode-crosslanguageoptions-i.md) | 该接口用于配置或查询FrameNode的跨语言访问权限。例如，针对ArkTS语言创建的节点，可通过该接口控制是否允许通过非ArkTS语言进行属性访问或修改。 |
| [InteractionEventBindingInfo](arkts-arkui-framenode-interactioneventbindinginfo-i.md) | 组件的交互事件绑定状态信息。如果当前节点上绑定了所要查询的交互事件，调用查询接口时返回一个InteractionEventBindingInfo对象，指示事件绑定详细信息。 |
| [LayoutConstraint](arkts-arkui-framenode-layoutconstraint-i.md) | 描述组件的布局约束。 |
| [TypedFrameNode](arkts-arkui-framenode-typedframenode-i.md) | TypedFrameNode继承自[FrameNode](../../apis-na/arkts-apis/arkts-na-framenode-c.md#FrameNode)，用于声明具体类型的FrameNode，支持Text、Image、Button、Column等多种组件类型，适用于通过代码动态创建具体类型组件节 点的场景。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChildrenCountMode](arkts-arkui-framenode-childrencountmode-e.md) | 子节点计数模式枚举。用于指定获取子节点数量时的计数方式。 |
| [ExpandMode](arkts-arkui-framenode-expandmode-e.md) | 子节点展开模式枚举。 |
| [UIState](arkts-arkui-framenode-uistate-e.md) | 多态样式状态枚举，用于处理多态样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [UIStatesChangeHandler](arkts-arkui-uistateschangehandler-t.md) | 当UI状态发生变化时触发的回调。接收回调触发时的[UIState](../../apis-na/arkts-apis/arkts-na-framenode-uistate-e.md#UIState)状态，该参数的取值为UIState状态枚举值或其运算结果。 |

