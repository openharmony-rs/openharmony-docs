# @system.device

This module provides information about the current device.
 It reads system configurations to obtain basic information such as the device brand,
 model, manufacturer, and screen parameters,
 which can be used for device adaptation and function determination.

> **NOTE**
 >
 > - Module maintenance strategy:
 >
 >    \- For lite wearables, this module is constantly maintained and available.
 >
 >    \- For other device types, this module is no longer maintained since API version 6,
 >       and you are advised to use @ohos.deviceInfo (supported since API version 6)
 >       to query device information.
 >
 > - The initial APIs of this module are supported since API version 3.
 >   Newly added APIs will be marked with a superscript to indicate their earliest API version.



## Modules to Import

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Device](arkts-basicservices-system-device-device-c.md) | getInfo interface |

### Interfaces

| Name | Description |
| --- | --- |
| [DeviceResponse](arkts-basicservices-system-device-deviceresponse-i.md) | Defines the device profile information. |
| [GetDeviceOptions](arkts-basicservices-system-device-getdeviceoptions-i.md) | Defines the parameters for obtaining the device information. |
