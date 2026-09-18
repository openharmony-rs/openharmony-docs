# GestureControl

Enumerates gesture competition results.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Enums

| Name | Description |
| --- | --- |
| [GestureType](arkts-arkui-gesturecontrol-gesturetype-e.md) | Enumerates gesture recognizer types. |

## Examples

```TypeScript
This example demonstrates the recognition of a long press gesture using LongPressGesture. Since API version 22, the allowableMovement attribute in [LongPressGestureHandlerOptions](./ts-gesturehandler.md#longpressgesturehandleroptions) can be used to set the maximum movement distance of a gesture to be recognized.
```

```TypeScript
### Example 1: Implementing Double-Tap Gesture Recognition

This example demonstrates the recognition of a double-tap gesture using TapGesture.


```

```TypeScript
### Example 2: Obtaining Coordinates of a Single-Tap Gesture

This example demonstrates how to obtain the coordinates of a single-tap gesture using TapGesture.
```

```TypeScript
This example demonstrates the recognition of single-finger and double-finger pan gestures using PanGesture.
```

```TypeScript
This example demonstrates how to implement swipe gesture recognition.
```

```TypeScript
This example demonstrates the recognition of a two-finger rotation gesture using RotationGesture.
```

```TypeScript
This example demonstrates the sequential recognition of combined gestures, specifically long press and pan gestures, using GestureGroup.
```

```TypeScript
### Example 1: Implementing Simple Scaling

This example demonstrates the recognition of a three-finger pinch gesture using PinchGesture.


```

```TypeScript
### Example 2: Implementing Image Scaling with Finger Tracking

This example demonstrates how to implement image scaling with finger tracking by configuring PinchGesture.
```
