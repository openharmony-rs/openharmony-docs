# FrameNode

提供用于实现 FrameNode 的方法。

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FrameNode](arkts-na-framenode-c.md) | 定义FrameNode。 |
| [NodeAdapter](arkts-na-framenode-nodeadapter-c.md) | NodeAdapter提供FrameNode的数据懒加载能力，通过LazyForEach实现接口功能。 |
| [TypedFrameNode](arkts-na-framenode-typedframenode-c.md) | TypedFrameNode继承自[FrameNode](arkts-na-framenode-framenodeoptions-i.md#framenodeoptions)，用于声明具体类型的FrameNode。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CrossLanguageOptions](arkts-na-framenode-crosslanguageoptions-i.md) | 该接口用于配置或查询FrameNode的跨语言访问权限。例如，针对ArkTS语言创建的节点，可通过该接口控制是否允许通过非ArkTS语言进行属性访问或修改。 |
| [FrameNodeOptions](arkts-na-framenode-framenodeoptions-i.md) | FrameNode选项，可设置FrameNode是否支持多线程操作。 |
| [InteractionEventBindingInfo](arkts-na-framenode-interactioneventbindinginfo-i.md) | 组件的交互事件绑定状态信息。如果当前节点上绑定了所要查询的交互事件，调用查询接口时返回一个InteractionEventBindingInfo对象，指示事件绑定详细信息。 |
| [LayoutConstraint](arkts-na-framenode-layoutconstraint-i.md) | 描述组件的布局约束。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChildrenCountMode](arkts-na-framenode-childrencountmode-e.md) | 子节点计数模式枚举。用于指定获取子节点数量时的计数方式。 |
| [ExpandMode](arkts-na-framenode-expandmode-e.md) | 子节点展开模式枚举。 |
| [UIState](arkts-na-framenode-uistate-e.md) | 多态样式状态枚举，用于处理多态样式。 .0.0 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [UIStatesChangeHandler](arkts-na-uistateschangehandler-t.md) | UI状态变化处理函数，返回当前UI状态，值为结果 的所有当前状态枚举值或计算，并且可以确定状态 通过执行&操作，如下。 如果(currentStates & UIState.PRESSED == UIState.PRESSED) 但是，请注意，对于正常的状态检查，应该直接使用equal。 如果(currentStates == UIState.NORMAL)。 |

