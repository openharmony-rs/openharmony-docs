# ReqPermissionDetail


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> ReqPermissionDetail instead.

Provides the detailed information of the permissions to request from the system.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** bundleInfo

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

**System capability:** SystemCapability.BundleManager.BundleFramework
