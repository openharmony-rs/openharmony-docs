# TouchEvent

Defines a touch event.

**Inheritance/Implementation:** TouchEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## action

```TypeScript
action: Action
```

Event type.

**Type:** [Action](arkts-input-multimodalinput-touchevent-action-e.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## sourceType

```TypeScript
sourceType: SourceType
```

Device type of the touch source.

**Type:** [SourceType](arkts-input-multimodalinput-touchevent-sourcetype-e.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## touch

```TypeScript
touch: Touch
```

Current touch point.

**Type:** [Touch](arkts-input-multimodalinput-touchevent-touch-i.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## touches

```TypeScript
touches: Touch[]
```

All touch points.

**Type:** [Touch](arkts-input-multimodalinput-touchevent-touch-i.md)[]

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core
