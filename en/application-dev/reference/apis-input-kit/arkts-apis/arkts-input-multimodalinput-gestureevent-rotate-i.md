# Rotate

```TypeScript
export declare interface Rotate
```

Defines a rotation gesture event.

**Since:** 11

<!--Device-unnamed-export declare interface Rotate--><!--Device-unnamed-export declare interface Rotate-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## angle

```TypeScript
angle: number
```

Rotation angle, in degrees.

**Type:** number

**Since:** 11

<!--Device-Rotate-angle: double--><!--Device-Rotate-angle: double-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

Gesture event type, for example, gesture start, gesture update, or gesture end.

**Type:** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**Since:** 11

<!--Device-Rotate-type: ActionType--><!--Device-Rotate-type: ActionType-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
