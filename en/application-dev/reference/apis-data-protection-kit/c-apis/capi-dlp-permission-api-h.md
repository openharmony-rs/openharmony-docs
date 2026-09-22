# dlp_permission_api.h

## Overview

Defines the APIs for cross-device file access management, encrypted storage, and access authorization.

**Library**: libohdlp_permission.so

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Related module**: [DlpPermissionApi](capi-dlppermissionapi.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DLP_ErrCode](#dlp_errcode) | DLP_ErrCode | Enumerates the DLP error codes. |
| [DLP_FileAccess](#dlp_fileaccess) | DLP_FileAccess | Enumerates the permissions on a DLP file. |

### Function

| Name | Description |
| -- | -- |
| [DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)](#oh_dlp_getdlppermissioninfo) | Obtains the permission information of this DLP sandbox. |
| [DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char **originalFileName)](#oh_dlp_getoriginalfilename) | Obtains the original file name of a DLP file. |
| [DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)](#oh_dlp_isinsandbox) | Checks whether this application is running in a DLP sandbox environment. |
| [DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)](#oh_dlp_setsandboxappconfig) | Sets sandbox application configuration. |
| [DLP_ErrCode OH_DLP_GetSandboxAppConfig(char **configInfo)](#oh_dlp_getsandboxappconfig) | Obtains the sandbox application configuration. |
| [DLP_ErrCode OH_DLP_CleanSandboxAppConfig()](#oh_dlp_cleansandboxappconfig) | Cleans the sandbox application configuration. |

## Enum type description

### DLP_ErrCode

```c
enum DLP_ErrCode
```

**Description**

Enumerates the DLP error codes.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

| Enum item | Description |
| -- | -- |
| ERR_OH_SUCCESS = 0 | The operation is successful. |
| OH_DLP_NOT_SUPPORTED = 801 |  |
| ERR_OH_INVALID_PARAMETER = 19100001 | Invalid parameters are specified. |
| ERR_OH_API_ONLY_FOR_SANDBOX = 19100006 | The caller is not a DLP sandbox application. |
| ERR_OH_API_NOT_FOR_SANDBOX = 19100007 | The API is not available to a DLP sandbox application. |
| ERR_OH_SYSTEM_SERVICE_EXCEPTION = 19100011 | The system service is abnormal. |
| ERR_OH_OUT_OF_MEMORY = 19100012 | The memory allocation fails. |
| ERR_OH_APPLICATION_NOT_AUTHORIZED = 19100018 | The application is not authorized to perform the operation. |

### DLP_FileAccess

```c
enum DLP_FileAccess
```

**Description**

Enumerates the permissions on a DLP file.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

| Enum item | Description |
| -- | -- |
| NO_PERMISSION = 0 | No permission on the file. |
| READ_ONLY = 1 | Read-only permission. |
| CONTENT_EDIT = 2 | Editing permission. |
| FULL_CONTROL = 3 | Full control. |


## Function description

### OH_DLP_GetDlpPermissionInfo()

```c
DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)
```

**Description**

Obtains the permission information of this DLP sandbox.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| [DLP_FileAccess](capi-dlp-permission-api-h.md#dlp_fileaccess) *dlpFileAccess | [out] User permission on the DLP file, for example, read-only. |
| uint32_t *flags | [out] Pointer to the operation permissions allowed for the DLP file. The options are as follows: <br>**0x00000000** indicates no permission on the file. <br>**0x00000001** indicates the permission for viewing the file. <br>**0x00000002** indicates the permission for saving the file. <br>**0x00000004** indicates the permission for saving the file as another file. <br>**0x00000008** indicates the permission for editing the file. <br>**0x00000010** indicates the permission for capturing screenshots of the file. <br>**0x00000020** indicates the permission for sharing the screen, on which the file is open. <br>**0x00000040** indicates the permission for recording the screen, on which the file is open. <br>**0x00000080** indicates the permission for copying the file. <br>**0x00000100** indicates the permission for printing the file. <br>**0x00000200** indicates the permission for exporting the file. <br>**0x00000400** indicates the permission for modifying the permissions on the file. |

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_INVALID_PARAMETER](capi-dlp-permission-api-h.md#dlp_errcode) 19100001 - If the parameter value is invalid.</li>      <li> [ERR_OH_API_ONLY_FOR_SANDBOX](capi-dlp-permission-api-h.md#dlp_errcode) 19100006 - If no permission to      call this API, which is available only for DLP sandbox applications.</li>      <li> [ERR_OH_SYSTEM_SERVICE_EXCEPTION](capi-dlp-permission-api-h.md#dlp_errcode) 19100011 - If the system ability      works abnormally.</li>      <li> [ERR_OH_OUT_OF_MEMORY](capi-dlp-permission-api-h.md#dlp_errcode) 19100012 - If the memory error.</li></ul> |

### OH_DLP_GetOriginalFileName()

```c
DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char **originalFileName)
```

**Description**

Obtains the original file name of a DLP file.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *fileName | [in] Pointer to the target file whose original file name is to be obtained. The length cannot exceed 256 characters. |
| char **originalFileName | [out] Double pointer to the original file name obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_INVALID_PARAMETER](capi-dlp-permission-api-h.md#dlp_errcode) 19100001 - If the parameter value is invalid.</li>      <li> [ERR_OH_OUT_OF_MEMORY](capi-dlp-permission-api-h.md#dlp_errcode) 19100012 - If the memory error.</li></ul> |

### OH_DLP_IsInSandbox()

```c
DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)
```

**Description**

Checks whether this application is running in a DLP sandbox environment.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| bool *isInSandbox | [out] Returns **true** if the application is running in a DLP sandbox; returns **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_SYSTEM_SERVICE_EXCEPTION](capi-dlp-permission-api-h.md#dlp_errcode) 19100011 - If the system ability      works abnormally.</li>      <li> [ERR_OH_OUT_OF_MEMORY](capi-dlp-permission-api-h.md#dlp_errcode) 19100012 - If the memory error.</li></ul> |

### OH_DLP_SetSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)
```

**Description**

Sets sandbox application configuration.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *configInfo | [in] Pointer to the sandbox application configuration to set. |

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_INVALID_PARAMETER](capi-dlp-permission-api-h.md#dlp_errcode) 19100001 - If the parameter value is invalid.</li>      <li> [ERR_OH_API_NOT_FOR_SANDBOX](capi-dlp-permission-api-h.md#dlp_errcode) 19100007 - If no permission to      call this API, which is available only for non-DLP sandbox applications.</li>      <li> [ERR_OH_SYSTEM_SERVICE_EXCEPTION](capi-dlp-permission-api-h.md#dlp_errcode) 19100011 - If the system ability      works abnormally.</li>      <li> [ERR_OH_APPLICATION_NOT_AUTHORIZED](capi-dlp-permission-api-h.md#dlp_errcode) 19100018 - If the application is not      authorized.</li></ul> |

### OH_DLP_GetSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_GetSandboxAppConfig(char **configInfo)
```

**Description**

Obtains the sandbox application configuration.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **configInfo | [out] Pointer to the sandbox application configuration obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_SYSTEM_SERVICE_EXCEPTION](capi-dlp-permission-api-h.md#dlp_errcode) 19100011 - If the system ability      works abnormally.</li>      <li> [ERR_OH_OUT_OF_MEMORY](capi-dlp-permission-api-h.md#dlp_errcode) 19100012 - If the memory error.</li>      <li> [ERR_OH_APPLICATION_NOT_AUTHORIZED](capi-dlp-permission-api-h.md#dlp_errcode) 19100018 - If the application is not      authorized.</li></ul> |

### OH_DLP_CleanSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_CleanSandboxAppConfig()
```

**Description**

Cleans the sandbox application configuration.

**System capability**: SystemCapability.Security.DataLossPrevention

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| [DLP_ErrCode](capi-dlp-permission-api-h.md#dlp_errcode) | <ul><li>[ERR_OH_SUCCESS](capi-dlp-permission-api-h.md#dlp_errcode) 0 - If the operation is successful.</li>      <li> [OH_DLP_NOT_SUPPORTED](capi-dlp-permission-api-h.md#dlp_errcode) 801 - If the device is car which not support DLP feature.      On API 26.0.1 and above, this error is returned. [since 26.0.1]</li>      <li> [ERR_OH_API_NOT_FOR_SANDBOX](capi-dlp-permission-api-h.md#dlp_errcode) 19100007 - If no permission to      call this API, which is available only for non-DLP sandbox applications.</li>      <li> [ERR_OH_SYSTEM_SERVICE_EXCEPTION](capi-dlp-permission-api-h.md#dlp_errcode) 19100011 - If the system ability      works abnormally.</li>      <li> [ERR_OH_APPLICATION_NOT_AUTHORIZED](capi-dlp-permission-api-h.md#dlp_errcode) 19100018 - If the application is not      authorized.</li></ul> |


