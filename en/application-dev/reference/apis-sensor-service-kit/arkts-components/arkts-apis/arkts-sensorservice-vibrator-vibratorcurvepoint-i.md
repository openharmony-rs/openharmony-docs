# VibratorCurvePoint

```TypeScript
interface VibratorCurvePoint
```

Defines the gain relative to the vibration intensity.

**Since:** 18

<!--Device-vibrator-interface VibratorCurvePoint--><!--Device-vibrator-interface VibratorCurvePoint-End-->

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

<!--Device-VibratorCurvePoint-frequency?: int--><!--Device-VibratorCurvePoint-frequency?: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## intensity

```TypeScript
intensity?: number
```

Gain relative to the vibration intensity. This parameter is optional. The value range is [0,100%]. If this parameter is left empty, the default value is **1**.

**Type:** number

**Since:** 18

<!--Device-VibratorCurvePoint-intensity?: double--><!--Device-VibratorCurvePoint-intensity?: double-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: number
```

Start time offset, in milliseconds.

**Type:** number

**Since:** 18

<!--Device-VibratorCurvePoint-time: int--><!--Device-VibratorCurvePoint-time: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
