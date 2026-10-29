# native_avscreen_capture_errors.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

## Overview

Declares the error codes for screen capture API calls, helping you identify and handle various exceptions in screen capture. This is applicable to development scenarios involving screen capture troubleshooting and error handling.

**File to include**: <multimedia/player_framework/native_avscreen_capture_errors.h>

**Library**: libnative_avscreen_capture.so

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVSCREEN_CAPTURE_ErrCode](#oh_avscreen_capture_errcode) | OH_AVSCREEN_CAPTURE_ErrCode | Enumerates the error codes generated during screen capture.|

## Enum Description

### OH_AVSCREEN_CAPTURE_ErrCode

```c
enum OH_AVSCREEN_CAPTURE_ErrCode
```

**Description**

Enumerates the error codes generated during screen capture.

In scenarios such as screen capture apps, online meeting screen sharing, and remote assistance, you can determine the cause of an API call error based on the returned error code and handle the error accordingly.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

| Enum| Description|
| -- | -- |
| AV_SCREEN_CAPTURE_ERR_BASE = 0 | Basic value of an error code. The number of other error codes increases based on this value and is used to identify different error types.| 
| AV_SCREEN_CAPTURE_ERR_OK = AV_SCREEN_CAPTURE_ERR_BASE | Operation successful.| 
| AV_SCREEN_CAPTURE_ERR_NO_MEMORY = AV_SCREEN_CAPTURE_ERR_BASE + 1 | Insufficient memory.<br>Possible causes: The system memory is insufficient.<br>Solution: Check the recording parameters or system memory status.| 
| AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT = AV_SCREEN_CAPTURE_ERR_BASE + 2 | Operation not allowed.<br>Possible causes: The required permission has not been obtained for the current operation or the operation is invalid.<br>Solution: Check the operation permission and current status, and try again.| 
| AV_SCREEN_CAPTURE_ERR_INVALID_VAL = AV_SCREEN_CAPTURE_ERR_BASE + 3 | Invalid parameter.<br>Possible causes: The input parameters do not meet the API requirements or the parameter values are out of the allowed range.<br>Solution: Check the parameter type and value range, and try again.| 
| AV_SCREEN_CAPTURE_ERR_IO = AV_SCREEN_CAPTURE_ERR_BASE + 4 | Abnormal input and output streams.<br>Possible causes: The file fails to be read or written, or a data transmission error occurs.<br>Solution: Check the file path, permissions, and storage space, and try again.| 
| AV_SCREEN_CAPTURE_ERR_TIMEOUT = AV_SCREEN_CAPTURE_ERR_BASE + 5 | Network timeout.<br>Possible causes: The Internet connection is unstable, or the server response times out.<br>Solution: Check the Internet connection status and try again.| 
| AV_SCREEN_CAPTURE_ERR_UNKNOWN = AV_SCREEN_CAPTURE_ERR_BASE + 6 | Unknown error.<br>Possible causes: An unexpected exception occurs.<br>Solution: Check the log information.| 
| AV_SCREEN_CAPTURE_ERR_SERVICE_DIED = AV_SCREEN_CAPTURE_ERR_BASE + 7 | Media service terminated.<br>Possible causes: The media service process crashes or is terminated by the system.<br>Solution: Check the system resources or restart the service.| 
| AV_SCREEN_CAPTURE_ERR_INVALID_STATE = AV_SCREEN_CAPTURE_ERR_BASE + 8 | Unsupported operation in this state.<br>Possible causes: The instance is in an error state when the interface is called.<br>Solution: Check the current state and call the interface according to the correct process.| 
| AV_SCREEN_CAPTURE_ERR_UNSUPPORT = AV_SCREEN_CAPTURE_ERR_BASE + 9 | Unsupported interface.<br>Possible causes: The current version does not support this interface or function.<br>Solution: Check the API version or device compatibility.| 
| AV_SCREEN_CAPTURE_ERR_EXTEND_START = AV_SCREEN_CAPTURE_ERR_BASE + 100 | Unexpected error.<br>Possible causes: An unexpected exception occurs.<br>Solution: Check the detailed error information.| 
