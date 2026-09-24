# oh_file_share.h

## Overview

Provides URI-based file and directory authorization and persistence, permission activation, permission query, and other methods.

**Library**: libohfileshare.so

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) | FileShare_PolicyErrorResult | Define the FileShare_PolicyErrorResult structure type.<br> Failed policy result on URI. |
| [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) | FileShare_PolicyInfo | Define the FileShare_PolicyInfo structure type.<br> Policy information to manager permissions on a URI. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [FileShare_OperationMode](#fileshare_operationmode) | FileShare_OperationMode | Enumerates the uri operate mode types. |
| [FileShare_PolicyErrorCode](#fileshare_policyerrorcode) | FileShare_PolicyErrorCode | Enumerates the error code of the permission policy for the URI operation. |

### Function

| Name | Description |
| -- | -- |
| [FileManagement_ErrCode OH_FileShare_PersistPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_persistpermission) | Set persistent permissions for the URI. |
| [FileManagement_ErrCode OH_FileShare_RevokePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_revokepermission) | Revoke persistent permissions for the URI. |
| [FileManagement_ErrCode OH_FileShare_ActivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_activatepermission) | Enable the URI that have been permanently authorized. |
| [FileManagement_ErrCode OH_FileShare_DeactivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_deactivatepermission) | Stop the authorized URI that has been enabled. |
| [FileManagement_ErrCode OH_FileShare_CheckPersistentPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, bool **result, unsigned int *resultNum)](#oh_fileshare_checkpersistentpermission) | Check persistent permissions for the URI. |
| [void OH_FileShare_ReleasePolicyErrorResult(FileShare_PolicyErrorResult *errorResult, unsigned int resultNum)](#oh_fileshare_releasepolicyerrorresult) | Free FileShare_PolicyErrorResult pointer points to address memory. |

## Enum type description

### FileShare_OperationMode

```c
enum FileShare_OperationMode
```

**Description**

Enumerates the uri operate mode types.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

| Enum item | Description |
| -- | -- |
| READ_MODE = 1 << 0 | Indicates read permissions. |
| WRITE_MODE = 1 << 1 | Indicates write permissions. |

### FileShare_PolicyErrorCode

```c
enum FileShare_PolicyErrorCode
```

**Description**

Enumerates the error code of the permission policy for the URI operation.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

| Enum item | Description |
| -- | -- |
| PERSISTENCE_FORBIDDEN = 1 | Indicates that the policy is not allowed to be persisted. |
| INVALID_MODE = 2 | Indicates that the mode of this policy is invalid. |
| INVALID_PATH = 3 | Indicates that the path of this policy is invalid. |
| PERMISSION_NOT_PERSISTED = 4 | Indicates that the policy is no persistent capability. |


## Function description

### OH_FileShare_PersistPermission()

```c
FileManagement_ErrCode OH_FileShare_PersistPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Set persistent permissions for the URI.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Required permission**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Input a pointer to an [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) instance. |
| unsigned int policyNum | Indicates the size of the policies array. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output a pointer to an [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) instance. Please use OH_FileShare_ReleasePolicyErrorResult() to clear Resource. |
| unsigned int *resultNum | Output the size of the result array. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_PERMISSION_ERROR} 201 - No permission to perform this operation.<br>        {@link ERR_EPERM} 13900001 - operation not permitted.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileShare_RevokePermission()

```c
FileManagement_ErrCode OH_FileShare_RevokePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Revoke persistent permissions for the URI.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Required permission**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Input a pointer to an [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) instance. |
| unsigned int policyNum | Indicates the size of the policies array. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output a pointer to an [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) instance. Please use OH_FileShare_ReleasePolicyErrorResult() to clear Resource. |
| unsigned int *resultNum | Output the size of the result array. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_PERMISSION_ERROR} 201 - No permission to perform this operation.<br>        {@link ERR_EPERM} 13900001 - operation not permitted.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileShare_ActivatePermission()

```c
FileManagement_ErrCode OH_FileShare_ActivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Enable the URI that have been permanently authorized.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Required permission**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Input a pointer to an [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) instance. |
| unsigned int policyNum | Indicates the size of the policies array. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output a pointer to an [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) instance. Please use OH_FileShare_ReleasePolicyErrorResult() to clear Resource. |
| unsigned int *resultNum | Output the size of the result array. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_PERMISSION_ERROR} 201 - No permission to perform this operation.<br>        {@link ERR_EPERM} 13900001 - operation not permitted.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileShare_DeactivatePermission()

```c
FileManagement_ErrCode OH_FileShare_DeactivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Stop the authorized URI that has been enabled.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Required permission**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Input a pointer to an [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) instance. |
| unsigned int policyNum | Indicates the size of the policies array. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output a pointer to an [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) instance. Please use OH_FileShare_ReleasePolicyErrorResult() to clear Resource. |
| unsigned int *resultNum | Output the size of the result array. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_PERMISSION_ERROR} 201 - No permission to perform this operation.<br>        {@link ERR_EPERM} 13900001 - operation not permitted.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileShare_CheckPersistentPermission()

```c
FileManagement_ErrCode OH_FileShare_CheckPersistentPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, bool **result, unsigned int *resultNum)
```

**Description**

Check persistent permissions for the URI.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Required permission**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Input a pointer to an [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) instance. |
| unsigned int policyNum | Indicates the size of the policies array. |
| bool **result | Output a pointer to an bool instance. Please use free() to clear Resource. |
| unsigned int *resultNum | Output the size of the result array. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Returns the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_PERMISSION_ERROR} 201 - No permission to perform this operation.<br>        {@link ERR_EPERM} 13900001 - operation not permitted.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory or failed to copy memory.<br>        {@link ERR_OK} 0 - This operation was successfully executed. |

### OH_FileShare_ReleasePolicyErrorResult()

```c
void OH_FileShare_ReleasePolicyErrorResult(FileShare_PolicyErrorResult *errorResult, unsigned int resultNum)
```

**Description**

Free FileShare_PolicyErrorResult pointer points to address memory.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) *errorResult | Input a pointer to an [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) instance. |
| unsigned int resultNum | Indicates the size of the errorResult array. |


