# AttachStateChangeInfo

```TypeScript
export interface AttachStateChangeInfo
```

Callback information about the device attachment state change. @typedef AttachStateChangeInfo

**Since:** 20

<!--Device-mechanicManager-export interface AttachStateChangeInfo--><!--Device-mechanicManager-export interface AttachStateChangeInfo-End-->

**System capability:** SystemCapability.Mechanic.Core

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## mechInfo

```TypeScript
mechInfo: MechInfo
```

Mechanical device information.

**Type:** [MechInfo](arkts-mechanic-mechanicmanager-mechinfo-i.md)

**Since:** 20

<!--Device-AttachStateChangeInfo-mechInfo: MechInfo--><!--Device-AttachStateChangeInfo-mechInfo: MechInfo-End-->

**System capability:** SystemCapability.Mechanic.Core

## state

```TypeScript
state: AttachState
```

Device attachment state.

**Type:** [AttachState](arkts-mechanic-mechanicmanager-attachstate-e.md)

**Since:** 20

<!--Device-AttachStateChangeInfo-state: AttachState--><!--Device-AttachStateChangeInfo-state: AttachState-End-->

**System capability:** SystemCapability.Mechanic.Core
