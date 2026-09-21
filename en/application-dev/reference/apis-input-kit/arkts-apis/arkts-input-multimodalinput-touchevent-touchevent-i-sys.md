# TouchEvent

```TypeScript
export declare interface TouchEvent extends InputEvent
```

Defines a touch event.

**Inheritance/Implementation:** TouchEvent extends [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md)

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## fixedMode

```TypeScript
fixedMode?: FixedMode
```

Coordinate correction mode.

**Type:** [FixedMode](arkts-input-multimodalinput-touchevent-fixedmode-e-sys.md)

**Since:** 19

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## isInject

```TypeScript
isInject?: boolean
```

Whether the touch event is an injection event. For details about injection events, see [@ohos.multimodalInput.inputEventClient](arkts-input-multimodalinput-inputeventclient.md).

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
