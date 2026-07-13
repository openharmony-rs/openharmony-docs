# TapGesture

支持单击、双击和多次点击事件的识别。

> **说明：**
>
> 当组件同时绑定双击和单击手势且双击手势先绑定时，单击手势会有300ms的延时。


## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

创建点击手势对象。继承自[GestureInterface<T>]{@link GestureInterface}。

触发点击手势事件的设备类型为键盘或手柄时，事件的[SourceTool]{@link SourceTool}值为Unknown，事件的[SourceType]{@link SourceType}值为KEY或JOYSTICK。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | TapGestureParameters | 否 | 点击手势的相关参数。 |

## TapGesture

```TypeScript
TapGesture(event: (event: GestureEvent) => void)
```

点击手势识别成功回调。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

## 汇总

- [BaseGestureEvent](arkts-arkui-tapgesture-basegestureevent-i.md)
- [BaseHandlerOptions](arkts-arkui-tapgesture-basehandleroptions-i.md)
- [EventLocationInfo](arkts-arkui-tapgesture-eventlocationinfo-i.md)
- [FingerInfo](arkts-arkui-tapgesture-fingerinfo-i.md)
- [GestureEvent](arkts-arkui-tapgesture-gestureevent-i.md)
- [GestureGroupGestureHandlerOptions](arkts-arkui-tapgesture-gesturegroupgesturehandleroptions-i.md)
- [GestureGroupInterface](arkts-arkui-tapgesture-gesturegroupinterface-i.md)
- [GestureInfo](arkts-arkui-tapgesture-gestureinfo-i.md)
- [GestureInterface](arkts-arkui-tapgesture-gestureinterface-i.md)
- [LongPressGestureEvent](arkts-arkui-tapgesture-longpressgestureevent-i.md)
- [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-longpressgesturehandleroptions-i.md)
- [LongPressGestureInterface](arkts-arkui-tapgesture-longpressgestureinterface-i.md)
- [PanGestureEvent](arkts-arkui-tapgesture-pangestureevent-i.md)
- [PanGestureHandlerOptions](arkts-arkui-tapgesture-pangesturehandleroptions-i.md)
- [PanGestureInterface](arkts-arkui-tapgesture-pangestureinterface-i.md)
- [PinchGestureEvent](arkts-arkui-tapgesture-pinchgestureevent-i.md)
- [PinchGestureHandlerOptions](arkts-arkui-tapgesture-pinchgesturehandleroptions-i.md)
- [PinchGestureInterface](arkts-arkui-tapgesture-pinchgestureinterface-i.md)
- [RotationGestureEvent](arkts-arkui-tapgesture-rotationgestureevent-i.md)
- [RotationGestureHandlerOptions](arkts-arkui-tapgesture-rotationgesturehandleroptions-i.md)
- [RotationGestureInterface](arkts-arkui-tapgesture-rotationgestureinterface-i.md)
- [SwipeGestureEvent](arkts-arkui-tapgesture-swipegestureevent-i.md)
- [SwipeGestureHandlerOptions](arkts-arkui-tapgesture-swipegesturehandleroptions-i.md)
- [SwipeGestureInterface](arkts-arkui-tapgesture-swipegestureinterface-i.md)
- [TapGestureEvent](arkts-arkui-tapgesture-tapgestureevent-i.md)
- [TapGestureHandlerOptions](arkts-arkui-tapgesture-tapgesturehandleroptions-i.md)
- [TapGestureParameters](arkts-arkui-tapgesture-tapgestureparameters-i.md)
- [GestureType](arkts-arkui-tapgesture-gesturetype-t.md)
- [GestureJudgeResult](arkts-arkui-tapgesture-gesturejudgeresult-e.md)
- [GestureMask](arkts-arkui-tapgesture-gesturemask-e.md)
- [GestureMode](arkts-arkui-tapgesture-gesturemode-e.md)
- [GesturePriority](arkts-arkui-tapgesture-gesturepriority-e.md)
- [GestureRecognizerState](arkts-arkui-tapgesture-gesturerecognizerstate-e.md)
- [PanDirection](arkts-arkui-tapgesture-pandirection-e.md)
- [SwipeDirection](arkts-arkui-tapgesture-swipedirection-e.md)
