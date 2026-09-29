# ReqPermissionDetail

```TypeScript
export interface ReqPermissionDetail
```


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> ReqPermissionDetail instead.

Provides the detailed information of the permissions to request from the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bundleInfo

<!--Device-unnamed-export interface ReqPermissionDetail--><!--Device-unnamed-export interface ReqPermissionDetail-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## name

```TypeScript
name: string
```

Name of the permission to request.

**Type:** string

**Default:** Indicates the name of this required permissions

**Since:** 7

**Deprecated since:** 9

**Substitutes:** name

<!--Device-ReqPermissionDetail-name: string--><!--Device-ReqPermissionDetail-name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## reason

```TypeScript
reason: string
```

Reason for requesting the permission.

**Type:** string

**Default:** Indicates the reason of this required permissions

**Since:** 7

**Deprecated since:** 9

**Substitutes:** reason

<!--Device-ReqPermissionDetail-reason: string--><!--Device-ReqPermissionDetail-reason: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## usedScene

```TypeScript
usedScene: UsedScene
```

Application scenario and timing for using the permission.

**Type:** [UsedScene](arkts-ability-bundleinfo-usedscene-depr-i.md)

**Default:** Indicates the used scene of this required permissions

**Since:** 7

**Deprecated since:** 9

**Substitutes:** usedScene

<!--Device-ReqPermissionDetail-usedScene: UsedScene--><!--Device-ReqPermissionDetail-usedScene: UsedScene-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
