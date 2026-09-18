# @system.vibrator

The **Vibrator** module provides APIs for controlling LED lights and vibrators. You can use the APIs to query the LED
 light list, vibrator list, and vibration effect, and turn on or off the LED light and the vibrator.

Misc devices refer to LED lights and vibrators on devices. LED lights are mainly used for indication (for example,
 indicating the charging state) and blinking (such as tri-colored lights). Vibrators are mainly used in scenarios such
 as the alarm clock, power-on/off, and incoming call vibration.

> **NOTE**
 >
 > - Module maintenance policy:
 > >   - For lite wearables, this module is constantly maintained and available.
 > >   - For other device types, this module is no longer maintained since API version 8, and You are advised to use
 > the new [@ohos.vibrator](arkts-sensorservice-vibrator.md) module.
 > - The initial APIs of this module are supported since API version 3.
 > Newly added APIs will be marked with a superscript to indicate their earliest API version.
 > - This module requires hardware support and can only be debugged on real devices.



## Modules to Import

```TypeScript
import { Vibrator, VibrateOptions } from '@kit.SensorServiceKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Vibrator](arkts-sensorservice-system-vibrator-vibrator-c.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [VibrateOptions](arkts-sensorservice-system-vibrator-vibrateoptions-i.md) | Defines the vibration options. |
