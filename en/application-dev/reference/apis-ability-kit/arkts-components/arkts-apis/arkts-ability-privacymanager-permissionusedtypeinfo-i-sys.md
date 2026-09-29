# PermissionUsedTypeInfo (System API)

```TypeScript
interface PermissionUsedTypeInfo
```

Represents detailed information about the use of a permission.

**Since:** 12

<!--Device-privacyManager-interface PermissionUsedTypeInfo--><!--Device-privacyManager-interface PermissionUsedTypeInfo-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## permissionName

```TypeScript
permissionName: Permissions
```

Name of the sensitive permission accessed.

**Type:** [Permissions](arkts-ability-permissions-t.md)

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedTypeInfo-permissionName: Permissions--><!--Device-PermissionUsedTypeInfo-permissionName: Permissions-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## tokenId

```TypeScript
tokenId: number
```

Token ID of the application that accesses the sensitive permission.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedTypeInfo-tokenId: int--><!--Device-PermissionUsedTypeInfo-tokenId: int-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## usedType

```TypeScript
usedType: PermissionUsedType
```

Usage type of the sensitive permission.

**Type:** [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md)

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PermissionUsedTypeInfo-usedType: PermissionUsedType--><!--Device-PermissionUsedTypeInfo-usedType: PermissionUsedType-End-->

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
