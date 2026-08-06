# GestureTriggerInfo

特定手势回调函数触发时的信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export interface GestureTriggerInfo--><!--Device-unnamed-export interface GestureTriggerInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## current

```TypeScript
current: GestureRecognizer
```

手势识别器对象。可从中获取手势的详细信息，但请勿在本地保留此对象，因为当节点释放后该对象可能失效。

**类型：** GestureRecognizer

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureTriggerInfo-current: GestureRecognizer--><!--Device-GestureTriggerInfo-current: GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentPhase

```TypeScript
currentPhase: GestureActionPhase
```

手势动作回调阶段。

**类型：** GestureActionPhase

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureTriggerInfo-currentPhase: GestureActionPhase--><!--Device-GestureTriggerInfo-currentPhase: GestureActionPhase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: GestureEvent
```

手势事件对象。

**类型：** GestureEvent

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureTriggerInfo-event: GestureEvent--><!--Device-GestureTriggerInfo-event: GestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## node

```TypeScript
node?: FrameNode
```

触发手势的节点。默认值为null，表示没有触发手势的节点。

**类型：** FrameNode

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureTriggerInfo-node?: FrameNode--><!--Device-GestureTriggerInfo-node?: FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

