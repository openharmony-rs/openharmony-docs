# VibratorCurvePoint

Defines the gain relative to the vibration intensity.

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

Change relative to the vibration frequency. This parameter is optional. The value range is [-100,100]. If this parameter is left empty, the default value is **0**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: number
```

Gain relative to the vibration intensity. This parameter is optional. The value range is [0,100%]. If this parameter is left empty, the default value is **1**.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: number
```

Start time offset, in ms.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice
