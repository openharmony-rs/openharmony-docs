# Pinch

Defines a pinch event.

**Since:** 10

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

**System capability:** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

Gesture event type, for example, gesture start, gesture update, or gesture end.

**Type:** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**Since:** 10

**System capability:** SystemCapability.MultimodalInput.Input.Core
