# SelectActionProposal

智慧手势选中动作处理。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md#gesturehandlingresolution)的selectedProposal为该类型对象，会使目标组件被选中。

**继承/实现关系：** SelectActionProposal extends [TargetedGestureProposal](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-targetedgestureproposal-c.md#targetedgestureproposal)

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export class SelectActionProposal--><!--Device-unnamed-export class SelectActionProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(node: FrameNode)
```

智慧手势选中动作处理的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectActionProposal-constructor(node: FrameNode)--><!--Device-SelectActionProposal-constructor(node: FrameNode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 响应选中动作的目标节点。 |

