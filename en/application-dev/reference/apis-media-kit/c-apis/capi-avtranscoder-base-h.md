# avtranscoder_base.h

## Overview

The file declares the struct and enums used by the AVTranscoder.

**Library**: libavtranscoder.so

**Since**: 20

**Related module**: [AVTranscoder](capi-avtranscoder.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) | OH_AVTranscoder | The struct initializes an AVTranscoder. |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) | OH_AVTranscoder_Config | The struct initializes an AVTranscoder_Config. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVTranscoder_State](#oh_avtranscoder_state) | OH_AVTranscoder_State | Enumerates the transcoding states. |

### Macro

| Name | Description |
| -- | -- |
| MULTIMEDIA_PLAYER_FRAMEWORK_AVTRANSCODER_BASE_H | The file declares the struct and enums used by the AVTranscoder.<br>**Since**: 20 |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AVTranscoder_OnStateChange)(OH_AVTranscoder *transcoder, OH_AVTranscoder_State state, void *userData)](#oh_avtranscoder_onstatechange) | OH_AVTranscoder_OnStateChange | Defines a callback invoked when the state of the transcoding process changes. |
| [typedef void (\*OH_AVTranscoder_OnError)(OH_AVTranscoder *transcoder, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avtranscoder_onerror) | OH_AVTranscoder_OnError | Defines a callback invoked when an error occurs during the transcoding process. |
| [typedef void (\*OH_AVTranscoder_OnProgressUpdate)(OH_AVTranscoder *transcoder, int32_t progress, void *userData)](#oh_avtranscoder_onprogressupdate) | OH_AVTranscoder_OnProgressUpdate | Defines a callback invoked when the progress of the transcoding process is updated. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AVTranscoder_OnStateChange)(OH_AVTranscoder *transcoder, OH_AVTranscoder_State state, void *userData) | Defines a callback invoked when the state of the transcoding process changes.<br>**Since**: 20 |
| void (*OH_AVTranscoder_OnError)(OH_AVTranscoder *transcoder, int32_t errorCode, const char *errorMsg, void *userData) | Defines a callback invoked when an error occurs during the transcoding process.<br>**Since**: 20 |
| void (*OH_AVTranscoder_OnProgressUpdate)(OH_AVTranscoder *transcoder, int32_t progress, void *userData) | Defines a callback invoked when the progress of the transcoding process is updated.<br>**Since**: 20 |

## Enum type description

### OH_AVTranscoder_State

```c
enum OH_AVTranscoder_State
```

**Description**

Enumerates the transcoding states.

**Since**: 20

| Enum item | Description |
| -- | -- |
| AVTRANSCODER_PREPARED = 1 | The transcoding process is prepared and ready to start. |
| AVTRANSCODER_STARTED = 2 | The transcoding process has started. |
| AVTRANSCODER_PAUSED = 3 | The transcoding process is paused. |
| AVTRANSCODER_CANCELLED = 4 | The transcoding process has been canceled. |
| AVTRANSCODER_COMPLETED = 5 | The transcoding process is completed. |


## Function description

### OH_AVTranscoder_OnStateChange()

```c
typedef void (*OH_AVTranscoder_OnStateChange)(OH_AVTranscoder *transcoder, OH_AVTranscoder_State state, void *userData)
```

**Description**

Defines a callback invoked when the state of the transcoding process changes.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) \*transcoder | The pointer to an OH_AVTranscoder instance. |
| [OH_AVTranscoder_State](capi-avtranscoder-base-h.md#oh_avtranscoder_state) state | Indicates the transcoder state. For details, see [OH_AVTranscoder_State](capi-avtranscoder-base-h.md#oh_avtranscoder_state). |
| void \*userData | Pointer to user specific data. |

### OH_AVTranscoder_OnError()

```c
typedef void (*OH_AVTranscoder_OnError)(OH_AVTranscoder *transcoder, int32_t errorCode, const char *errorMsg, void *userData)
```

**Description**

Defines a callback invoked when an error occurs during the transcoding process.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) \*transcoder | Pointer to an OH_AVTranscoder instance. |
| int32_t errorCode | Error code. {@link AV_ERR_NO_MEMORY}: memory is insufficient.<br>{@link AV_ERR_IO}: IO access failed.<br>{@link AV_ERR_INVALID_STATE}: current state does not support this operation.<br>{@link AV_ERR_UNSUPPORT}: unsupported function.<br>{@link AV_ERR_INVALID_VAL}: the parameter check failed.<br>{@link AV_ERR_OPERATE_NOT_PERMIT}: operation not allowed. |
| const char \*errorMsg | Error message. |
| void \*userData | Pointer to user specific data. |

### OH_AVTranscoder_OnProgressUpdate()

```c
typedef void (*OH_AVTranscoder_OnProgressUpdate)(OH_AVTranscoder *transcoder, int32_t progress, void *userData)
```

**Description**

Defines a callback invoked when the progress of the transcoding process is updated.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) \*transcoder | Pointer to an OH_AVTranscoder instance. |
| int32_t progress | Transcoding progress, in percentage. |
| void \*userData | Pointer to user specific data. |


