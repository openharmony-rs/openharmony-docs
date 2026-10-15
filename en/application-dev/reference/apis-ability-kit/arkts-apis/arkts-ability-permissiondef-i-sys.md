# PermissionDef (System API)

```TypeScript
export interface PermissionDef
```

The module provides permission details defined in the [module.json5](../../../quick-start/module-configuration-file.md) file. The information can be obtained using [bundleManager.getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md).

**Since:** 9

<!--Device-unnamed-export interface PermissionDef--><!--Device-unnamed-export interface PermissionDef-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## descriptionId

```TypeScript
readonly descriptionId: number
```

Resource ID of the permission description.

**Type:** number

**Since:** 9

<!--Device-PermissionDef-readonly descriptionId: long--><!--Device-PermissionDef-readonly descriptionId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## grantMode

```TypeScript
readonly grantMode: number
```

[Grant mode of the permission](../../../security/AccessToken/app-permission-mgmt-overview.md#authorization-mode). The value **0** means user authorization, and **1** means system authorization.

**Type:** number

**Since:** 9

<!--Device-PermissionDef-readonly grantMode: int--><!--Device-PermissionDef-readonly grantMode: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## labelId

```TypeScript
readonly labelId: number
```

Resource ID of the permission label, used to display the permission name.

**Type:** number

**Since:** 9

<!--Device-PermissionDef-readonly labelId: long--><!--Device-PermissionDef-readonly labelId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## permissionName

```TypeScript
readonly permissionName: string
```

Permission name.

**Type:** string

**Since:** 9

<!--Device-PermissionDef-readonly permissionName: string--><!--Device-PermissionDef-readonly permissionName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
