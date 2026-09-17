# TransientParam

Defines the parameters for transient vibration.

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## frequency

```TypeScript
frequency?: number
```

Vibration frequency. This parameter is optional. The value range is [0,100]. If this parameter is left empty, the default value is **50**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## index

```TypeScript
index?: number
```

Channel number. This parameter is optional. The value range is [0,2]. If this parameter is left empty, the default value is **0**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: number
```

Vibration intensity. This parameter is optional. The value range is [0,100]. If this parameter is left empty, the default value is **100**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice
