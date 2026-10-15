# RefuelingInfo

```TypeScript
export interface RefuelingInfo
```

Interface for refueling response info.

**Since:** 26.0.1

<!--Device-carAwareness-export interface RefuelingInfo--><!--Device-carAwareness-export interface RefuelingInfo-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## status

```TypeScript
status: number
```

Refueling status.  
- 1: invalid  
0: idle (refueling is not started) 1: refueling started 2: refueling finished.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-RefuelingInfo-status: number--><!--Device-RefuelingInfo-status: number-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the recognition result. Unit: ms.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-RefuelingInfo-timestamp: number--><!--Device-RefuelingInfo-timestamp: number-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness
