# oh_environment.h

## Overview

Provide environment APIS.

**Library**: libohenvironment.so

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Since**: 12

**Related module**: [Environment](capi-environment.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)](#oh_environment_getuserdownloaddir) | Obtains the sandbox path of the Download root directory. |
| [FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)](#oh_environment_getuserdesktopdir) | Obtains the sandbox path of the Desktop root directory. |
| [FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)](#oh_environment_getuserdocumentdir) | Obtains the sandbox path of the Document root directory. |

## Function description

### OH_Environment_GetUserDownloadDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)
```

**Description**

Obtains the sandbox path of the Download root directory.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **result | Double pointer to the path of the Download root directory. You also need to include malloc.h and use free() to release the memory allocated. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Return the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDesktopDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)
```

**Description**

Obtains the sandbox path of the Desktop root directory.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **result | Double pointer to the path of the Desktop root directory. You also need to include malloc.h and use free() to release the memory allocated. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Return the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDocumentDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)
```

**Description**

Obtains the sandbox path of the Document root directory.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char **result | Double pointer to the path of the Document root directory. You also need to include malloc.h and use free() to release the memory allocated. |

**Returns**:

| Type | Description |
| -- | -- |
| FileManagement_ErrCode | Return the status code of the execution.          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>        {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>        {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |


