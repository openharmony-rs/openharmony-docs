# VibrateTime

Represents vibration of the specified duration.

**Since:** 9

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## duration

```TypeScript
duration: number
```

Vibration duration, in ms. The value range is (0,1800000]. The maximum vibration duration varies with devices due to different component protection design specifications of drivers provided by different vendors. It is recommended that a single vibration duration be less than or equal to 10s to maximize user experience.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'time'
```

The value is **time**, indicating vibration of the specified duration.

**Type:** 'time'

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice
