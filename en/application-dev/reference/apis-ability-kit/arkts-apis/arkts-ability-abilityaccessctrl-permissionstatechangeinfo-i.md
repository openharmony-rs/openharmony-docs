# PermissionStateChangeInfo

```TypeScript
interface PermissionStateChangeInfo
```

Represents the permission state change details.

**Since:** 18

<!--Device-abilityAccessCtrl-interface PermissionStateChangeInfo--><!--Device-abilityAccessCtrl-interface PermissionStateChangeInfo-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PermissionStateChangeInfo-change: PermissionStateChangeType--><!--Device-PermissionStateChangeInfo-change: PermissionStateChangeType-End-->

**System capability:** SystemCapability.Security.AccessToken

## permissionName

```TypeScript
permissionName: Permissions
```

Permissions whose authorization state changes. For details about the permissions, see [Application Permissions](../../../security/AccessToken/app-permissions.md).

**Type:** [Permissions](arkts-ability-permissions-t.md)

**Since:** 18

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PermissionStateChangeInfo-permissionName: Permissions--><!--Device-PermissionStateChangeInfo-permissionName: Permissions-End-->

**System capability:** SystemCapability.Security.AccessToken

## tokenID

```TypeScript
tokenID: number
```

ID of the subscribed application, which can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md).

**Type:** number

**Since:** 18

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-PermissionStateChangeInfo-tokenID: int--><!--Device-PermissionStateChangeInfo-tokenID: int-End-->

**System capability:** SystemCapability.Security.AccessToken
