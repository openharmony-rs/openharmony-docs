# GestureGroupGestureHandlerOptions

手势组处理器配置参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface GestureGroupGestureHandlerOptions--><!--Device-unnamed-export interface GestureGroupGestureHandlerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gestures

```TypeScript
gestures: GestureHandler[]
```

设置手势组中需要包含的手势集合。 **说明：** 当需要为一个组件同时添加单击和双击手势时，可在GestureGroup中添加两个TapGesture，需要双击手势在前，单击手势在后，否则不生效。

**类型：** [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md)[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroupGestureHandlerOptions-gestures: GestureHandler[]--><!--Device-GestureGroupGestureHandlerOptions-gestures: GestureHandler[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode: GestureMode
```

设置组合手势识别模式。 默认值：GestureMode.Sequence

**类型：** [GestureMode](arkts-arkui-gesture-gesturemode-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GestureGroupGestureHandlerOptions-mode: GestureMode--><!--Device-GestureGroupGestureHandlerOptions-mode: GestureMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

