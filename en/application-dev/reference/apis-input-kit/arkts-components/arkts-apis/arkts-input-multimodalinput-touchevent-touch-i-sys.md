# Touch

Defines the touch point information.

**Since:** 9

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## blobId

```TypeScript
blobId?: number
```

Touch point attribute ID. Currently, only single-finger touch is supported. The value **1** indicates left-hand touch, and the value **2** indicates right-hand touch.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## fixedDisplayX

```TypeScript
fixedDisplayX?: number
```

Corrected value of the screenX coordinate in one-hand mode, in px.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## fixedDisplayY

```TypeScript
fixedDisplayY?: number
```

Corrected value of the screenY coordinate in one-hand mode, in px.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
