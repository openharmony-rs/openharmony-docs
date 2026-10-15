# Pinch

```TypeScript
export declare interface Pinch
```

Defines a pinch event.

**Since:** 10

<!--Device-unnamed-export declare interface Pinch--><!--Device-unnamed-export declare interface Pinch-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## scale

```TypeScript
scale: number
```

Pinch scale factor. The value is greater than or equal to 0.

**Type:** number

**Since:** 10

<!--Device-Pinch-scale: double--><!--Device-Pinch-scale: double-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

Gesture event type, including gesture cancel, gesture start, gesture update, and gesture end.

**Type:** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**Since:** 10

<!--Device-Pinch-type: ActionType--><!--Device-Pinch-type: ActionType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
