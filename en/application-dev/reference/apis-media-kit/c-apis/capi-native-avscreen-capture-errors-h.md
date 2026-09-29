# native_avscreen_capture_errors.h

## Overview

The file declares the error codes generated during screen capture.

**Library**: libnative_avscreen_capture.so

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](#oh_avscreen_capture_errcode) | OH_AVSCREEN_CAPTURE_ErrCode | Enumerates the error codes generated during screen capture. |

### Macro

| Name | Description |
| -- | -- |
| NATIVE_AVSCREEN_CAPTURE_ERRORS_H | The file declares the error codes generated during screen capture.<br>**Since**: 10<br>**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture |

## Enum type description

### OH_AVSCREEN_CAPTURE_ErrCode

```c
enum OH_AVSCREEN_CAPTURE_ErrCode
```

**Description**

Enumerates the error codes generated during screen capture.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AV_SCREEN_CAPTURE_ERR_BASE = 0 | Basic value returned when an API call error occurs. |
| AV_SCREEN_CAPTURE_ERR_OK = AV_SCREEN_CAPTURE_ERR_BASE | Operation successful. |
| AV_SCREEN_CAPTURE_ERR_NO_MEMORY = AV_SCREEN_CAPTURE_ERR_BASE + 1 | Insufficient memory. |
| AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT = AV_SCREEN_CAPTURE_ERR_BASE + 2 | Operation not allowed. |
| AV_SCREEN_CAPTURE_ERR_INVALID_VAL = AV_SCREEN_CAPTURE_ERR_BASE + 3 | Invalid parameter. |
| AV_SCREEN_CAPTURE_ERR_IO = AV_SCREEN_CAPTURE_ERR_BASE + 4 | Abnormal input and output streams. |
| AV_SCREEN_CAPTURE_ERR_TIMEOUT = AV_SCREEN_CAPTURE_ERR_BASE + 5 | Network timeout. |
| AV_SCREEN_CAPTURE_ERR_UNKNOWN = AV_SCREEN_CAPTURE_ERR_BASE + 6 | Unknown error. |
| AV_SCREEN_CAPTURE_ERR_SERVICE_DIED = AV_SCREEN_CAPTURE_ERR_BASE + 7 | Media service terminated. |
| AV_SCREEN_CAPTURE_ERR_INVALID_STATE = AV_SCREEN_CAPTURE_ERR_BASE + 8 | Unsupported operation in this state. |
| AV_SCREEN_CAPTURE_ERR_UNSUPPORT = AV_SCREEN_CAPTURE_ERR_BASE + 9 | Unsupported interface. |
| AV_SCREEN_CAPTURE_ERR_EXTEND_START = AV_SCREEN_CAPTURE_ERR_BASE + 100 | Unexpected error. |


