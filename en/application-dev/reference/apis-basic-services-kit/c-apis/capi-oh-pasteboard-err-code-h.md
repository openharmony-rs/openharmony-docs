# oh_pasteboard_err_code.h

## Overview

Declaration error code information.

**File to Include**: <database/pasteboard/oh_pasteboard_err_code.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-basic-services-kit-pasteboard.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | Enumerates pasteboard error codes, which are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes. |

## Enum type description

### PASTEBOARD_ErrCode

```c
enum PASTEBOARD_ErrCode
```

**Description**

Enumerates pasteboard error codes, which are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes.

<!--Device-enum PASTEBOARD_ErrCode--><!--Device-enum PASTEBOARD_ErrCode-End-->

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

| Enum item | Description |
| -- | -- |
| ERR_OK = 0 | &nbsp;Operation successful.<br><!--Device-ERR_OK = 0--><!--Device-ERR_OK = 0-End--> |
| ERR_PERMISSION_ERROR = 201 | &nbsp;Permission verification failed.<br><!--Device-ERR_PERMISSION_ERROR = 201--><!--Device-ERR_PERMISSION_ERROR = 201-End--> |
| ERR_INVALID_PARAMETER = 401 | &nbsp;Invalid parameter.<br><!--Device-ERR_INVALID_PARAMETER = 401--><!--Device-ERR_INVALID_PARAMETER = 401-End--> |
| ERR_DEVICE_NOT_SUPPORTED = 801 | &nbsp;Device capability not supported.<br><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801--><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801-End--> |
| ERR_INNER_ERROR = 12900000 | &nbsp;Internal error.<br><!--Device-ERR_INNER_ERROR = 12900000--><!--Device-ERR_INNER_ERROR = 12900000-End--> |
| ERR_BUSY = 12900003 | &nbsp;System busy.<br><!--Device-ERR_BUSY = 12900003--><!--Device-ERR_BUSY = 12900003-End--> |
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 | &nbsp;Failed to copy files.<br>**Since**: 15<br><!--Device-ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007--><!--Device-ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007-End--> |
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 | &nbsp;Failed to display the progress.<br>**Since**: 15<br><!--Device-ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008--><!--Device-ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008-End--> |
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 | &nbsp;Abnormal progress.<br>**Since**: 15<br><!--Device-ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009--><!--Device-ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009-End--> |
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 | &nbsp;Failed to obtain the pasteboard data.<br>**Since**: 15<br><!--Device-ERR_PASTEBOARD_GET_DATA_FAILED = 12900010--><!--Device-ERR_PASTEBOARD_GET_DATA_FAILED = 12900010-End--> |


