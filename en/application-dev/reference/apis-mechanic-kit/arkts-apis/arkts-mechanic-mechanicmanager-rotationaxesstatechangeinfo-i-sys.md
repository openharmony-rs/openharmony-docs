# RotationAxesStateChangeInfo (System API)

```TypeScript
export interface RotationAxesStateChangeInfo
```

Rotation axes state change information. @typedef RotationAxesStateChangeInfo

**Since:** 20

<!--Device-mechanicManager-export interface RotationAxesStateChangeInfo--><!--Device-mechanicManager-export interface RotationAxesStateChangeInfo-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## mechId

```TypeScript
mechId: number
```

ID of the mechanical device.

**Type:** number

**Since:** 20

<!--Device-RotationAxesStateChangeInfo-mechId: int--><!--Device-RotationAxesStateChangeInfo-mechId: int-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## status

```TypeScript
status: RotationAxesStatus
```

Rotate axis status.

**Type:** [RotationAxesStatus](arkts-mechanic-mechanicmanager-rotationaxesstatus-i-sys.md)

**Since:** 20

<!--Device-RotationAxesStateChangeInfo-status: RotationAxesStatus--><!--Device-RotationAxesStateChangeInfo-status: RotationAxesStatus-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
