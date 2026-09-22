# BatteryLevelInfo (System API)

```TypeScript
export interface BatteryLevelInfo
```

Definition of battery level information.

**Since:** 26.2.0

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## batteryLevel

```TypeScript
batteryLevel: number
```

Battery level percentage(in %). The value is an integer in the range [0, 100]. 0 indicates empty battery and 100 indicates full battery.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## isCharging

```TypeScript
isCharging: boolean
```

Indicates whether the device is charging. The value is true when charging and false otherwise.

**Type:** boolean

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## mechId

```TypeScript
mechId: number
```

ID of the mechanical device corresponding to the battery level information.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
