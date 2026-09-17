# error_code.h

## Overview

Declare the error codes of file management module.

**Library**: NA

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 12

**Related module**: [FileIO](capi-fileio.md)

## Summary

### Enum

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

**Since**: 12

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | The API is called successfully.<br>**Since**: 12 |
| ERR_PERMISSION_ERROR = 201 | The permission verification fails.<br>**Since**: 12 |
| ERR_INVALID_PARAMETER = 401 | Invalid parameter.<br>**Since**: 12 |
| ERR_DEVICE_NOT_SUPPORTED = 801 | The device does not support this API.<br>**Since**: 12 |
| ERR_EPERM = 13900001 | The operation is not allowed.<br>**Since**: 12 |
| ERR_ENOENT = 13900002 | The file or folder does not exist.<br>**Since**: 12 |
| ERR_ENOMEM = 13900011 | out of memory.<br>**Since**: 12 |
| ERR_UNKNOWN = 13900042 | Internal unknown error.<br>**Since**: 12 |


