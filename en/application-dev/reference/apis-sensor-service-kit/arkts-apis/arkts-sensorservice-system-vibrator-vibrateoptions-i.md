# VibrateOptions

```TypeScript
export interface VibrateOptions
```

Defines the configuration parameters for triggering device vibration, including the vibration mode and callback function. When calling [Vibrator.vibrate()](arkts-sensorservice-vibrator-vibrate-f.md), you can use **VibrateOptions** to specify the vibration mode (short or long vibration) and the callback function for listening for the vibration triggering success, failure, and completion events. After **VibrateOptions** is passed, the device vibrates in the specified mode. When the vibration is successfully triggered, the **success** function is called back. If the vibration fails to be triggered, the **fail** function is called back. When the API call is complete, the **complete** function is called back.

> **NOTE:** 
> 
> This API is supported since API version 3 and deprecated since API version 8. You are advised to use
> [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md) instead.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)

**Required permissions:** ohos.permission.VIBRATE

<!--Device-unnamed-export interface VibrateOptions--><!--Device-unnamed-export interface VibrateOptions-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## Modules to Import

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## complete

```TypeScript
complete?: () => void
```

Callback function invoked when the vibration API call is complete. Usage scenarios: Use this callback when you need to perform clearance or status update operations after the vibration API call is complete (regardless of whether the call is successful or fails). If this parameter is not specified, no callback notification will be sent when the API call is complete. Effect: The system calls this callback function regardless of whether the vibration is successfully triggered. No parameter is returned.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

<!--Device-VibrateOptions-complete?: () => void--><!--Device-VibrateOptions-complete?: () => void-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when the vibration fails to be triggered. Use scenarios: This callback is used to obtain error information upon failure to trigger vibration. For example, the permission is not granted or the device does not support vibration. If this parameter is not specified, no callback notification will be sent when the vibration fails to be triggered. Effect: When the vibration fails to be triggered, the system calls this callback function and passes the error information data and error code. The callback function signature is **(data: string, code: number) =&gt; void**, where **data** is the error information string and **code** is the error code number, indicating the specific error type.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

<!--Device-VibrateOptions-fail?: (data: string, code: number) => void--><!--Device-VibrateOptions-fail?: (data: string, code: number) => void-End-->

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

Callback invoked when the vibration is successfully triggered. Use scenarios: This callback is used to send notices upon successful vibration triggering. Effect: After the vibration is successfully triggered, the system calls this callback function. No parameter is returned.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

<!--Device-VibrateOptions-success: () => void--><!--Device-VibrateOptions-success: () => void-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## mode

```TypeScript
mode?: 'number' | 'short'
```

Vibration mode, which specifies the duration type of device vibration. The options include **'long'** (long vibration) and **'short'** (short vibration). The default value is **'long'**. Use scenarios: You can select the vibration mode based on your requirements. For example, use **'long'** for incoming call notifications to continuously remind users, and use **'short'** for button touch feedback to provide instant feedback. If this parameter is not specified, long vibration is performed by default. Restrictions: This parameter applies only to lite wearables.

**Type:** 'number' &#124; 'short'

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

<!--Device-VibrateOptions-mode?: 'long' | 'short'--><!--Device-VibrateOptions-mode?: 'long' | 'short'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite
