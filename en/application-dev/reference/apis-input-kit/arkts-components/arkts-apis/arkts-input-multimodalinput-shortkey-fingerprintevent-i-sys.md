# FingerprintEvent (System API)

Provides fingerprint gesture event types and the offset of the fingerprint sensor relative to the side edge.

**Since:** 12

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

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## distanceX

```TypeScript
distanceX: number
```

Offset relative to the short axis of the side fingerprint device (positive values indicate movement to the right, and negative values indicate movement to the left).

**Type:** number

**Since:** 12

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.

## distanceY

```TypeScript
distanceY: number
```

Offset relative to the long axis of the side fingerprint device (positive values indicate upward movement, and negative values indicate downward movement).

**Type:** number

**Since:** 12

**System capability:** SystemCapability.MultimodalInput.Input.Core

**System API:** This is a system API.
