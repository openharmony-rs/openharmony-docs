# PermissionRequestToggleStatus (System API)

Enumerates the permission toggle states.

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## CLOSED

```TypeScript
CLOSED = 0
```

Indicates that the dialog box for the specified permission is disabled. When an app calls APIs such as [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) to request this permission, no permission dialog box will be displayed.

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## OPEN

```TypeScript
OPEN = 1
```

Indicates that the dialog box for the specified permission is enabled. When an app calls APIs such as [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) to request this permission, a permission dialog box will be displayed normally.

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
