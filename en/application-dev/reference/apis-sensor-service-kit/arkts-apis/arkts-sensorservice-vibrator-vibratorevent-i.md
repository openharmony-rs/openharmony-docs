# VibratorEvent

Vibration event.

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## duration

```TypeScript
duration?: number
```

Vibration duration. This parameter is optional, in ms. The value range is (0,5000]. The default value is **48** for short vibration and **1000** for long vibration.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## eventType

```TypeScript
eventType: VibratorEventType
```

Vibration event type.

**Type:** [VibratorEventType](arkts-sensorservice-vibrator-vibratoreventtype-e.md)

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

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

## points

```TypeScript
points?: Array<VibratorCurvePoint>
```

Adjustment points of the vibration curve.

**Type:** Array&lt;[VibratorCurvePoint](arkts-sensorservice-vibrator-vibratorcurvepoint-i.md)&gt;

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice

## time

```TypeScript
time: number
```

Vibration start time, in ms. The value range is [0,1800000].

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Sensors.MiscDevice
