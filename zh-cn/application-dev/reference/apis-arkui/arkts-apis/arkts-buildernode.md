# BuilderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | class BuilderNode\&lt;Args extends Object[]&gt;<br/><br/>BuilderNode支持通过无状态的UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)生成组件树，并持有组件树的根节点。不支持定义为状态变量。<br/>BuilderNode中持有的FrameNode仅用于将该BuilderNode作为子节点挂载到其他FrameNode上。对BuilderNode持有的FrameNode进行属性设置与子节点操作可能会产生未定义行为，因此不建议通过<br/>BuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getFrameNode-1)方法和[FrameNode](arkts-arkui-framenode-c.md#FrameNode)的<br/>[getRenderNode](arkts-arkui-framenode-c.md#getRenderNode-1)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md#RenderNode)的接<br/>口对其进行属性设置与子节点操作。<br/> |
| [ReactiveBuilderNode](arkts-arkui-reactivebuildernode-c.md) | ReactiveBuilderNode支持通过无状态的UI方法[@Builder](../../../../ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变量<br/>。ReactiveBuilderNode中持有的[FrameNode](arkts-arkui-framenode-c.md#FrameNode)仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对ReactiveBuilderNode<br/>持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getFrameNode-1)方法和<br/>[FrameNode](arkts-arkui-framenode-c.md#FrameNode)节点的[getRenderNode](arkts-arkui-framenode-c.md#getRenderNode-1)方法获取RenderNode，并通过<br/>[RenderNode](arkts-arkui-rendernode-c.md#RenderNode)的接口对其进行属性设置与子节点操作。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuildOptions](arkts-arkui-buildoptions-i.md) | build的可选参数。<br/> |
| [RenderOptions](arkts-arkui-renderoptions-i.md) | 创建BuilderNode时的可选参数。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NodeRenderType](arkts-arkui-noderendertype-e.md) | 节点渲染类型枚举。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | [postInputEvent](arkts-arkui-buildernode-c.md#postInputEvent-1)的参数，定义要发送的输入事件类型。<br/> |

