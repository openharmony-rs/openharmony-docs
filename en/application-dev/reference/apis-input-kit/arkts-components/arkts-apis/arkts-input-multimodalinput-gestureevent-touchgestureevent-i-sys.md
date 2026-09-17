# TouchGestureEvent (System API)

Defines a touchscreen gesture event.

**Since:** 18

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## action

```TypeScript
action: TouchGestureAction
```

Enumerates touchscreen gesture types.

**Type:** [TouchGestureAction](arkts-input-multimodalinput-gestureevent-touchgestureaction-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## touches

```TypeScript
touches: Touch[]
```

Touch point information.

**Type:** [Touch](arkts-input-multimodalinput-touchevent-touch-i.md)[]

**Since:** 18

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
