# @ohos.enterprise.deviceInfo(Device Information Management)

This module provides APIs for enterprise device information management, including obtaining device serial numbers, device names, and SIM card information. Enterprise administrators can use this module to query device details, enabling unified management and tracking of device assets.

**Use cases:**

- Device asset management and tracking  
- Enterprise device compliance check  
- Device information collection and statistics  
- Fault diagnosis and device identification

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDeviceInfo](arkts-mdm-deviceinfo-getdeviceinfo-f.md) | Obtains device information. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getdevicename) | Obtains the device name. This API uses an asynchronous callback to return the result. |
| [getDeviceName](arkts-mdm-deviceinfo-getdevicename-f-sys.md#getdevicename-1) | Obtains the device name. This API uses a promise to return the result. |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getdeviceserial) | Obtains the device serial number. This API uses an asynchronous callback to return the result. |
| [getDeviceSerial](arkts-mdm-deviceinfo-getdeviceserial-f-sys.md#getdeviceserial-1) | Obtains the device serial number. This API uses a promise to return the result. |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getdisplayversion) | Obtains the device version number. This API uses an asynchronous callback to return the result. |
| [getDisplayVersion](arkts-mdm-deviceinfo-getdisplayversion-f-sys.md#getdisplayversion-1) | Obtains the device version number. This API uses a promise to return the result. |
<!--DelEnd-->
