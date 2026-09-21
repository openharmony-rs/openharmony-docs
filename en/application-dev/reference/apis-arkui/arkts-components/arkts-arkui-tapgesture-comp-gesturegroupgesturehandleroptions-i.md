# GestureGroupGestureHandlerOptions

```TypeScript
interface GestureGroupGestureHandlerOptions
```

Provides the parameters of the gesture group handler.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## gestures

```TypeScript
gestures: GestureHandler<TapGestureHandler | LongPressGestureHandler | PanGestureHandler | SwipeGestureHandler | PinchGestureHandler | RotationGestureHandler | GestureGroupHandler>[]
```

Gestures to be included in a gesture group.

**NOTE:** 

To add both single-tap and double-tap gestures for a component, add two [TapGesture](arkts-arkui-gesturecontrol-n.md#tapgesture) instances as the [combined gestures](arkts-arkui-tapgesture-comp-con.md#gesturegroup), with the double-tap gesture preceding the single-tap gesture. The gestures will not work correctly if this order is reversed.

**Type:** [GestureHandler](arkts-arkui-tapgesture-comp-gesturehandler-c.md)&lt;[TapGestureHandler](arkts-arkui-tapgesture-comp-tapgesturehandler-c.md) &#124; [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) &#124; [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) &#124; [SwipeGestureHandler](arkts-arkui-tapgesture-comp-swipegesturehandler-c.md) &#124; [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) &#124; [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) &#124; [GestureGroupHandler](arkts-arkui-tapgesture-comp-gesturegrouphandler-c.md)&gt;[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode: GestureMode
```

Recognition mode of combined gestures.

Default value: **GestureMode.Sequence**

**Type:** [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
