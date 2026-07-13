# avtranscoder_base.h

## 概述

定义了媒体AVTranscoder的结构体和枚举。

**库：** libavtranscoder.so

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**起始版本：** 20

**相关模块：** [AVTranscoder](capi-avtranscoder.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) | OH_AVTranscoder | 初始化AVTranscoder。 |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) | OH_AVTranscoder_Config | 初始化AVTranscoder_Config。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AVTranscoder_State](#oh_avtranscoder_state) | OH_AVTranscoder_State | 转码状态。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVTranscoder_OnStateChange)(OH_AVTranscoder *transcoder, OH_AVTranscoder_State state, void *userData)](#oh_avtranscoder_onstatechange) | OH_AVTranscoder_OnStateChange | 转码过程的状态回调函数。 |
| [typedef void (\*OH_AVTranscoder_OnError)(OH_AVTranscoder *transcoder, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avtranscoder_onerror) | OH_AVTranscoder_OnError | 转码过程中错误事件的回调函数。 |
| [typedef void (\*OH_AVTranscoder_OnProgressUpdate)(OH_AVTranscoder *transcoder, int32_t progress, void *userData)](#oh_avtranscoder_onprogressupdate) | OH_AVTranscoder_OnProgressUpdate | 回调转码进度更新时调用。 |

## 枚举类型说明

### OH_AVTranscoder_State

```c
enum OH_AVTranscoder_State
```

**描述**

转码状态。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AVTRANSCODER_PREPARED = 1 | 准备 |
| AVTRANSCODER_STARTED = 2 | 开始 |
| AVTRANSCODER_PAUSED = 3 | 暂停 |
| AVTRANSCODER_CANCELLED = 4 | 取消 |
| AVTRANSCODER_COMPLETED = 5 | 完成 |


## 函数说明

### OH_AVTranscoder_OnStateChange()

```c
typedef void (*OH_AVTranscoder_OnStateChange)(OH_AVTranscoder *transcoder, OH_AVTranscoder_State state, void *userData)
```

**描述**

转码过程的状态回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVTranscoder \*transcoder | The pointer to an OH_AVTranscoder instance. |
| [OH_AVTranscoder_State](capi-avtranscoder-base-h.md#oh_avtranscoder_state) state | Indicates the transcoder state. For details, see [OH_AVTranscoder_State](capi-avtranscoder-base-h.md#oh_avtranscoder_state). |
| void \*userData | Pointer to user specific data. |

### OH_AVTranscoder_OnError()

```c
typedef void (*OH_AVTranscoder_OnError)(OH_AVTranscoder *transcoder, int32_t errorCode, const char *errorMsg, void *userData)
```

**描述**

转码过程中错误事件的回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVTranscoder \*transcoder | Pointer to an OH_AVTranscoder instance. |
| int32_t errorCode | Error code.{@link AV_ERR_NO_MEMORY} if memory is insufficient.{@link AV_ERR_IO} if IO access failed.{@link AV_ERR_INVALID_STATE} if current state does not support this operation.{@link AV_ERR_UNSUPPORT} if unsupported function.{@link AV_ERR_INVALID_VAL} if the parameter check failed.{@link AV_ERR_OPERATE_NOT_PERMIT} if operation not allowed. |
| const char \*errorMsg | Error message. |
| void \*userData | Pointer to user specific data. |

### OH_AVTranscoder_OnProgressUpdate()

```c
typedef void (*OH_AVTranscoder_OnProgressUpdate)(OH_AVTranscoder *transcoder, int32_t progress, void *userData)
```

**描述**

回调转码进度更新时调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVTranscoder \*transcoder | Pointer to an OH_AVTranscoder instance. |
| int32_t progress | Transcoding progress, in percentage. |
| void \*userData | Pointer to user specific data. |


