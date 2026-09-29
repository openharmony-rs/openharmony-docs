# ReqPermissionDetail

```TypeScript
export interface ReqPermissionDetail
```

Provides the detailed information of the permissions to request from the system.

> **NOTE:** 
> 
> - If multiple packages of an application have requested the same permission but with different reasons, the system returns only one reason based on a descending priority order: entry HAP feature HAP in-app HSP.

**Since:** 9

<!--Device-unnamed-export interface ReqPermissionDetail--><!--Device-unnamed-export interface ReqPermissionDetail-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
moduleName: string
```

Name of the module that requests the permission.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ReqPermissionDetail-moduleName: string--><!--Device-ReqPermissionDetail-moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## name

```TypeScript
name: string
```

[Name of the permission](../../../security/AccessToken/app-permissions.md) to request.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ReqPermissionDetail-name: string--><!--Device-ReqPermissionDetail-name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## reason

```TypeScript
reason: string
```

Reason for requesting the permission.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ReqPermissionDetail-reason: string--><!--Device-ReqPermissionDetail-reason: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## reasonId

```TypeScript
reasonId: number
```

ID of the reason for requesting the permission.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ReqPermissionDetail-reasonId: long--><!--Device-ReqPermissionDetail-reasonId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## usedScene

```TypeScript
usedScene: UsedScene
```

Use scenario and timing for using the permission.

**Type:** [UsedScene](arkts-ability-bundleinfo-usedscene-i.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ReqPermissionDetail-usedScene: UsedScene--><!--Device-ReqPermissionDetail-usedScene: UsedScene-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
