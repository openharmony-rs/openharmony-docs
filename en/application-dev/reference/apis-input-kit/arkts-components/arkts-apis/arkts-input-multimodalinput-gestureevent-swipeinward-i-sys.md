# SwipeInward (System API)

```TypeScript
export declare interface SwipeInward
```

Defines an inward swipe event.

**Since:** 12

<!--Device-unnamed-export declare interface SwipeInward--><!--Device-unnamed-export declare interface SwipeInward-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## type

```TypeScript
type: ActionType
```

Type of the inward swipe event. The value is fixed at **SwipeInward**.

**Type:** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**Since:** 12

<!--Device-SwipeInward-type: ActionType--><!--Device-SwipeInward-type: ActionType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## x

```TypeScript
x: number
```

X-coordinate of the swipe event trigger point, in pixels.

**Type:** number

**Since:** 12

<!--Device-SwipeInward-x: int--><!--Device-SwipeInward-x: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## y

```TypeScript
y: number
```

Y-coordinate of the swipe event trigger point, in pixels.

**Type:** number

**Since:** 12

<!--Device-SwipeInward-y: int--><!--Device-SwipeInward-y: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
