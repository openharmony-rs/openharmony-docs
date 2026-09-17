# @ohos.enterprise.deviceControl(Device Control Management)

This module provides device control capabilities for enterprise device management scenarios. Administrators can remotely control devices through this module, including operations such as device restart, shutdown, screen lock, and factory reset, helping enterprises achieve unified device management and security control.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { deviceControl } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [operateDevice](arkts-mdm-devicecontrol-operatedevice-f.md) | Allows administrators to perform operations such as factory reset, restart, shutdown, and screen lock on devices. For example, in enterprise device management scenarios, administrators can remotely control employee devices to perform factory reset, restart, shutdown, or screen lock operations. |
| [operateDevice](arkts-mdm-devicecontrol-operatedevice-f.md) | Allows the administrator to operate devices, for example, erasing disks. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [lockScreen](arkts-mdm-devicecontrol-lockscreen-f-sys.md) | Locks the device screen immediately. |
| [reboot](arkts-mdm-devicecontrol-reboot-f-sys.md) | Reboots the device. |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f-sys.md) | Restores factory settings. This API uses an asynchronous callback to return the result. |
| [resetFactory](arkts-mdm-devicecontrol-resetfactory-f-sys.md) | Restores factory settings. This API uses a promise to return the result. |
| [shutdown](arkts-mdm-devicecontrol-shutdown-f-sys.md) | Shuts down the device. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Operation](arkts-mdm-devicecontrol-operation-e.md) | Defines the device operation. |
