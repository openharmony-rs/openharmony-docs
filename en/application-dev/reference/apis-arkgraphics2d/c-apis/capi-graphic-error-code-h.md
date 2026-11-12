# graphic_error_code.h

## Overview

Defines the error codes.

**Library**: libnative_window.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

**Related module**: [NativeWindow](capi-arkgraphics2d-nativewindow.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OHNativeErrorCode](#ohnativeerrorcode) | OHNativeErrorCode | native error code. |

## Enum type description

### OHNativeErrorCode

```c
enum OHNativeErrorCode
```

**Description**

native error code.

<!--Device-OHNativeErrorCode--><!--Device-OHNativeErrorCode-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

| Enum item | Description |
| -- | -- |
| NATIVE_ERROR_OK = 0 | &nbsp;success |
| NATIVE_ERROR_MEM_OPERATION_ERROR = 30001000 | &nbsp;memory operation error<br>**Since**: 15 |
| NATIVE_ERROR_INVALID_ARGUMENTS = 40001000 | &nbsp;invalid input parameter |
| NATIVE_ERROR_NO_PERMISSION = 40301000 | &nbsp;unauthorized operation |
| NATIVE_ERROR_NO_BUFFER = 40601000 | &nbsp;no idle buffer is available |
| NATIVE_ERROR_INVALID_OPERATION = 41201000 | &nbsp;invalid operation<br>**Since**: 26.0.0 |
| NATIVE_ERROR_NO_CONSUMER = 41202000 | &nbsp;the consumer side doesn't exist |
| NATIVE_ERROR_NOT_INIT = 41203000 | &nbsp;uninitialized |
| NATIVE_ERROR_CONSUMER_CONNECTED = 41206000 | &nbsp;the consumer is connected |
| NATIVE_ERROR_BUFFER_STATE_INVALID = 41207000 | &nbsp;the buffer status did not meet expectations |
| NATIVE_ERROR_BUFFER_IN_CACHE = 41208000 | &nbsp;buffer is already in the cache queue |
| NATIVE_ERROR_BUFFER_QUEUE_FULL = 41209000 | &nbsp;the buffer queue is full |
| NATIVE_ERROR_BUFFER_NOT_IN_CACHE = 41210000 | &nbsp;buffer is not in the cache queue |
| NATIVE_ERROR_CONSUMER_DISCONNECTED = 41211000 | &nbsp;the consumer is disconnected |
| NATIVE_ERROR_CONSUMER_NO_LISTENER_REGISTERED = 41212000 | &nbsp;no listener registered on consumer |
| NATIVE_ERROR_UNSUPPORTED = 50102000 | &nbsp;the current device or platform does not support it |
| NATIVE_ERROR_UNKNOWN = 50002000 | &nbsp;unknown error, please check log |
| NATIVE_ERROR_HDI_ERROR = 50007000 | &nbsp;hdi interface error |
| NATIVE_ERROR_BINDER_ERROR = 50401000 | &nbsp;ipc send failed |
| NATIVE_ERROR_EGL_STATE_UNKNOWN = 60001000 | &nbsp;the egl environment is abnormal |
| NATIVE_ERROR_EGL_API_FAILED = 60002000 | &nbsp;egl interface invocation failed |


