# VibrateOptions

Defines the vibration options.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)

**Required permissions:** ohos.permission.VIBRATE

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## Modules to Import

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when the API call is complete.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Called when the API call fails.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: () => void
```

Called when the vibrator data changes.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## mode

```TypeScript
mode?: 'number' | 'short'
```

Vibration mode. The value **long** indicates long vibration, and **short** indicates short vibration. The default value is **long**.

**Type:** 'number' &#124; 'short'

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.MiscDevice.Lite
