# VibrateAttribute

```TypeScript
interface VibrateAttribute
```

Describes the vibration attribute.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 9

<!--Device-vibrator-interface VibrateAttribute--><!--Device-vibrator-interface VibrateAttribute-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

Device ID. The default value is **-1**, indicating the local device. Since API version 19, you can use [getVibratorInfoSync](arkts-sensorservice-vibrator-getvibratorinfosync-f.md) or [on](arkts-sensorservice-vibrator-on-f.md#onvibratorstatechange) to query the device ID. <br>**Atomic service API**: This API can be used in atomic services since API version 19.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-VibrateAttribute-deviceId?: int--><!--Device-VibrateAttribute-deviceId?: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## id

```TypeScript
id?: number
```

Vibrator ID. The default value is **0**.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-VibrateAttribute-id?: int--><!--Device-VibrateAttribute-id?: int-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## usage

```TypeScript
usage: Usage
```

Vibration scenario. The default value is **unknown**. The value must be an enum defined in [Usage](arkts-sensorservice-vibrator-usage-t.md).

**Type:** [Usage](arkts-sensorservice-vibrator-usage-t.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-VibrateAttribute-usage: Usage--><!--Device-VibrateAttribute-usage: Usage-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
