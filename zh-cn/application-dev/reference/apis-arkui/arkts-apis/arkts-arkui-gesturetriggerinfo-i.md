# GestureTriggerInfo

特定手势回调函数触发时的信息。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## current

```TypeScript
current: GestureRecognizer
```

手势识别器对象。可从中获取手势的详细信息，但请勿在本地保留此对象，因为当节点释放后该对象可能失效。

**类型：** GestureRecognizer

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentPhase

```TypeScript
currentPhase: GestureActionPhase
```

手势动作回调阶段。

**类型：** GestureActionPhase

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: GestureEvent
```

手势事件对象。

**类型：** GestureEvent

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## node

```TypeScript
node?: FrameNode
```

触发手势的节点。默认值为null，表示没有触发手势的节点。

**类型：** FrameNode

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

