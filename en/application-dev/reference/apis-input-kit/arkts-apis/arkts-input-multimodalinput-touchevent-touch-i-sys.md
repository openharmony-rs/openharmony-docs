# Touch

```TypeScript
export declare interface Touch
```

Defines the touch point information.

**Since:** 9

<!--Device-unnamed-export declare interface Touch--><!--Device-unnamed-export declare interface Touch-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## blobId

```TypeScript
blobId?: number
```

Attribute identifier of the touch point. Currently, only single-finger touch is supported: the value is 1 for a left-hand touch and 2 for a right-hand touch. By default, the system automatically identifies the value. By default, this attribute is not set.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-Touch-blobId?: int--><!--Device-Touch-blobId?: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## fixedDisplayX

```TypeScript
fixedDisplayX?: number
```

Correction value of the screenX coordinate in one-handed mode, in pixels. The default value is 0.

**Type:** number

**Since:** 19

<!--Device-Touch-fixedDisplayX?: int--><!--Device-Touch-fixedDisplayX?: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## fixedDisplayY

```TypeScript
fixedDisplayY?: number
```

Correction value of the screenY coordinate in one-handed mode, in pixels. The default value is 0.

**Type:** number

**Since:** 19

<!--Device-Touch-fixedDisplayY?: int--><!--Device-Touch-fixedDisplayY?: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
