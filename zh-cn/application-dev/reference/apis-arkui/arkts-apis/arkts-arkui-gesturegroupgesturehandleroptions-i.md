# GestureGroupGestureHandlerOptions

手势组处理器配置参数。

**起始版本：** 12

<!--Device-unnamed-interface GestureGroupGestureHandlerOptions--><!--Device-unnamed-interface GestureGroupGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## gestures

```TypeScript
gestures: GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]
```

设置手势组中需要包含的手势集合。 **说明：** 当需要为一个组件同时添加单击和双击手势时，可在[GestureGroup](arkts-arkui-gesture-con.md#gesturegroup)中添加两个[TapGesture](arkts-arkui-gesture-con.md#tapgesture)，需要双击手势在前，单击手势在后，否则不生效。

**类型：** [GestureHandler](arkts-arkui-gesturehandler-c.md)&lt;[TapGestureHandler](arkts-arkui-tapgesturehandler-c.md) \| [LongPressGestureHandler](arkts-arkui-longpressgesturehandler-c.md) \| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) \| [SwipeGestureHandler](arkts-arkui-swipegesturehandler-c.md) \| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) \| [RotationGestureHandler](arkts-arkui-rotationgesturehandler-c.md) \| [GestureGroupHandler](arkts-arkui-gesturegrouphandler-c.md)&gt;[]

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureGroupGestureHandlerOptions-gestures: GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]--><!--Device-GestureGroupGestureHandlerOptions-gestures: GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode: GestureMode
```

设置组合手势识别模式。 默认值：GestureMode.Sequence

**类型：** [GestureMode](arkts-arkui-gesturemode-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GestureGroupGestureHandlerOptions-mode: GestureMode--><!--Device-GestureGroupGestureHandlerOptions-mode: GestureMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

