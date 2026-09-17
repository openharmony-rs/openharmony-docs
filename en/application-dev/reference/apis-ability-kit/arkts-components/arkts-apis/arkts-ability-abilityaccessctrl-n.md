# abilityAccessCtrl(Application Access Control)

**Since:** 8

**System capability:** SystemCapability.Security.AccessToken

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md) | Creates a program access control management instance for scenarios such as permission verification, runtime permission request, settings page authorization guidance, and permission status change monitoring. After the call is successful, an AtManager instance is returned, which can be used for subsequent permission management operations. |

### Interfaces

| Name | Description |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i.md) | Program access control management class, providing capabilities such as permission verification, runtime permission dialog box request, settings page authorization guidance, global switch request, and permission status monitoring. Obtain an instance through [createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md). |
| [PermissionStateChangeInfo](arkts-ability-abilityaccessctrl-permissionstatechangeinfo-i.md) | Represents the permission state change details. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i-sys.md) | Program access control management class, providing capabilities such as permission verification, runtime permission dialog box request, settings page authorization guidance, global switch request, and permission status monitoring. Obtain an instance through [createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md). |
| [PermissionStatusInfo](arkts-ability-abilityaccessctrl-permissionstatusinfo-i-sys.md) | Indicates the permission status. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md) | Enumerates the permission grant states. |
| [SelectedResult](arkts-ability-abilityaccessctrl-selectedresult-e.md) | Enumerates the results of the dialog box for redirection to the settings page. |
| [PermissionStateChangeType](arkts-ability-abilityaccessctrl-permissionstatechangetype-e.md) | Enumerates the operations that trigger permission state changes. |
| [PermissionStatus](arkts-ability-abilityaccessctrl-permissionstatus-e.md) | Enumerates the permission states. |
| [SwitchType](arkts-ability-abilityaccessctrl-switchtype-e.md) | Enumerates the global switch types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PermissionRequestToggleStatus](arkts-ability-abilityaccessctrl-permissionrequesttogglestatus-e-sys.md) | Enumerates the permission toggle states. |
<!--DelEnd-->
