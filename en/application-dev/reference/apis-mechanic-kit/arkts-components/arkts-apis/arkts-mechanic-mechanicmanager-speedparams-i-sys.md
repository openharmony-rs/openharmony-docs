# SpeedParams (System API)

```TypeScript
export interface SpeedParams
```

Parameters for moving or turning at a speed.

**Since:** 26.0.0

<!--Device-mechanicManager-export interface SpeedParams--><!--Device-mechanicManager-export interface SpeedParams-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## angle

```TypeScript
angle: number
```

Turning angle, unit degree.

**Type:** number

**Since:** 26.0.0

<!--Device-SpeedParams-angle: double--><!--Device-SpeedParams-angle: double-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## mode

```TypeScript
mode?: MarchingMode
```

Movement mode.

**Type:** [MarchingMode](arkts-mechanic-mechanicmanager-marchingmode-e-sys.md)

**Since:** 26.0.0

<!--Device-SpeedParams-mode?: MarchingMode--><!--Device-SpeedParams-mode?: MarchingMode-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## speed

```TypeScript
speed: number
```

Turning or moving speed, unit cm. The value should be an integer.

**Type:** number

**Since:** 26.0.0

<!--Device-SpeedParams-speed: int--><!--Device-SpeedParams-speed: int-End-->

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
