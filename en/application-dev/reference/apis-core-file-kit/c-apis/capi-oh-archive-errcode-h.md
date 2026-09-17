# oh_archive_errcode.h

## Overview

Declares the error codes of Archive module.

**Library**: liboharchive.so

**System capability**: SystemCapability.FileManagement.File.FileIO

**Since**: 26.0.0

**Related module**: [Archive](capi-archive.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Archive_ErrCode](#oh_archive_errcode) | OH_Archive_ErrCode | Error codes for the Archive. |

### Macro

| Name | Description |
| -- | -- |
| FILE_MANAGEMENT_ARCHIVE_OH_ARCHIVE_ERRCODE_H | Declares the error codes of Archive module.<br>**Since**: 26.0.0<br>**System capability**: SystemCapability.FileManagement.File.FileIO |

## Enum type description

### OH_Archive_ErrCode

```c
enum OH_Archive_ErrCode
```

**Description**

Error codes for the Archive.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ARCHIVE_OK = 0 | Operation completed successfully.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_PARAM_ERROR = 401 | Invalid input parameters.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_UNKNOWN_ERROR = 13900100 | An unknown error occurred.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_CANCEL_ERROR = 13900101 | Operation cancelled by user.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_UNSUPPORTED_ERROR = 13900102 | Format not supported.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_MEM_ERROR = 13900103 | Memory allocation failed.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_OPEN_ERROR = 13900104 | Failed to open archive file.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_WRITE_ERROR = 13900105 | Write operation failed.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_READ_ERROR = 13900106 | Read operation failed.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_STREAM_OUTPUT_ERROR = 13900107 | Stream output error.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_INSUFFICIENT_OUTBUF_ERROR = 13900108 | Insufficient output buffer error.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_NO_SPACE_ERROR = 13900200 | Insufficient disk space.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_PATH_NOT_EXIST_ERROR = 13900201 | Path does not exist.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_PATH_EXISTS_ERROR = 13900202 | Path already exists.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_PATH_ACCESS_ERROR = 13900203 | Path access error.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_NAME_TOO_LONG_ERROR = 13900204 | File name too long.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_FULL_PATH_TOO_LONG_ERROR = 13900205 | Full path too long.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_DATA_ERROR = 13900300 | Data integrity error.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_CRC_ERROR = 13900301 | CRC check error.<br>**Since**: 26.0.0 |
| OH_ARCHIVE_DEFLATE_ERROR = 13900302 | Deflate method error.<br>**Since**: 26.0.0 |


