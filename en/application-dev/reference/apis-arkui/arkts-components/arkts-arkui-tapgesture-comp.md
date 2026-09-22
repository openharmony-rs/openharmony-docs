# TapGesture

Defines TapGesture Component.

## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

Creates a tap gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

When triggered by keyboard or gamepad input, the gesture event's [SourceTool](arkts-arkui-common-comp-sourcetool-e.md) is **Unknown**, and SourceType is **KEY** or **JOYSTICK**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TapGestureParameters](arkts-arkui-tapgesture-comp-tapgestureparameters-i.md) | No | Parameters for the tap gesture. |

## TapGesture

```TypeScript
TapGesture(event: (event: GestureEvent) => void)
```

Triggered when the tap gesture is recognized.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the tap event. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md) | Defines the basic gesture event type. Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md). |
| [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md) | Provides the parameters of the basic gesture handler. |
| [EventLocationInfo](arkts-arkui-tapgesture-comp-eventlocationinfo-i.md) | Provides coordinate information for tap gestures. |
| [FingerInfo](arkts-arkui-tapgesture-comp-fingerinfo-i.md) | Defines the finger information type. |
| [GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md) | Defines the gesture event information. Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md). |
| [GestureGroupGestureHandlerOptions](arkts-arkui-tapgesture-comp-gesturegroupgesturehandleroptions-i.md) | Provides the parameters of the gesture group handler. |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) | Combined gestures integrate two or more gestures into a compound gesture, supporting sequential recognition, parallel recognition, and exclusive recognition. |
| [GestureInfo](arkts-arkui-tapgesture-comp-gestureinfo-i.md) | Defines the gesture information type. |
| [GestureInterface](arkts-arkui-tapgesture-comp-gestureinterface-i.md) | Defines the gesture API. |
| [LongPressGestureEvent](arkts-arkui-tapgesture-comp-longpressgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-comp-longpressgesturehandleroptions-i.md) | Provides the parameters of the long press gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) | **LongPressGesture** is used to trigger a long press gesture. This gesture requires one or more fingers to be held down for a specified duration, which is 500 ms by default and can be adjusted using the **duration** parameter. |
| [PanGestureEvent](arkts-arkui-tapgesture-comp-pangestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [PanGestureHandlerOptions](arkts-arkui-tapgesture-comp-pangesturehandleroptions-i.md) | Provides the parameters of the pan gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [PanGestureInterface](arkts-arkui-tapgesture-comp-pangestureinterface-i.md) | PanGesture is used to trigger a pan gesture when the movement distance of a finger on the screen reaches the minimum value. |
| [PinchGestureEvent](arkts-arkui-tapgesture-comp-pinchgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [PinchGestureHandlerOptions](arkts-arkui-tapgesture-comp-pinchgesturehandleroptions-i.md) | Provides the parameters of the pinch gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [PinchGestureInterface](arkts-arkui-tapgesture-comp-pinchgestureinterface-i.md) | **PinchGesture** is used to trigger a pinch gesture, which requires two to five fingers with a minimum 5 vp distance between the fingers. |
| [RotationGestureEvent](arkts-arkui-tapgesture-comp-rotationgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [RotationGestureHandlerOptions](arkts-arkui-tapgesture-comp-rotationgesturehandleroptions-i.md) | Provides the parameters of the rotation gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [RotationGestureInterface](arkts-arkui-tapgesture-comp-rotationgestureinterface-i.md) | **RotationGesture** is used to trigger a rotation gesture, which recognizes rotational movements using two to five fingers, with a minimum angular change of 1 degree. This gesture cannot be triggered using a two-finger rotation operation on a trackpad. |
| [SwipeGestureEvent](arkts-arkui-tapgesture-comp-swipegestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [SwipeGestureHandlerOptions](arkts-arkui-tapgesture-comp-swipegesturehandleroptions-i.md) | Provides the parameters of the swipe gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [SwipeGestureInterface](arkts-arkui-tapgesture-comp-swipegestureinterface-i.md) | **SwipeGesture** is used to trigger a swipe gesture. This gesture is successfully recognized when the swipe speed exceeds the specified threshold, which is 100 vp/s by default. |
| [TapGestureEvent](arkts-arkui-tapgesture-comp-tapgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin). |
| [TapGestureHandlerOptions](arkts-arkui-tapgesture-comp-tapgesturehandleroptions-i.md) | Provides the parameters of the tap gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |
| [TapGestureParameters](arkts-arkui-tapgesture-comp-tapgestureparameters-i.md) | Defines tap gesture parameters. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md). |

### Types

| Name | Description |
| --- | --- |
| [GestureType](arkts-arkui-tapgesture-comp-gesturetype-t.md) | Defines the Gesture Type. |

### Enums

| Name | Description |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-tapgesture-comp-gesturejudgeresult-e.md) | Enumerates gesture competition results. |
| [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | Enumerates masking modes of child component gestures. |
| [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md) | Defines the recognition mode of a gesture group. |
| [GesturePriority](arkts-arkui-tapgesture-comp-gesturepriority-e.md) | Enumerates gesture priority levels. |
| [GestureRecognizerState](arkts-arkui-tapgesture-comp-gesturerecognizerstate-e.md) | Enumerates the gesture recognizer states. |
| [PanDirection](arkts-arkui-tapgesture-comp-pandirection-e.md) | Enumerates the pan directions. Unlike **SwipeDirection**, **PanDirection** has no angular restrictions. |
| [SwipeDirection](arkts-arkui-tapgesture-comp-swipedirection-e.md) | Enumerates the directions in which the swipe gesture can be recognized. |

## Examples

### Example 1: Implementing Double-Tap Gesture Recognition

This example demonstrates the recognition of a double-tap gesture using TapGesture.



```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {
  @State value: string = '';

  build() {
    Column() {
      // The gesture event is triggered by double-tapping.
      Text('Click twice').fontSize(28)
        .gesture(
        TapGesture({ count: 2 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.value = JSON.stringify(event.fingerList[0])
            }
          })
        )
      Text(this.value)
    }
    .height(300)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30)
  }
}
```

### Example 2: Obtaining Coordinates of a Single-Tap Gesture

This example demonstrates how to obtain the coordinates of a single-tap gesture using TapGesture.

```TypeScript
// xxx.ets
@Entry
@Component
struct TapGestureExample {

  build() {
    Column() {
      Text('Click Once').fontSize(28)
        .gesture(
          TapGesture({ count: 1, fingers: 1 })
            .onAction((event: GestureEvent | undefined) => {
              if (event) {
                console.info(`x = ${JSON.stringify(event.tapLocation?.x)}`)
                console.info(`y = ${JSON.stringify(event.tapLocation?.y)}`)
                console.info(`windowX = ${JSON.stringify(event.tapLocation?.windowX)}`)
                console.info(`windowY = ${JSON.stringify(event.tapLocation?.windowY)}`)
                console.info(`displayX = ${JSON.stringify(event.tapLocation?.displayX)}`)
                console.info(`displayY = ${JSON.stringify(event.tapLocation?.displayY)}`)
                // The globalDisplayX and globalDisplayY attributes are added since API version 23.
                console.info(`globalDisplayX = ${JSON.stringify(event.tapLocation?.globalDisplayX)}`)
                console.info(`globalDisplayY = ${JSON.stringify(event.tapLocation?.globalDisplayY)}`)
              }
            })
        )
    }
    .height(200)
    .width(300)
    .padding(20)
    .border({ width: 3 })
    .margin(30)
  }
}
```
