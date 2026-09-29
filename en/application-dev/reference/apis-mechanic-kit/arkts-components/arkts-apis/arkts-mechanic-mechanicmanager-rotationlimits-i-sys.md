# RotationLimits (System API)

```TypeScript
export interface RotationLimits
```

Rotation angle limits relative to the reference point. @typedef RotationLimits

**Since:** 20

<!--Device-mechanicManager-export interface RotationLimits--><!--Device-mechanicManager-export interface RotationLimits-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## negativePitchMax

```TypeScript
negativePitchMax: number
```

Maximum pitch rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-negativePitchMax: double--><!--Device-RotationLimits-negativePitchMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## negativeRollMax

```TypeScript
negativeRollMax: number
```

Maximum roll rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-negativeRollMax: double--><!--Device-RotationLimits-negativeRollMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## negativeYawMax

```TypeScript
negativeYawMax: number
```

Maximum yaw rotation angles in the negative direction, ranging from -2*Math.PI to 0, measured in radians. If the value is less than or equal to -2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-negativeYawMax: double--><!--Device-RotationLimits-negativeYawMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## positivePitchMax

```TypeScript
positivePitchMax: number
```

Maximum pitch rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-positivePitchMax: double--><!--Device-RotationLimits-positivePitchMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## positiveRollMax

```TypeScript
positiveRollMax: number
```

Maximum roll rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-positiveRollMax: double--><!--Device-RotationLimits-positiveRollMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## positiveYawMax

```TypeScript
positiveYawMax: number
```

Maximum yaw rotation angles in the positive direction, ranging from 0 to 2*Math.PI, measured in radians. If the value is greater than or equal to 2*Math.PI, there is no restriction.

**Type:** number

**Since:** 20

<!--Device-RotationLimits-positiveYawMax: double--><!--Device-RotationLimits-positiveYawMax: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
