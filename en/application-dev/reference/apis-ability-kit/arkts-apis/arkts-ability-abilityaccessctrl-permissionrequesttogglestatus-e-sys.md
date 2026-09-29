# PermissionRequestToggleStatus (System API)

```TypeScript
export enum PermissionRequestToggleStatus
```

Enumerates the permission toggle states.

**Since:** 12

<!--Device-abilityAccessCtrl-export enum PermissionRequestToggleStatus--><!--Device-abilityAccessCtrl-export enum PermissionRequestToggleStatus-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## CLOSED

```TypeScript
CLOSED = 0
```

Indicates that the dialog box for the specified permission is disabled. When an app calls APIs such as [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) to request this permission, no permission dialog box will be displayed.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionRequestToggleStatus-CLOSED = 0--><!--Device-PermissionRequestToggleStatus-CLOSED = 0-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## OPEN

```TypeScript
OPEN = 1
```

Indicates that the dialog box for the specified permission is enabled. When an app calls APIs such as [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) to request this permission, a permission dialog box will be displayed normally.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionRequestToggleStatus-OPEN = 1--><!--Device-PermissionRequestToggleStatus-OPEN = 1-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
