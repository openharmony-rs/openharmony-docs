# @ohos.enterprise.locationManager(Location Service Management)

The **locationManager** module provides location service management capabilities for devices, including setting and obtaining the location service policy.

**Use cases:** This module is applicable to enterprise device management scenarios, where administrators can centrally manage location service policies for devices.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { locationManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md) | Queries the location service policy. |
| [getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md) | Queries the location service policy. This API can be used in enterprise device administrator applications to check the current location service policy state of the device, for policy compliance verification or state confirmation before policy adjustment. It is suitable for scenarios such as confirming the current policy configuration, reading the policy state when the device administrator application starts, and checking the policy when troubleshooting location service issues. |
| [setLocationPolicy](arkts-mdm-locationmanager-setlocationpolicy-f.md) | Sets a location service policy. This API can be used in enterprise management and control scenarios. For example, you can disable the location service in confidential areas to protect information security, or forcibly enable the location service in logistics and distribution applications to track device locations. |

### Enums

| Name | Description |
| --- | --- |
| [LocationPolicy](arkts-mdm-locationmanager-locationpolicy-e.md) | Enumerates the location service policies. |
