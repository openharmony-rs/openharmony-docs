# RenderNode

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [RenderNode](arkts-arkui-rendernode-c.md) | 提供自绘制渲染节点RenderNode，支持开发者通过C API进行开发，完成自定义绘制需求。<br/><br/>&gt; **说明：**<br/><br/>&gt; - 不建议对[BuilderNode](arkts-arkui-buildernode-c.md#BuilderNode)中的RenderNode进行修改操作。BuilderNode中持有的[FrameNode](arkts-arkui-framenode-c.md#FrameNode)仅用于将该<br/>&gt; BuilderNode作为子节点挂载到其他FrameNode上，对该FrameNode或对应的RenderNode进行属性设置与子节点操作可能会产生未定义行为，包括但不限于显示异常、事件异常、稳定性问题等。<br/>&gt;<br/>&gt; - RenderNode对象不支持使用JSON序列化。<br/> |

