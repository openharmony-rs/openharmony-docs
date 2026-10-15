# Vibrator

```TypeScript
export default class Vibrator
```

Provides static methods for triggering device vibration.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [vibrator/vibrator](arkts-sensorservice-vibrator.md)

**Required permissions:** ohos.permission.VIBRATE

<!--Device-unnamed-export default class Vibrator--><!--Device-unnamed-export default class Vibrator-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

## Modules to Import

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## vibrate

```TypeScript
static vibrate(options?: VibrateOptions): void
```

Triggers the device to vibrate in short or long mode based on the specified vibration mode. This API uses an asynchronous callback to return the result.

Use this API to trigger device vibration such as alarm clock vibration, incoming call vibration, power-off vibration, and button touch feedback on lite wearable devices. After this API is called, the device vibrates in the specified mode (short or long vibration). If the **mode** parameter is not specified, the device will perform long vibration (the default value of **mode** is **'long'**).

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [vibrator.startVibration()](arkts-sensorservice-vibrator-startvibration-f.md#startvibration1)
> since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [startVibration](arkts-sensorservice-vibrator-startvibration-f.md#startvibration1)(effect: VibrateEffect, attribute: VibrateAttribute, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.VIBRATE

**Model restriction:** This API can be used only in the FA model.

<!--Device-Vibrator-static vibrate(options?: VibrateOptions): void--><!--Device-Vibrator-static vibrate(options?: VibrateOptions): void-End-->

**System capability:** SystemCapability.Sensors.MiscDevice.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [VibrateOptions](arkts-sensorservice-system-vibrator-vibrateoptions-i.md) | No | Vibration configuration parameters, which are used to specify the vibration mode and callback function. If this parameter is not specified, the default configuration is used. The default value of **mode** is **'long'**. In this case, only the **success** and **complete** callbacks are triggered, while the **fail** callback will not be triggered. |
