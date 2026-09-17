# VibratorInfoParam

Defines the vibrator parameters. If **VibratorInfoParam** is left unspecified, an API applies to all vibrators of the local device by default.

**Since:** 19

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

Device ID. The default value is **-1**, indicating the local device. Since API version 19, you can use [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md) or [on](arkts-sensorservice-vibrator-on-f.md) to query the device ID.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Sensors.MiscDevice

## vibratorId

```TypeScript
vibratorId?: number
```

Vibrator ID. The default value is **0**, which indicates all vibrators of the local device. Since API version 19, you can use [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md) or [on](arkts-sensorservice-vibrator-on-f.md) to query the vibrator ID.

**Type:** number

**Since:** 19

**System capability:** SystemCapability.Sensors.MiscDevice
