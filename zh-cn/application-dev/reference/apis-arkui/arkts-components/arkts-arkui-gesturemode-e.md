# GestureMode

定义手势组的识别模式。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Sequence

```TypeScript
Sequence
```

顺序识别，根据注册顺序依次进行手势识别，直到所有手势识别成功。如果任一手势识别失败，则后续手势识别均无法完成。

在顺序识别手势组中，仅最后一个手势能响应onActionEnd事件。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Parallel

```TypeScript
Parallel
```

并行识别，注册的手势同时识别，直到所有手势识别结束，手势识别互相不影响。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Exclusive

```TypeScript
Exclusive
```

互斥识别，注册的手势同时识别，若有一个手势识别成功，则结束手势识别，其他手势识别均失败。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

