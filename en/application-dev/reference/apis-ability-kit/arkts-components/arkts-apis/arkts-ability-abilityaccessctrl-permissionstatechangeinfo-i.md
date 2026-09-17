# PermissionStateChangeInfo

Represents the permission state change details.

**Since:** 18

**System capability:** SystemCapability.Security.AccessToken

## Modules to Import

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## change

```TypeScript
change: PermissionStateChangeType
```

Operation that triggers the permission state change.

**Type:** [PermissionStateChangeType](arkts-ability-abilityaccessctrl-permissionstatechangetype-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.AccessToken

## permissionName

```TypeScript
permissionName: Permissions
```

Permissions whose authorization state changes. For details about the permissions, see [Application Permissions](../../../security/AccessToken/app-permissions.md).

**Type:** [Permissions](arkts-ability-permissions-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.AccessToken

## tokenID

```TypeScript
tokenID: number
```

ID of the subscribed application, which can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md).

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Security.AccessToken
