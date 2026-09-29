# RotationAngles (System API)

```TypeScript
export interface RotationAngles
```

The rotion angles, relative to the current position. @typedef RotationAngles

**Since:** 20

<!--Device-mechanicManager-export interface RotationAngles--><!--Device-mechanicManager-export interface RotationAngles-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## pitch

```TypeScript
pitch?: number
```

Pitch angle, ranging from -2*Math.PI to 2*Math.PI, measured in radians.

**Type:** number

**Since:** 20

<!--Device-RotationAngles-pitch?: double--><!--Device-RotationAngles-pitch?: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## roll

```TypeScript
roll?: number
```

Roll angle, ranging from -2*Math.PI to 2*Math.PI, measured in radians.

**Type:** number

**Since:** 20

<!--Device-RotationAngles-roll?: double--><!--Device-RotationAngles-roll?: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## yaw

```TypeScript
yaw?: number
```

Yaw angle, ranging from -2*Math.PI to 2*Math.PI, measured in radians.

**Type:** number

**Since:** 20

<!--Device-RotationAngles-yaw?: double--><!--Device-RotationAngles-yaw?: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
