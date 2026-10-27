# TapGesture

Defines TapGesture Component.

## TapGesture

```TypeScript
TapGesture(value?: TapGestureParameters)
```

Creates a tap gesture. Inherits from [GestureInterface<T>](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

When triggered by keyboard or gamepad input, the gesture event's [SourceTool](arkts-arkui-common-comp-sourcetool-e.md) is **Unknown**, and SourceType is **KEY** or **JOYSTICK**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TapGestureInterface-(value?: TapGestureParameters): TapGestureInterface--><!--Device-TapGestureInterface-(value?: TapGestureParameters): TapGestureInterface-End-->

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

<!--Device-TapGestureInterface-onAction(event: (event: GestureEvent) => void): TapGestureInterface--><!--Device-TapGestureInterface-onAction(event: (event: GestureEvent) => void): TapGestureInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for the tap event. |

## Summary

### Classes

| Name | Description |
| --- | --- |
| [EventTargetInfo](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md) | Provides the information about the component corresponding to the gesture recognizer. |
| [GestureGroupHandler](arkts-arkui-tapgesture-comp-gesturegrouphandler-c.md) | Defines the gesture group handler object type, which is used to combine multiple gestures and bind them to a component as a whole. It is suitable for scenarios where the recognition order or concurrency relationship of multiple gestures such as single tap, double tap, and long press needs to be coordinated. |
| [GestureHandler](arkts-arkui-tapgesture-comp-gesturehandler-c.md) | Defines the base type of a gesture handler, which carries the common configuration capabilities of specific gesture handlers, such as setting the gesture tag and limiting the supported event input sources. |
| [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) | Defines the gesture recognizer object, which supports querying gesture tag, type, state, and target component information, controlling the enabled state of the recognizer, blocking the current recognition process, and determining whether the bound node belongs to a specified component subtree. It is applicable to gesture recognition state management and gesture competition handling scenarios. |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Defines the long press gesture handler object type, which is used to recognize long press interactions on a component. It is suitable for scenarios where an operation is triggered after pressing and holding, and supports configuring recognition conditions such as the number of triggering fingers, the long press duration, whether to trigger continuously, and the movement threshold. |
| [LongPressRecognizer](arkts-arkui-tapgesture-comp-longpressrecognizer-c.md) | Defines the long press gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying whether long press is triggered repeatedly, the trigger duration threshold, and the maximum recognizable movement distance. It is applicable to querying the long press gesture recognition configuration. |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Defines the pan gesture handler object type, which is used to recognize drag or slide interactions on a component. It is suitable for scenarios where the state needs to be updated as the finger moves, and supports configuring the number of triggering fingers, the pan direction, the minimum drag distance, and the trigger distance for different input sources. |
| [PanGestureOptions](arkts-arkui-tapgesture-comp-pangestureoptions-c.md) | Defines the PanGesture options. |
| [PanRecognizer](arkts-arkui-tapgesture-comp-panrecognizer-c.md) | Defines the pan gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying pan gesture attributes, recognition direction, minimum pan distance, and pan thresholds for different input sources. It is applicable to querying the pan gesture recognition configuration. |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Defines the pinch gesture handler object type, which is used to recognize multi-finger pinch interactions on a component. It is suitable for scaling operation scenarios, and supports configuring recognition conditions such as the number of triggering fingers, the minimum recognition distance, and the finger count limit. |
| [PinchRecognizer](arkts-arkui-tapgesture-comp-pinchrecognizer-c.md) | Defines the pinch gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying the minimum recognition distance threshold of the pinch gesture. It is applicable to querying the recognition configuration of scaling gestures. |
| [RotationGestureHandler](arkts-arkui-tapgesture-comp-rotationgesturehandler-c.md) | Defines the rotation gesture handler object type, which is used to recognize multi-finger rotation interactions on a component. It is suitable for scenarios where an object needs to be rotated or an angle needs to be adjusted, and supports configuring recognition conditions such as the number of triggering fingers, the minimum angle change, and the finger count limit. |
| [RotationRecognizer](arkts-arkui-tapgesture-comp-rotationrecognizer-c.md) | Defines the rotation gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying the minimum angle threshold for triggering the rotation gesture. It is applicable to querying the gesture recognition configuration of rotation interactions. |
| [ScrollableTargetInfo](arkts-arkui-tapgesture-comp-scrollabletargetinfo-c.md) | Provides the information about the scrollable container component corresponding to the gesture recognizer. It inherits from [EventTargetInfo](arkts-arkui-tapgesture-comp-eventtargetinfo-c.md). |
| [SwipeGestureHandler](arkts-arkui-tapgesture-comp-swipegesturehandler-c.md) | Defines the swipe gesture handler object type, which is used to recognize quick swipe interactions on a component. It is suitable for scenarios where an operation is triggered based on the swipe direction or speed, and supports configuring the number of triggering fingers, the swipe direction, and the minimum speed. |
| [SwipeRecognizer](arkts-arkui-tapgesture-comp-swiperecognizer-c.md) | Defines the swipe gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying the velocity threshold and swipe direction of the swipe gesture. It is applicable to querying the swipe gesture recognition configuration. |
| [TapGestureHandler](arkts-arkui-tapgesture-comp-tapgesturehandler-c.md) | Defines the tap gesture handler object type, which is used to recognize tap interactions on a component. It is suitable for touch scenarios such as single tap, multiple taps, or multi-finger tap, and supports configuring recognition conditions such as the tap count and the number of triggering fingers. |
| [TapRecognizer](arkts-arkui-tapgesture-comp-taprecognizer-c.md) | Defines the tap gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports obtaining the tap count threshold. It is applicable to querying the recognition configuration of single-tap or multi-tap gestures. |
| [TouchRecognizer](arkts-arkui-tapgesture-comp-touchrecognizer-c.md) | Defines the touch gesture recognizer object, which supports obtaining touch target information, canceling the current touch interaction, and determining whether the bound node belongs to a specified component subtree. It is applicable to touch processing and event distribution control scenarios. |

### Interfaces

| Name | Description |
| --- | --- |
| [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md) | Defines the basic gesture event type. Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md). |
| [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md) | Provides the parameters of the basic gesture handler. |
| [EventLocationInfo](arkts-arkui-tapgesture-comp-eventlocationinfo-i.md) | Provides coordinate information for tap gestures. |
| [FingerInfo](arkts-arkui-tapgesture-comp-fingerinfo-i.md) | Defines the finger information type. |
| [GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md) | Defines the gesture event information. Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md). |
| [GestureGroupGestureHandlerOptions](arkts-arkui-tapgesture-comp-gesturegroupgesturehandleroptions-i.md) | Provides the parameters of the gesture group handler. |
| [GestureGroupInterface](arkts-arkui-tapgesture-comp-gesturegroupinterface-i.md) | Combined gestures integrate two or more gestures into a compound gesture, supporting sequential recognition, parallel recognition, and exclusive recognition. They are suitable for scenarios where multiple basic gestures need to be combined on the same component and their recognition order, parallel relationship, or exclusive relationship needs to be controlled, helping developers implement more complex gesture interaction logic. |
| [GestureInfo](arkts-arkui-tapgesture-comp-gestureinfo-i.md) | Defines the gesture information type. |
| [GestureInterface](arkts-arkui-tapgesture-comp-gestureinterface-i.md) | Configures common attributes of gestures, supporting setting gesture tags and input types for gesture responses. |
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
| [GestureType](arkts-arkui-tapgesture-comp-gesturetype-t.md) | Enumerates gesture types. |

### Enums

| Name | Description |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-tapgesture-comp-gesturejudgeresult-e.md) | Enumerates gesture competition results. |
| [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | Enumerates masking modes of child component gestures. |
| [GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md) | Defines the recognition mode of a gesture group. |
| [GesturePriority](arkts-arkui-tapgesture-comp-gesturepriority-e.md) | Defines the priority of the bound gesture, which is suitable for scenarios where the response order of gestures needs to be controlled or gesture conflicts need to be handled when multiple gestures are bound at the same time. |
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
