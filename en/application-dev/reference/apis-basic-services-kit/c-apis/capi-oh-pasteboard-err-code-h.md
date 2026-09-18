# oh_pasteboard_err_code.h

## Overview

Declaration error code information.

**Include**: <database/pasteboard/oh_pasteboard_err_code.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-pasteboard.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | Enumerates the error codes. |

## Enum type description

### PASTEBOARD_ErrCode

```c
enum PASTEBOARD_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 13

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | The operation is successful. |
| ERR_PERMISSION_ERROR = 201 | Permission verification failed. |
| ERR_INVALID_PARAMETER = 401 | Invalid parameter is detected. |
| ERR_DEVICE_NOT_SUPPORTED = 801 | The capability is not supported. |
| ERR_INNER_ERROR = 12900000 | Inner error. |
| ERR_BUSY = 12900003 | Another copy is in progress. |
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 |  Copy file failed.<br>**Since**: 15 |
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 |  Failed to start progress.<br>**Since**: 15 |
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 |  Progress exits abnormally.<br>**Since**: 15 |
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 |  Get Data failed.<br>**Since**: 15 |


