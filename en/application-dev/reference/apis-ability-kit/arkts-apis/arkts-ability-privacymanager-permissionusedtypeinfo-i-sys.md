# PermissionUsedTypeInfo (System API)

Represents detailed information about the use of a permission.

**Since:** 12

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

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## tokenId

```TypeScript
tokenId: number
```

Token ID of the application that accesses the sensitive permission.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## usedType

```TypeScript
usedType: PermissionUsedType
```

Usage type of the sensitive permission.

**Type:** [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
