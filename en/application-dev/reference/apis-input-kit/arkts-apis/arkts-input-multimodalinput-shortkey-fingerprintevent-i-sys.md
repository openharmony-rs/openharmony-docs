# FingerprintEvent (System API)

```TypeScript
export declare interface FingerprintEvent
```

Provides fingerprint gesture event types and the offset of the fingerprint sensor relative to the side edge.

**Since:** 12

<!--Device-unnamed-export declare interface FingerprintEvent--><!--Device-unnamed-export declare interface FingerprintEvent-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { shortKey } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';
```

## action

```TypeScript
action: FingerprintAction
```

Enumeration of fingerprint gesture event types.

**Type:** [FingerprintAction](arkts-input-multimodalinput-shortkey-fingerprintaction-e-sys.md)

**Since:** 12

<!--Device-FingerprintEvent-action: FingerprintAction--><!--Device-FingerprintEvent-action: FingerprintAction-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## distanceX

```TypeScript
distanceX: number
```

Offset of the X axis for the fingerprint sensor relative to the side edge (a positive number indicates that a rightward offset, and a negative number indicates a leftward offset).

**Type:** number

**Since:** 12

<!--Device-FingerprintEvent-distanceX: double--><!--Device-FingerprintEvent-distanceX: double-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## distanceY

```TypeScript
distanceY: number
```

Offset of the Y axis for the fingerprint sensor relative to the side edge (a positive number indicates an upward offset, and a negative number indicates a downward offset).

**Type:** number

**Since:** 12

<!--Device-FingerprintEvent-distanceY: double--><!--Device-FingerprintEvent-distanceY: double-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
