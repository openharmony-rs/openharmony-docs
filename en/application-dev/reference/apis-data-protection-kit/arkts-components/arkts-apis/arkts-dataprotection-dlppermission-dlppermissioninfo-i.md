# DLPPermissionInfo

```TypeScript
export interface DLPPermissionInfo
```

Represents the permission information about a DLP file.

**Since:** 10

<!--Device-dlpPermission-export interface DLPPermissionInfo--><!--Device-dlpPermission-export interface DLPPermissionInfo-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## dlpFileAccess

```TypeScript
dlpFileAccess: DLPFileAccess
```

User permission on the DLP file, for example, read-only.

**Type:** [DLPFileAccess](arkts-dataprotection-dlppermission-dlpfileaccess-e.md)

**Since:** 10

<!--Device-DLPPermissionInfo-dlpFileAccess: DLPFileAccess--><!--Device-DLPPermissionInfo-dlpFileAccess: DLPFileAccess-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## flags

```TypeScript
flags: number
```

Operations that can be performed on the DLP file. The value is determined by a combination of different [ActionFlagTypes](arkts-dataprotection-dlppermission-actionflagtype-e.md).

**Type:** number

**Since:** 10

<!--Device-DLPPermissionInfo-flags: number--><!--Device-DLPPermissionInfo-flags: number-End-->

**System capability:** SystemCapability.Security.DataLossPrevention
