# TapGesture

Defines TapGesture Component.

## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

Creates a tap gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-gestureinterface-i.md).

When triggered by keyboard or gamepad input, the gesture event's [SourceTool](arkts-arkui-sourcetool-e.md) is **Unknown**, and SourceType is **KEY** or **JOYSTICK**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [TapGestureParameters](arkts-arkui-tapgestureparameters-i.md) | No | Parameters for the tap gesture. |

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
| [BaseGestureEvent](arkts-arkui-basegestureevent-i.md) | Defines the basic gesture event type. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md) | Provides the parameters of the basic gesture handler. |
| [EventLocationInfo](arkts-arkui-eventlocationinfo-i.md) | Provides coordinate information for tap gestures. |
| [FingerInfo](arkts-arkui-fingerinfo-i.md) | Defines the finger information type. |
| [GestureEvent](arkts-arkui-gestureevent-i.md) | Defines the gesture event information. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md). |
| [GestureGroupGestureHandlerOptions](arkts-arkui-gesturegroupgesturehandleroptions-i.md) | Provides the parameters of the gesture group handler. |
| [GestureGroupInterface](arkts-arkui-gesturegroupinterface-i.md) | Combined gestures integrate two or more gestures into a compound gesture, supporting sequential recognition, parallel recognition, and exclusive recognition. |
| [GestureInfo](arkts-arkui-gestureinfo-i.md) | Defines the gesture information type. |
| [GestureInterface](arkts-arkui-gestureinterface-i.md) | Defines the gesture API. |
| [LongPressGestureEvent](arkts-arkui-longpressgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [LongPressGestureHandlerOptions](arkts-arkui-longpressgesturehandleroptions-i.md) | Provides the parameters of the long press gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | **LongPressGesture** is used to trigger a long press gesture. This gesture requires one or more fingers to be held down for a specified duration, which is 500 ms by default and can be adjusted using the **duration** parameter. |
| [PanGestureEvent](arkts-arkui-pangestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [PanGestureHandlerOptions](arkts-arkui-pangesturehandleroptions-i.md) | Provides the parameters of the pan gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [PanGestureInterface](arkts-arkui-pangestureinterface-i.md) | PanGesture is used to trigger a pan gesture when the movement distance of a finger on the screen reaches the minimum value. |
| [PinchGestureEvent](arkts-arkui-pinchgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [PinchGestureHandlerOptions](arkts-arkui-pinchgesturehandleroptions-i.md) | Provides the parameters of the pinch gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [PinchGestureInterface](arkts-arkui-pinchgestureinterface-i.md) | **PinchGesture** is used to trigger a pinch gesture, which requires two to five fingers with a minimum 5 vp distance between the fingers. |
| [RotationGestureEvent](arkts-arkui-rotationgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [RotationGestureHandlerOptions](arkts-arkui-rotationgesturehandleroptions-i.md) | Provides the parameters of the rotation gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [RotationGestureInterface](arkts-arkui-rotationgestureinterface-i.md) | **RotationGesture** is used to trigger a rotation gesture, which recognizes rotational movements using two to five fingers, with a minimum angular change of 1 degree. This gesture cannot be triggered using a two-finger rotation operation on a trackpad. |
| [SwipeGestureEvent](arkts-arkui-swipegestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | Provides the parameters of the swipe gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [SwipeGestureInterface](arkts-arkui-swipegestureinterface-i.md) | **SwipeGesture** is used to trigger a swipe gesture. This gesture is successfully recognized when the swipe speed exceeds the specified threshold, which is 100 vp/s by default. |
| [TapGestureEvent](arkts-arkui-tapgestureevent-i.md) | Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin). |
| [TapGestureHandlerOptions](arkts-arkui-tapgesturehandleroptions-i.md) | Provides the parameters of the tap gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |
| [TapGestureParameters](arkts-arkui-tapgestureparameters-i.md) | Defines tap gesture parameters. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md). |

### Types

| Name | Description |
| --- | --- |
| [GestureType](arkts-arkui-gesturetype-t.md) | Defines the Gesture Type. |

### Enums

| Name | Description |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-gesturejudgeresult-e.md) | Enumerates gesture competition results. |
| [GestureMask](arkts-arkui-gesturemask-e.md) | Enumerates masking modes of child component gestures. |
| [GestureMode](arkts-arkui-gesturemode-e.md) | Defines the recognition mode of a gesture group. |
| [GesturePriority](arkts-arkui-gesturepriority-e.md) | Enumerates gesture priority levels. |
| [GestureRecognizerState](arkts-arkui-gesturerecognizerstate-e.md) | Enumerates the gesture recognizer states. |
| [PanDirection](arkts-arkui-pandirection-e.md) | Enumerates the pan directions. Unlike **SwipeDirection**, **PanDirection** has no angular restrictions. |
| [SwipeDirection](arkts-arkui-swipedirection-e.md) | Enumerates the directions in which the swipe gesture can be recognized. |

## Examples

```TypeScript
### Example 1: Implementing Double-Tap Gesture Recognition

This example demonstrates the recognition of a double-tap gesture using TapGesture.


```

```TypeScript
### Example 2: Obtaining Coordinates of a Single-Tap Gesture

This example demonstrates how to obtain the coordinates of a single-tap gesture using TapGesture.
```
