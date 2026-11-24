# error_code.h

## Overview

Declare the error codes of file management module.

**Library**: NA

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 12

**Related module**: [FileIO](capi-core-file-kit-fileio.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [FileManagement_ErrCode](#filemanagement_errcode) | FileManagement_ErrCode | error codes of file management |

## Enum type description

### FileManagement_ErrCode

```c
enum FileManagement_ErrCode
```

**Description**

error codes of file management

<!--Device-enum FileManagement_ErrCode--><!--Device-enum FileManagement_ErrCode-End-->

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 12

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | The API is called successfully.<br>**Since**: 12<br><!--Device-ERR_OK = 0--><!--Device-ERR_OK = 0-End--> |
| ERR_PERMISSION_ERROR = 201 | The permission verification fails.<br>**Since**: 12<br><!--Device-ERR_PERMISSION_ERROR = 201--><!--Device-ERR_PERMISSION_ERROR = 201-End--> |
| ERR_INVALID_PARAMETER = 401 | Invalid parameter.<br>**Since**: 12<br><!--Device-ERR_INVALID_PARAMETER = 401--><!--Device-ERR_INVALID_PARAMETER = 401-End--> |
| ERR_DEVICE_NOT_SUPPORTED = 801 | The device does not support this API.<br>**Since**: 12<br><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801--><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801-End--> |
| ERR_EPERM = 13900001 | The operation is not allowed.<br>**Since**: 12<br><!--Device-ERR_EPERM = 13900001--><!--Device-ERR_EPERM = 13900001-End--> |
| ERR_ENOENT = 13900002 | The file or folder does not exist.<br>**Since**: 12<br><!--Device-ERR_ENOENT = 13900002--><!--Device-ERR_ENOENT = 13900002-End--> |
| ERR_ENOMEM = 13900011 | out of memory.<br>**Since**: 12<br><!--Device-ERR_ENOMEM = 13900011--><!--Device-ERR_ENOMEM = 13900011-End--> |
| ERR_UNKNOWN = 13900042 | Internal unknown error.<br>**Since**: 12<br><!--Device-ERR_UNKNOWN = 13900042--><!--Device-ERR_UNKNOWN = 13900042-End--> |


