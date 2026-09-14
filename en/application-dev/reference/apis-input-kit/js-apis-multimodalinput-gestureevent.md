# @ohos.multimodalInput.gestureEvent (Gesture Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=9a1cb1c28d6db83260f62725623fc8e88729c2c6 translatedAt=2026-09-01T01:22:01.834Z pushedAt=2026-09-03T08:35:54.070Z -->

The **gestureEvent** module provides APIs for gesture events reported by devices.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { Rotate, Pinch, ThreeFingersSwipe, FourFingersSwipe, ThreeFingersTap, ActionType } from '@kit.InputKit';
```

## Pinch

Defines a pinch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No    | No    | Gesture event type, including gesture cancel, gesture start, gesture update, and gesture end.                                   |
| scale        | number      | No   | No   | Pinch scale factor. The value is greater than or equal to 0.                            |

## Rotate<sup>11+</sup>

Defines a rotation gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type | [ActionType](#actiontype)   | No   | No   | Gesture event type, for example, gesture start, gesture update, or gesture end.                                  |
| angle | number      | No    | No    | Rotation angle, in degrees.                             |

## ThreeFingersSwipe

Defines a three-finger swipe gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No   | No   | Gesture event type, for example, gesture start, gesture update, or gesture end.                                  |
| x        | number      | No    | No    | X coordinate, in px.                             |
| y        | number      | No    | No    | Y coordinate, in px.                             |

## FourFingersSwipe

Defines a four-finger swipe gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name            | Type       | Read-Only  | Optional  | Description                                      |
| -------------- | ----------- | ---- | ---- | ---------------------------------------- |
| type         | [ActionType](#actiontype)   | No   | No   | Gesture event type, for example, gesture start, gesture update, or gesture end.                                  |
| x        | number      | No    | No    | X coordinate, in px.                               |
| y        | number      | No    | No    | Y coordinate, in px.                              |

## ThreeFingersTap<sup>11+</sup>

Defines a three-finger tap gesture event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name              | Type                     | Read-Only| Optional| Description            |
| ------------------ | ------------------------- | ---- | ---- | ---------------- |
| type | [ActionType](#actiontype) | No  | No  | Gesture event type, for example, gesture start, gesture update, or gesture end.|

## ActionType

Enumerates gesture event types.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name       | Value | Description            |
| ----------- | --- | --------------- |
| CANCEL      | 0   | Canceled.            |
| BEGIN       | 1   | Started.        |
| UPDATE      | 2   | Updated.        |
| END         | 3   | Ended.        |