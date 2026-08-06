# oh_pasteboard_err_code.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->

## Overview

Declares the error code information of the pasteboard. Pasteboard error codes are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes.

**File to include**: <database/pasteboard/oh_pasteboard_err_code.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-pasteboard.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | Enumerates the error codes.|

## Enum Description

### PASTEBOARD_ErrCode

```c
enum PASTEBOARD_ErrCode
```

**Description**

Enumerates pasteboard error codes, which are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes.

**Since**: 13

| Enum Item| Description| Remarks|
| -- | -- | -- |
| ERR_OK = 0 | Operation successful.| - |
| ERR_PERMISSION_ERROR = 201 | Permission verification failed.| Permission verification failed. Check whether the application has requested the required permission or whether the permission configuration is correct.|
| ERR_INVALID_PARAMETER = 401 | Invalid parameter.| The parameter is invalid. Check the parameter type, value range, and whether the parameter is empty.|
| ERR_DEVICE_NOT_SUPPORTED = 801 | Device capability not supported.| The current device does not support this function. Check whether the device has the required capability.|
| ERR_INNER_ERROR = 12900000 | Internal error.| System internal error. Try again later or contact technical support.|
| ERR_BUSY = 12900003 | System busy.| The system is busy. Please try again later.|
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 | Failed to copy files.<br> **Since**: 15| Failed to copy the file. Check whether the file exists, whether the storage space is sufficient, and whether you have the access permission.|
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 | Failed to display the progress.<br> **Since**: 15| Failed to display the progress. Check the system status or try again later.|
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 | Abnormal progress.<br> **Since**: 15| The progress is abnormal. Check the system status or try again later.|
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 | Failed to obtain the pasteboard data.<br> **Since**: 15| Failed to obtain pasteboard data. Check whether the pasteboard contains data or whether the permission is correct.|
