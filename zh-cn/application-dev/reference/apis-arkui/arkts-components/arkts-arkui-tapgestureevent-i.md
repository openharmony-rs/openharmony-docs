# TapGestureEvent

继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的
event参数来传递。

**继承/实现关系：** TapGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

用于点击手势中，获取当前手势的坐标信息。在非点击手势中，tapLocation返回值为undefined。

**类型：** EventLocationInfo

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

