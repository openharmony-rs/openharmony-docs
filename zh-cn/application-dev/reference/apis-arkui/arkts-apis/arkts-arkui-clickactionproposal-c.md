# ClickActionProposal

智慧手势点击动作处理。当通过[registerMonitor](arkts-arkui-smartgesturecontroller-c.md#registermonitor-1)接口动态自定义智慧手势行为时，设置返回值
[GestureHandlingResolution](arkts-arkui-gesturehandlingresolution-c.md)的selectedProposal为该类型对象，会触发目标组件的点击操作。

> **说明：**
>
> - 该动作处理遵循“先选中，再点击”的处理语义。
>
> - 当目标节点尚未被选中时，本次处理会优先建立选中态，而不会立即触发点击。

**继承/实现关系：** ClickActionProposal extends [TargetedGestureProposal](arkts-arkui-targetedgestureproposal-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(node: FrameNode)
```

智慧手势点击动作处理的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 响应点击动作的目标节点。 |

