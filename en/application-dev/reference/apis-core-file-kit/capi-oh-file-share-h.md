# oh_file_share.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c64d2c1f172d9dc3e2eb14c8f94152b166d857bb translatedAt=2026-11-03T03:49:44.140Z pushedAt=2026-11-04T03:11:33.471Z nl=1 -->

## Overview

Provides URI-based methods for persistent authorization of files and directories, cancellation of persistent authorization, permission activation, and permission query, applicable to cross-application file sharing scenarios. Persistent authorization is used to save access policies, and permission activation is used to make the persisted permissions take effect.

**File to include**: <filemanagement/fileshare/oh_file_share.h>

**Library**: libohfileshare.so

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Since**: 12

**Related module**: [fileShare](capi-fileshare.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) | FileShare_PolicyErrorResult | URI policy result for failed grant or activation of permission. |
| [FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) | FileShare_PolicyInfo | Represents the permission policy information. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [FileShare_OperationMode](#fileshare_operationmode) | FileShare_OperationMode | Enumerates the URI operation mode.|
| [FileShare_PolicyErrorCode](#fileshare_policyerrorcode) | FileShare_PolicyErrorCode | Error code corresponding to the URI for which the grant or activation of the permission policy failed. |

### Functions

| Name| Description|
| -- | -- |
| [FileManagement_ErrCode OH_FileShare_PersistPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_persistpermission) | Persists the permissions on files or directories.|
| [FileManagement_ErrCode OH_FileShare_RevokePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_revokepermission) | Revokes the permissions from files or directories.|
| [FileManagement_ErrCode OH_FileShare_ActivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_activatepermission) | Activates multiple files or directories that have been granted persistent authorization. |
| [FileManagement_ErrCode OH_FileShare_DeactivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)](#oh_fileshare_deactivatepermission) | Deactivates multiple files or directories that have been granted persistent authorization. |
| [FileManagement_ErrCode OH_FileShare_CheckPersistentPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, bool **result, unsigned int *resultNum)](#oh_fileshare_checkpersistentpermission) | Checks the persistent permissions on files or directories.|
| [void OH_FileShare_ReleasePolicyErrorResult(FileShare_PolicyErrorResult *errorResult, unsigned int resultNum)](#oh_fileshare_releasepolicyerrorresult) | Releases the memory, to which **FileShare_PolicyErrorResult** points.|

## Enum Description

### FileShare_OperationMode

```c
enum FileShare_OperationMode
```

**Description**

Enumerates the URI operation mode.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| READ_MODE = 1 << 0 | Read permission. It can be used alone or combined with WRITE_MODE. |
| WRITE_MODE = 1 << 1 | Write permission. It can be used alone or combined with READ_MODE. |

### FileShare_PolicyErrorCode

```c
enum FileShare_PolicyErrorCode
```

**Description**

Error code corresponding to the URI for which granting or activating the permission policy failed.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| PERSISTENCE_FORBIDDEN = 1 | The URI is forbidden from being persisted, for example, a remote URI does not support persistence. |
| INVALID_MODE = 2 | Invalid mode, for example, the permission mode value is not within the supported range. |
| INVALID_PATH = 3 | Invalid path.|
| PERMISSION_NOT_PERSISTED = 4 | The permission is not persisted.|


## Function Description

### OH_FileShare_PersistPermission()

```c
FileManagement_ErrCode OH_FileShare_PersistPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Grants persistent authorization to the selected multiple file or directory URIs. After the persistent authorization is complete, you can call [OH_FileShare_ActivatePermission()](#oh_fileshare_activatepermission) to activate the permission.

**Required permissions**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Pointer to a FileShare_PolicyInfo instance array, indicating the URI policy information of the file or directory that requires persistence grant authorization. |
| unsigned int policyNum | Number of elements in the FileShare_PolicyInfo instance array. The value range is [1, 500]. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output parameter, pointing to a FileShare_PolicyErrorResult array pointer. Please use OH_FileShare_ReleasePolicyErrorResult() to perform resource release. |
| unsigned int *resultNum | Output parameter, indicating the number of elements in the FileShare_PolicyErrorResult array. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>         ERR_INVALID_PARAMETER 401 - The input parameter is invalid. Possible causes:<br>             1. The **policies**, **result**, or **resultNum** parameter is a null pointer.<br>             2. The value of **policyNum** is **0** or exceeds the maximum length (500).<br>             3. The value of **uri** in the **policies** parameter is empty, the value of **length** is **0**, or the value of **uri** is different from the value of **length**.<br>         ERR_DEVICE_NOT_SUPPORTED 801 - The device does not support this API.<br>         ERR_PERMISSION_ERROR 201 - The permission verification fails.<br>         ERR_ENOMEM 13900011 - The memory allocation or copy fails.<br>         ERR_EPERM 13900001 - The operation is not allowed.<br>         ERR_OK 0 - The API is called successfully.|

### OH_FileShare_RevokePermission()

```c
FileManagement_ErrCode OH_FileShare_RevokePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Cancels the persistent authorization for the selected multiple file or directory URIs. Before calling this interface, you must first complete the persistent authorization.

**Required permissions**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Pointer to the FileShare_PolicyInfo instance array, indicating the file or directory URI policy information for which persistent authorization needs to be canceled. |
| unsigned int policyNum | Number of elements in the FileShare_PolicyInfo instance array. The value range is [1, 500]. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output parameter, pointing to the FileShare_PolicyErrorResult array pointer. Please use OH_FileShare_ReleasePolicyErrorResult() to release resources. |
| unsigned int *resultNum | Output parameter, indicating the number of elements in the FileShare_PolicyErrorResult array. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns the FileManagement module error code [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>         ERR_INVALID_PARAMETER 401 - The input parameter is invalid. Possible causes are as follows:<br>             1. The parameter policies, result, or resultNum is a null pointer;<br>             2. The value of the parameter policyNum is 0 or exceeds the maximum length (500);<br>             3. The uri carried in the parameter policies is null, or its length is 0, or the length of the uri is inconsistent with length.<br>         ERR_DEVICE_NOT_SUPPORTED 801 - The current device type does not support this interface.<br>         ERR_PERMISSION_ERROR 201 - Interface permission verification failed.<br>         ERR_ENOMEM 13900011 - Failed to allocate or copy memory.<br>         ERR_EPERM 13900001 - The operation is not allowed.<br>         ERR_OK 0 - The interface call is successful. |

### OH_FileShare_ActivatePermission()

```c
FileManagement_ErrCode OH_FileShare_ActivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Activates multiple files or directories that have been granted persistent authorization. Before calling this interface, you must first call [OH_FileShare_PersistPermission()](#oh_fileshare_persistpermission) to complete the persistent authorization. The permission takes effect after activation.

**Required permissions**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Pointer to the FileShare_PolicyInfo instance array, indicating the URI policy information of the file or directory for which permission needs to be activated. |
| unsigned int policyNum | Number of elements in the FileShare_PolicyInfo instance array. The value range is [1, 500]. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output parameter, pointing to the FileShare_PolicyErrorResult array pointer. Please use OH_FileShare_ReleasePolicyErrorResult() to perform resource release. |
| unsigned int *resultNum | Output parameter, indicating the number of elements in the FileShare_PolicyErrorResult array. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>         ERR_INVALID_PARAMETER 401 - The input parameter is invalid. Possible causes:<br>             1. The **policies**, **result**, or **resultNum** parameter is a null pointer.<br>             2. The value of **policyNum** is **0** or exceeds the maximum length (500).<br>             3. The value of **uri** in the **policies** parameter is empty, the value of **length** is **0**, or the value of **uri** is different from the value of **length**.<br>         ERR_DEVICE_NOT_SUPPORTED 801 - The device does not support this API.<br>         ERR_PERMISSION_ERROR 201 - The permission verification fails.<br>         ERR_ENOMEM 13900011 - The memory allocation or copy fails.<br>         ERR_EPERM 13900001 - The operation is not allowed.<br>         ERR_OK 0 - The API is called successfully.|

### OH_FileShare_DeactivatePermission()

```c
FileManagement_ErrCode OH_FileShare_DeactivatePermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, FileShare_PolicyErrorResult **result, unsigned int *resultNum)
```

**Description**

Deactivates multiple files or directories that have been granted persistent authorization. Before calling this interface, you must first call [OH_FileShare_ActivatePermission()](#oh_fileshare_activatepermission) to activate the permission. After deactivation, the persistent authorization is still retained.

**Required permissions**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Pointer to the FileShare_PolicyInfo instance array, indicating the URI policy information of the file or directory for which the permission is to be deactivated. |
| unsigned int policyNum | Number of elements in the FileShare_PolicyInfo instance array. The value range is [1, 500]. |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) **result | Output parameter, pointing to the FileShare_PolicyErrorResult array pointer. Use OH_FileShare_ReleasePolicyErrorResult() to release resources. |
| unsigned int *resultNum | Output parameter, indicating the number of elements in the FileShare_PolicyErrorResult array. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>         ERR_INVALID_PARAMETER 401 - The input parameter is invalid. Possible causes:<br>             1. The **policies**, **result**, or **resultNum** parameter is a null pointer.<br>             2. The value of **policyNum** is **0** or exceeds the maximum length (500).<br>             3. The value of **uri** in the **policies** parameter is empty, the value of **length** is **0**, or the value of **uri** is different from the value of **length**.<br>         ERR_DEVICE_NOT_SUPPORTED 801 - The device does not support this API.<br>         ERR_PERMISSION_ERROR 201 - The permission verification fails.<br>         ERR_ENOMEM 13900011 - The memory allocation or copy fails.<br>         ERR_EPERM 13900001 - The operation is not allowed.<br>         ERR_OK 0 - The API is called successfully.|

### OH_FileShare_CheckPersistentPermission()

```c
FileManagement_ErrCode OH_FileShare_CheckPersistentPermission(const FileShare_PolicyInfo *policies, unsigned int policyNum, bool **result, unsigned int *resultNum)
```

**Description**

Verifies the persistent authorization of the selected multiple file or directory URIs. You can call this interface before activating the permission to confirm whether the target URI has completed persistent authorization.

**Required permissions**: ohos.permission.FILE_ACCESS_PERSIST

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const FileShare_PolicyInfo](capi-fileshare-fileshare-policyinfo.md) *policies | Pointer to an array of FileShare_PolicyInfo instances, indicating the file or directory URI policy information for which persistent authorization needs to be verified. |
| unsigned int policyNum | Number of elements in the FileShare_PolicyInfo instance array. The value range is [1, 500]. |
| bool **result | Output parameter, a pointer to the authorization verification result array. The array elements correspond one-to-one with the elements of the policies array. true indicates that persistent authorization is granted; false indicates that persistent authorization is not granted. After the interface is successfully called, include the header file stdlib.h and use free() to release this array. |
| unsigned int *resultNum | Output parameter, indicating the number of elements in the verification result array. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>         ERR_INVALID_PARAMETER 401 - The input parameter is invalid. Possible causes:<br>             1. The **policies**, **result**, or **resultNum** parameter is a null pointer.<br>             2. The value of **policyNum** is **0** or exceeds the maximum length (500).<br>             3. The value of **uri** in the **policies** parameter is empty, the value of **length** is **0**, or the value of **uri** is different from the value of **length**.<br>         ERR_DEVICE_NOT_SUPPORTED 801 - The device does not support this API.<br>         ERR_PERMISSION_ERROR 201 - The permission verification fails.<br>         ERR_ENOMEM 13900011 - The memory allocation or copy fails.<br>         ERR_EPERM 13900001 - The operation is not allowed. All URIs carried in **policies** do not meet the specifications, or the path converted from the URI does not exist.<br>         ERR_OK 0 - The API is called successfully.|

### OH_FileShare_ReleasePolicyErrorResult()

```c
void OH_FileShare_ReleasePolicyErrorResult(FileShare_PolicyErrorResult *errorResult, unsigned int resultNum)
```

**Description**

Releases the memory resources pointed to by the FileShare_PolicyErrorResult pointer. This resource is output through result by OH_FileShare_PersistPermission, OH_FileShare_RevokePermission, OH_FileShare_ActivatePermission, and OH_FileShare_DeactivatePermission.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [FileShare_PolicyErrorResult](capi-fileshare-fileshare-policyerrorresult.md) *errorResult | Pointer to the FileShare_PolicyErrorResult instance array. |
| unsigned int resultNum | Number of elements in the FileShare_PolicyErrorResult instance array. |
