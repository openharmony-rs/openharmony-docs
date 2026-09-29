# VibratorStatusEvent

```TypeScript
interface VibratorStatusEvent
```

Defines the vibrator status change event.

**Since:** 19

<!--Device-vibrator-interface VibratorStatusEvent--><!--Device-vibrator-interface VibratorStatusEvent-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId: number
```

Device ID.

**Type:** number

**Since:** 19

<!--Device-VibratorStatusEvent-deviceId: int--><!--Device-VibratorStatusEvent-deviceId: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## isVibratorOnline

```TypeScript
isVibratorOnline: boolean
```

Vibrator status. The value **true** indicates that the device is online, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 19

<!--Device-VibratorStatusEvent-isVibratorOnline: boolean--><!--Device-VibratorStatusEvent-isVibratorOnline: boolean-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## timestamp

```TypeScript
timestamp: number
```

Timestamp when the event is reported, in milliseconds.

**Type:** number

**Since:** 19

<!--Device-VibratorStatusEvent-timestamp: long--><!--Device-VibratorStatusEvent-timestamp: long-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## vibratorCount

```TypeScript
vibratorCount: number
```

Number of vibrators on the device.

**Type:** number

**Since:** 19

<!--Device-VibratorStatusEvent-vibratorCount: int--><!--Device-VibratorStatusEvent-vibratorCount: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
