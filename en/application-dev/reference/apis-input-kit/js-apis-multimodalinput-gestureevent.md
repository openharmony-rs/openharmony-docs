# @ohos.multimodalInput.gestureEvent (Gesture Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

The **gestureEvent** module provides APIs for gesture events reported by devices.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { Rotate, Pinch, ThreeFingersSwipe, FourFingersSwipe, ActionType } from '@kit.InputKit';
```

## Pinch

Defines a pinch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No   | No   | Event type, for example, gesture start, gesture update, or gesture end.                                  |
| scale        | number      | No   | No   | Pinch scale factor. The value is greater than or equal to 0.                            |

## Rotate<sup>11+</sup>

Defines a rotation gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type | [ActionType](#actiontype)   | No   | No   | Event type, for example, gesture start, gesture update, or gesture end.                                  |
| angle | number      | No   | No   | Angle to rotate.                            |

## ThreeFingersSwipe

Defines a three-finger swipe gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No   | No   | Event type, for example, gesture start, gesture update, or gesture end.                                  |
| x        | number      | No   | No   | X coordinate.                            |
| y        | number      | No   | No   | Y coordinate.                            |

## FourFingersSwipe

Defines a four-finger swipe gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No   | No   | Event type, for example, gesture start, gesture update, or gesture end.                                  |
| x        | number      | No   | No   | X coordinate.                            |
| y        | number      | No   | No   | Y coordinate.                            |

## ThreeFingersTap<sup>11+</sup>

Defines a three-finger tap gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name              | Type                     | Read-Only| Optional| Description            |
| ------------------ | ------------------------- | ---- | ---- | ---------------- |
| type | [ActionType](#actiontype) | No  | No  | Event type, for example, gesture start, gesture update, or gesture end.|

## ActionType

Enumerates gesture event types.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name       | Value | Description            |
| ----------- | --- | --------------- |
| CANCEL      | 0   | Canceled.            |
| BEGIN       | 1   | Started.        |
| UPDATE      | 2   | Updated.        |
| END         | 3   | Ended.        |
