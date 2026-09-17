# VibrateAttribute

Describes the vibration attribute.

**Since:** 9

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

This API can be used in atomic services since API version 19.

**Type:** number

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Sensors.MiscDevice

## id

```TypeScript
id?: number
```

Vibrator ID. The default value is **0**.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice

## usage

```TypeScript
usage: Usage
```

Vibration scenario. The default value is **unknown**. The value must be an enum defined in [Usage](arkts-sensorservice-vibrator-usage-t.md).

**Type:** [Usage](arkts-sensorservice-vibrator-usage-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.MiscDevice
