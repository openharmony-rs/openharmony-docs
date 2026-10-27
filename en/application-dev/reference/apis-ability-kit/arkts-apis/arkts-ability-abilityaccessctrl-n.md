# abilityAccessCtrl(Application Access Control)

```TypeScript
declare namespace abilityAccessCtrl
```

Provides permission verification and management capabilities for apps, supporting permission status checks before accessing protected resources, runtime authorization requests, settings page authorization guidance, and permission status change monitoring.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-unnamed-declare namespace abilityAccessCtrl--><!--Device-unnamed-declare namespace abilityAccessCtrl-End-->

**System capability:** SystemCapability.Security.AccessToken

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md#createatmanager-1) | Creates a program access control management instance for scenarios such as permission verification, runtime permission request, settings page authorization guidance, and permission status change monitoring. After the call is successful, an AtManager instance is returned, which can be used for subsequent permission management operations. |

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
| [AutomationControlControllerInfo](arkts-ability-abilityaccessctrl-automationcontrolcontrollerinfo-i-sys.md) | Represents a controller app that has automation control over a target app. |
| [AutomationControlTargetParam](arkts-ability-abilityaccessctrl-automationcontroltargetparam-i-sys.md) | Represents a target app and its automation control status. |
| [AutomationControlTargetResult](arkts-ability-abilityaccessctrl-automationcontroltargetresult-i-sys.md) | Represents a target app and its automation control status with bundle name. Used as the return type of getAutomationControlTargets. |
| [PermissionStatusInfo](arkts-ability-abilityaccessctrl-permissionstatusinfo-i-sys.md) | Indicates the permission status. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md) | Enumerates the permission grant states. |
| [PermissionStateChangeType](arkts-ability-abilityaccessctrl-permissionstatechangetype-e.md) | Enumerates the operations that trigger permission state changes. |
| [PermissionStatus](arkts-ability-abilityaccessctrl-permissionstatus-e.md) | Enumerates the permission states. |
| [SelectedResult](arkts-ability-abilityaccessctrl-selectedresult-e.md) | Enumerates the results of the dialog box for redirection to the settings page. |
| [SwitchType](arkts-ability-abilityaccessctrl-switchtype-e.md) | Enumerates the global switch types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AutomationControlSetResult](arkts-ability-abilityaccessctrl-automationcontrolsetresult-e-sys.md) | Enumerates the results for setting automation control status per target app. |
| [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md) | Enumerates the automation control status values. |
| [PermissionRequestToggleStatus](arkts-ability-abilityaccessctrl-permissionrequesttogglestatus-e-sys.md) | Enumerates the permission toggle states. |
<!--DelEnd-->
