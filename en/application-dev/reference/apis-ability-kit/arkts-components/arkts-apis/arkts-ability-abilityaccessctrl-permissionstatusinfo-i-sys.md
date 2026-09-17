# PermissionStatusInfo (System API)

Indicates the permission status.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## grantFlags

```TypeScript
grantFlags: number
```

Permission flags. The value range is as follows:  
- 0: The permission is not set by the user.  
- 1: The permission is set by the user. If the permission is not granted, a permission dialog box can be  
displayed again to request authorization.  
- 2: The permission is set by the user. If the permission is not granted, a permission dialog box cannot be  
displayed again to request authorization. The user needs to grant the permission in system settings.  
- 4: The permission is set by the system.  
- 8: The permission is pre-granted by the system and can be revoked.  
- 16: The permission is set by a security control.  
- 32: The permission is fixed by a security policy. The user cannot grant or revoke it.  
- 64: The permission is allowed only when the app is in the foreground during the current lifecycle.  
- 128: The permission is fixed by an administrator policy. The user cannot grant or revoke it, but the  
administrator can unfix it.  
- 256: The permission is unfixed by an administrator policy. The user can grant or revoke it.  
- 512: The permission is restricted by a user policy.  
The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## grantStatus

```TypeScript
grantStatus: GrantStatus
```

Permission authorization status.

**Type:** [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## grantTimestamp

```TypeScript
grantTimestamp?: number
```

Timestamp of the authorization status change. This is an optional field and is returned when the permission status changes. Unit: milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## permissionName

```TypeScript
permissionName: Permissions
```

Permission name.

**Type:** [Permissions](arkts-ability-permissions-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## tokenID

```TypeScript
tokenID: number
```

Application ID. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
