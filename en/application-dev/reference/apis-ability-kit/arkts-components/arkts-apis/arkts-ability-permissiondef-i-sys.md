# PermissionDef (System API)

```TypeScript
export interface PermissionDef
```

The module provides permission details defined in the [module.json5](../../../quick-start/module-configuration-file.md) file. The information can be obtained using [bundleManager.getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md).

> **NOTE:** 
> 
> The APIs provided by this module are system APIs.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## descriptionId

```TypeScript
readonly descriptionId: number
```

ID of the permission description.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## grantMode

```TypeScript
readonly grantMode: number
```

[Grant mode of the permission](../../../security/AccessToken/app-permission-mgmt-overview.md#authorization-mode). The value **0** means user authorization, and **1** means system authorization.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## labelId

```TypeScript
readonly labelId: number
```

ID of the permission label.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## permissionName

```TypeScript
readonly permissionName: string
```

Name of the permission.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
