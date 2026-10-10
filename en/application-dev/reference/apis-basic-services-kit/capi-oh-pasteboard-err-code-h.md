# oh_pasteboard_err_code.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=3f7e8cc3ffe8312d3c00ac721422357ddd729ccb translatedAt=2026-10-09T11:35:43.676Z pushedAt=2026-10-10T03:41:22.001Z -->

## Overview

Declares the error code information of the pasteboard. Pasteboard error codes are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes.

**File to include**: <database/pasteboard/oh_pasteboard_err_code.h>

**Library**: libpasteboard.so

**System capability**: SystemCapability.MiscServices.Pasteboard

**Since**: 13

**Related module**: [Pasteboard](capi-pasteboard.md)

## Summary

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | Enumerates the error codes. |

## Enum Description

### PASTEBOARD_ErrCode

```c
enum PASTEBOARD_ErrCode
```

**Description**

Enumerates pasteboard error codes, which are used to identify the pasteboard operation results. You can determine whether an operation is successful and find the cause of a failure based on the error codes.

**Since**: 13

| Value | Description |
| -- | -- |
| ERR_OK = 0 | Success. |
| ERR_PERMISSION_ERROR = 201 | Permission verification fails. |
| ERR_INVALID_PARAMETER = 401 | Invalid parameters are specified. |
| ERR_DEVICE_NOT_SUPPORTED = 801 | The device capability is not supported. |
| ERR_INNER_ERROR = 12900000 | Internal error. |
| ERR_BUSY = 12900003 | The system is busy. |
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 | Failed to copy the file.</br> **Since:** 15 |
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 | Failed to start the progress display.</br> **Since:** 15 |
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 | The progress display is abnormal.</br> **Since:** 15 |
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 | Failed to obtain clipboard data.</br> **Since:** 15 |


