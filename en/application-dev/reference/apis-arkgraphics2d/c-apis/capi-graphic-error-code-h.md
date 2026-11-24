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

<!--Device-enum OHNativeErrorCode--><!--Device-enum OHNativeErrorCode-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 12

| Enum item | Description |
| -- | -- |
| NATIVE_ERROR_OK = 0 | &nbsp;success<br><!--Device-NATIVE_ERROR_OK = 0--><!--Device-NATIVE_ERROR_OK = 0-End--> |
| NATIVE_ERROR_MEM_OPERATION_ERROR = 30001000 | &nbsp;memory operation error<br>**Since**: 15<br><!--Device-NATIVE_ERROR_MEM_OPERATION_ERROR = 30001000--><!--Device-NATIVE_ERROR_MEM_OPERATION_ERROR = 30001000-End--> |
| NATIVE_ERROR_INVALID_ARGUMENTS = 40001000 | &nbsp;invalid input parameter<br><!--Device-NATIVE_ERROR_INVALID_ARGUMENTS = 40001000--><!--Device-NATIVE_ERROR_INVALID_ARGUMENTS = 40001000-End--> |
| NATIVE_ERROR_NO_PERMISSION = 40301000 | &nbsp;unauthorized operation<br><!--Device-NATIVE_ERROR_NO_PERMISSION = 40301000--><!--Device-NATIVE_ERROR_NO_PERMISSION = 40301000-End--> |
| NATIVE_ERROR_NO_BUFFER = 40601000 | &nbsp;no idle buffer is available<br><!--Device-NATIVE_ERROR_NO_BUFFER = 40601000--><!--Device-NATIVE_ERROR_NO_BUFFER = 40601000-End--> |
| NATIVE_ERROR_INVALID_OPERATION = 41201000 | &nbsp;invalid operation<br>**Since**: 26.0.0<br><!--Device-NATIVE_ERROR_INVALID_OPERATION = 41201000--><!--Device-NATIVE_ERROR_INVALID_OPERATION = 41201000-End--> |
| NATIVE_ERROR_NO_CONSUMER = 41202000 | &nbsp;the consumer side doesn't exist<br><!--Device-NATIVE_ERROR_NO_CONSUMER = 41202000--><!--Device-NATIVE_ERROR_NO_CONSUMER = 41202000-End--> |
| NATIVE_ERROR_NOT_INIT = 41203000 | &nbsp;uninitialized<br><!--Device-NATIVE_ERROR_NOT_INIT = 41203000--><!--Device-NATIVE_ERROR_NOT_INIT = 41203000-End--> |
| NATIVE_ERROR_CONSUMER_CONNECTED = 41206000 | &nbsp;the consumer is connected<br><!--Device-NATIVE_ERROR_CONSUMER_CONNECTED = 41206000--><!--Device-NATIVE_ERROR_CONSUMER_CONNECTED = 41206000-End--> |
| NATIVE_ERROR_BUFFER_STATE_INVALID = 41207000 | &nbsp;the buffer status did not meet expectations<br><!--Device-NATIVE_ERROR_BUFFER_STATE_INVALID = 41207000--><!--Device-NATIVE_ERROR_BUFFER_STATE_INVALID = 41207000-End--> |
| NATIVE_ERROR_BUFFER_IN_CACHE = 41208000 | &nbsp;buffer is already in the cache queue<br><!--Device-NATIVE_ERROR_BUFFER_IN_CACHE = 41208000--><!--Device-NATIVE_ERROR_BUFFER_IN_CACHE = 41208000-End--> |
| NATIVE_ERROR_BUFFER_QUEUE_FULL = 41209000 | &nbsp;the buffer queue is full<br><!--Device-NATIVE_ERROR_BUFFER_QUEUE_FULL = 41209000--><!--Device-NATIVE_ERROR_BUFFER_QUEUE_FULL = 41209000-End--> |
| NATIVE_ERROR_BUFFER_NOT_IN_CACHE = 41210000 | &nbsp;buffer is not in the cache queue<br><!--Device-NATIVE_ERROR_BUFFER_NOT_IN_CACHE = 41210000--><!--Device-NATIVE_ERROR_BUFFER_NOT_IN_CACHE = 41210000-End--> |
| NATIVE_ERROR_CONSUMER_DISCONNECTED = 41211000 | &nbsp;the consumer is disconnected<br><!--Device-NATIVE_ERROR_CONSUMER_DISCONNECTED = 41211000--><!--Device-NATIVE_ERROR_CONSUMER_DISCONNECTED = 41211000-End--> |
| NATIVE_ERROR_CONSUMER_NO_LISTENER_REGISTERED = 41212000 | &nbsp;no listener registered on consumer<br><!--Device-NATIVE_ERROR_CONSUMER_NO_LISTENER_REGISTERED = 41212000--><!--Device-NATIVE_ERROR_CONSUMER_NO_LISTENER_REGISTERED = 41212000-End--> |
| NATIVE_ERROR_UNSUPPORTED = 50102000 | &nbsp;the current device or platform does not support it<br><!--Device-NATIVE_ERROR_UNSUPPORTED = 50102000--><!--Device-NATIVE_ERROR_UNSUPPORTED = 50102000-End--> |
| NATIVE_ERROR_UNKNOWN = 50002000 | &nbsp;unknown error, please check log<br><!--Device-NATIVE_ERROR_UNKNOWN = 50002000--><!--Device-NATIVE_ERROR_UNKNOWN = 50002000-End--> |
| NATIVE_ERROR_HDI_ERROR = 50007000 | &nbsp;hdi interface error<br><!--Device-NATIVE_ERROR_HDI_ERROR = 50007000--><!--Device-NATIVE_ERROR_HDI_ERROR = 50007000-End--> |
| NATIVE_ERROR_BINDER_ERROR = 50401000 | &nbsp;ipc send failed<br><!--Device-NATIVE_ERROR_BINDER_ERROR = 50401000--><!--Device-NATIVE_ERROR_BINDER_ERROR = 50401000-End--> |
| NATIVE_ERROR_EGL_STATE_UNKNOWN = 60001000 | &nbsp;the egl environment is abnormal<br><!--Device-NATIVE_ERROR_EGL_STATE_UNKNOWN = 60001000--><!--Device-NATIVE_ERROR_EGL_STATE_UNKNOWN = 60001000-End--> |
| NATIVE_ERROR_EGL_API_FAILED = 60002000 | &nbsp;egl interface invocation failed<br><!--Device-NATIVE_ERROR_EGL_API_FAILED = 60002000--><!--Device-NATIVE_ERROR_EGL_API_FAILED = 60002000-End--> |


