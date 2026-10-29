# DLPFileAccess

```TypeScript
export enum DLPFileAccess
```

Enumerates the permissions on a DLP file.

**Since:** 10

<!--Device-dlpPermission-export enum DLPFileAccess--><!--Device-dlpPermission-export enum DLPFileAccess-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_CONTROL

```TypeScript
ATOMIC_CONTROL = 4
```

The user has atomic control on the file, enabling fine-grained permission management via DlpAtomicPermissionType bit masks. This provides more granular control compared to FULL_CONTROL which grants all permissions.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DLPFileAccess-ATOMIC_CONTROL = 4--><!--Device-DLPFileAccess-ATOMIC_CONTROL = 4-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## CONTENT_EDIT

```TypeScript
CONTENT_EDIT = 2
```

Edit the file.

**Since:** 10

<!--Device-DLPFileAccess-CONTENT_EDIT = 2--><!--Device-DLPFileAccess-CONTENT_EDIT = 2-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## FULL_CONTROL

```TypeScript
FULL_CONTROL = 3
```

The user has full control on the file.

**Since:** 10

<!--Device-DLPFileAccess-FULL_CONTROL = 3--><!--Device-DLPFileAccess-FULL_CONTROL = 3-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## NO_PERMISSION

```TypeScript
NO_PERMISSION = 0
```

The user has no permission on the file.

**Since:** 10

<!--Device-DLPFileAccess-NO_PERMISSION = 0--><!--Device-DLPFileAccess-NO_PERMISSION = 0-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## READ_ONLY

```TypeScript
READ_ONLY = 1
```

The user has only the permission to read the file.

**Since:** 10

<!--Device-DLPFileAccess-READ_ONLY = 1--><!--Device-DLPFileAccess-READ_ONLY = 1-End-->

**System capability:** SystemCapability.Security.DataLossPrevention
