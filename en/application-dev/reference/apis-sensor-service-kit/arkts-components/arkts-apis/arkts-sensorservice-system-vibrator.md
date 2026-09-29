# @system.vibrator(Vibration control module)

The **@system.vibrator** module provides the capability of controlling the vibration of a device. You can use this
 module to trigger the device to perform long or short vibration effects, providing tactile feedback for users. It is
 mainly used in interaction scenarios that require tactile feedback, such as alarm clock, power-off vibration, and
 incoming call vibration. It helps apps attract users' attention through vibration when key events occur.
 This module is applicable to lite wearables. For other device types, this module is not maintained since API version
 8.
 Compared with the [@ohos.vibrator](arkts-sensorservice-vibrator.md) module, this module provides simpler functions and
 does not support advanced functions such as querying vibration effects, querying the vibrator list, and customizing
 vibration files. For lite wearable devices, this module is continuously maintained. For other device types, this
 module is no longer maintained since API version 8. You are advised to use the
 [vibrator.startVibration()](arkts-sensorservice-vibrator-startvibration-f.md)
 API of the [@ohos.vibrator](arkts-sensorservice-vibrator.md) module. This API supports more vibration effects (
 including [VibrateTime](arkts-sensorservice-vibrator-vibratetime-i.md),
 [VibratePreset](arkts-sensorservice-vibrator-vibratepreset-i.md), and
 [VibrateFromFile](arkts-sensorservice-vibrator-vibratefromfile-i.md)) and is applicable to more device types.

> **NOTE**

> - Module maintenance policy:
 >  >   - For lite wearables, this module is constantly maintained and available.
 >  >   - For other device types, this module is no longer maintained since API version 8, and you are advised to use
 > the new [@ohos.vibrator (Vibrator)](arkts-sensorservice-vibrator.md) module.
 > - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a
 > superscript to indicate their earliest API version.
 > - This module requires hardware support and can only be debugged on real devices. You can check whether the device
 > supports the vibration function by querying the system device information or using related APIs.



## Modules to Import

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Vibrator](arkts-sensorservice-system-vibrator-vibrator-c.md) | Provides static methods for triggering device vibration. |

### Interfaces

| Name | Description |
| --- | --- |
| [VibrateOptions](arkts-sensorservice-system-vibrator-vibrateoptions-i.md) | Defines the configuration parameters for triggering device vibration, including the vibration mode and callback function. When calling [Vibrator.vibrate()](arkts-sensorservice-vibrator-vibrate-f.md), you can use **VibrateOptions** to specify the vibration mode (short or long vibration) and the callback function for listening for the vibration triggering success, failure, and completion events. After **VibrateOptions** is passed, the device vibrates in the specified mode. When the vibration is successfully triggered, the **success** function is called back. If the vibration fails to be triggered, the **fail** function is called back. When the API call is complete, the **complete** function is called back. |
