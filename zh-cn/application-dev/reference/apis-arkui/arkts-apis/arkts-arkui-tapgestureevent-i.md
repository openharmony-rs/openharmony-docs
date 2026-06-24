# TapGestureEvent

继承自[BaseGestureEvent](arkts-arkui-tapgesture-basegestureevent-i.md#BaseGestureEvent)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#onGestureJudgeBegin-1)的
event参数来传递。

**继承/实现关系：** TapGestureEvent extends [BaseGestureEvent](arkts-arkui-tapgesture-basegestureevent-i.md#BaseGestureEvent)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

用于点击手势中，获取当前手势的坐标信息。在非点击手势中，tapLocation返回值为undefined。

**类型：** EventLocationInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

