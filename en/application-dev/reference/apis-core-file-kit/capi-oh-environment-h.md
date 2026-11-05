# oh_environment.h

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=6c0893247bd78c129e32a38e52ccc47805b1914a translatedAt=2026-11-03T03:48:35.317Z pushedAt=2026-11-04T03:11:33.469Z nl=1 -->

## Overview

Defines the native APIs used to obtain the sandbox paths of the user files.

**Header file**: <filemanagement/environment/oh_environment.h>

**Library**: libohenvironment.so

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Device behavior differences**
- Since API version 26.0.0, this API can be called on PCs, 2-in-1 devices, and tablets only. If it is called on other device types, error code 801 is returned.
- Before API version 26.0.0, this API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**Since**: 12

**Related module**: [Environment](capi-environment.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)](#oh_environment_getuserdownloaddir) | Obtains the sandbox path of the current user's download directory, used to access files in the corresponding directory. |
| [FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)](#oh_environment_getuserdesktopdir) | Obtains the sandbox path of the current user's desktop directory, used to access files in the corresponding directory. |
| [FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)](#oh_environment_getuserdocumentdir) | Obtains the sandbox path of the current user's document directory, used to access files in the corresponding directory. |

## Function Description

### OH_Environment_GetUserDownloadDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)
```

**Description**

Get the sandbox path of the current user's download directory, used to access files in the corresponding directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Returns the sandbox path of the Download root directory. This string is allocated by the system. The caller needs to release it through free() after use to avoid memory leaks. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns the FileManagement module error code [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode).<br>ERR_INVALID_PARAMETER 401 - Invalid input parameter, pointer is null. <br>ERR_DEVICE_NOT_SUPPORTED 801 - Device not supported. <br>ERR_ENOMEM 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDesktopDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)
```

**Description**

Get the sandbox path of the current user's desktop directory, used to access files in the corresponding directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Returns the sandbox path of the Desktop root directory. This string is allocated by the system. The caller needs to release it via free() after use to avoid memory leaks. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns the FileManagement module error code [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode). <br>ERR_INVALID_PARAMETER 401 - Invalid input parameter, pointer is null. <br>ERR_DEVICE_NOT_SUPPORTED 801 - Device not supported. <br>ERR_ENOMEM 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDocumentDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)
```

**Description**

Get the sandbox path of the current user's documents directory, used to access files in the corresponding directory.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char **result | Returns the sandbox path of the Document root directory. This string is allocated by the system. The caller needs to release it via free() after use to avoid memory leaks. |

**Returns**

| Type| Description|
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | Returns the FileManagement module error code [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode). <br>ERR_INVALID_PARAMETER 401 - Invalid input parameter, pointer is null. <br>ERR_DEVICE_NOT_SUPPORTED 801 - Device not supported. <br>ERR_ENOMEM 13900011 - Failed to apply for memory. |


