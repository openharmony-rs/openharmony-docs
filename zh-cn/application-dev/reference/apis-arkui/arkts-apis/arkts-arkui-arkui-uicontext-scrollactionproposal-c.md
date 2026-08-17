# ScrollActionProposal

智慧手势滚动动作处理，默认方向为向前滚动，包括向右和向下。当通过[registerMonitor](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-smartgesturecontroller-c.md#registermonitor)接口动态自定义智慧手势行为时，设置返回值 [GestureHandlingResolution](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-gesturehandlingresolution-c.md#gesturehandlingresolution)的selectedProposal为该类型对象，会触发目标组件的滚动操作。

**继承/实现关系：** ScrollActionProposal extends [TargetedGestureProposal](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-targetedgestureproposal-c.md#targetedgestureproposal)

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export class ScrollActionProposal--><!--Device-unnamed-export class ScrollActionProposal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(node: FrameNode, distance: double)
```

智慧手势滚动动作处理的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollActionProposal-constructor(node: FrameNode, distance: double)--><!--Device-ScrollActionProposal-constructor(node: FrameNode, distance: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | FrameNode | 是 | 响应滚动动作的目标节点。 |
| distance | double | 是 | 滚动距离。<br/>取值范围：[0, +∞)，小于0时按0处理。<br/>单位为vp。 |

## distance

```TypeScript
distance?: double
```

智慧手势滚动距离。 取值范围：[0, +∞)，小于0时按0处理。 单位为vp。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollActionProposal-distance?: double--><!--Device-ScrollActionProposal-distance?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

