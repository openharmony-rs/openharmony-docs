# GestureGroupGestureHandlerOptions

手势组处理器配置参数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gestures

```TypeScript
gestures: GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]
```

设置手势组中需要包含的手势集合。

**说明：**

当需要为一个组件同时添加单击和双击手势时，可在[GestureGroup](arkts-arkui-tapgesture-con.md#gesturegroup)中添加两个[TapGesture](TapGesture)，需要双击手势在前，单击手势在后，否则不生效。

**类型：** GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode: GestureMode
```

设置组合手势识别模式。

默认值：GestureMode.Sequence

**类型：** GestureMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

