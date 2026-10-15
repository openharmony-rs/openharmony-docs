# PermissionDef (System API)

```TypeScript
export interface PermissionDef
```

The module provides permission details defined in the configuration file.

> **NOTE:** 
> 
> Since API version 9, this module is no longer maintained. You are advised to use
> [PermissionDef](arkts-ability-permissiondef-depr-i-sys.md) instead.
> 
> This module is a system API.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [PermissionDef](arkts-ability-permissiondef-depr-i-sys.md)

<!--Device-unnamed-export interface PermissionDef--><!--Device-unnamed-export interface PermissionDef-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## descriptionId

```TypeScript
descriptionId: number
```

ID of the permission description.

**Type:** number

**Default:** Indicates the descriptionId of this permission

**Since:** 8

**Deprecated since:** 9

**Substitutes:** descriptionId

<!--Device-PermissionDef-descriptionId: number--><!--Device-PermissionDef-descriptionId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## grantMode

```TypeScript
grantMode: number
```

Grant mode of the permission. The value **0** means that the system automatically grants the permission after the application installation, and **1** means that the application needs to dynamically request the permission from the user.

**Type:** number

**Default:** Indicates the grant mode of this permission

**Since:** 8

**Deprecated since:** 9

**Substitutes:** grantMode

<!--Device-PermissionDef-grantMode: number--><!--Device-PermissionDef-grantMode: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## labelId

```TypeScript
labelId: number
```

ID of the permission label.

**Type:** number

**Default:** Indicates the labelId of this permission

**Since:** 8

**Deprecated since:** 9

**Substitutes:** labelId

<!--Device-PermissionDef-labelId: number--><!--Device-PermissionDef-labelId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## permissionName

```TypeScript
permissionName: string
```

Name of the permission.

**Type:** string

**Default:** Indicates the name of this permission

**Since:** 8

**Deprecated since:** 9

**Substitutes:** permissionName

<!--Device-PermissionDef-permissionName: string--><!--Device-PermissionDef-permissionName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.
