# BuilderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BuilderNode](arkts-arkui-buildernode-c.md) | class BuilderNode\<Args extends Object[]>  BuilderNode支持通过无状态的UI方法[@Builder](docroot://ui/state-management/arkts-builder.md)生成组件树，并持有组件树的根节点。不支持定义为状态变量。BuilderNode中持有的FrameNode仅用于将该BuilderNode作为子节点挂载到其他FrameNode上。对BuilderNode持有的FrameNode进行属性设置与子节点操作可能会产生未定义行为，因此不建议通过BuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getframenode-1)方法和[FrameNode](arkts-arkui-framenode-c.md)的[getRenderNode](arkts-arkui-framenode-c.md#getrendernode-1)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md)的接口对其进行属性设置与子节点操作。 |
| [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) | ReactiveBuilderNode支持通过无状态的UI方法[@Builder](docroot://ui/state-management/arkts-builder.md)生成组件树，并持有该组件树的根节点，不支持定义为状态变量。ReactiveBuilderNode中持有的[FrameNode](arkts-arkui-framenode-c.md)仅用于将此ReactiveBuilderNode作为子节点挂载到其他FrameNode上。对ReactiveBuilderNode持有的FrameNode进行属性设置与子节点操作可能会导致未定义行为，因此不建议通过ReactiveBuilderNode的[getFrameNode](arkts-arkui-buildernode-c.md#getframenode-1)方法和[FrameNode](arkts-arkui-framenode-c.md)节点的[getRenderNode](arkts-arkui-framenode-c.md#getrendernode-1)方法获取RenderNode，并通过[RenderNode](arkts-arkui-rendernode-c.md)的接口对其进行属性设置与子节点操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | build的可选参数。 |
| [RenderOptions](arkts-arkui-buildernode-renderoptions-i.md) | 创建BuilderNode时的可选参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NodeRenderType](arkts-arkui-buildernode-noderendertype-e.md) | 节点渲染类型枚举。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InputEventType](arkts-arkui-inputeventtype-t.md) | [postInputEvent](arkts-arkui-buildernode-c.md#postinputevent-1)的参数，定义要发送的输入事件类型。 |

