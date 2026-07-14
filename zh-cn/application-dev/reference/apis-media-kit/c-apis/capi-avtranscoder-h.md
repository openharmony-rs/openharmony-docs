# avtranscoder.h

## 概述

定义AVTranscoder接口。使用AVTranscoder提供的Native API将源视频文件转码为新视频文件。

**库：** libavtranscoder.so

**起始版本：** 20

**相关模块：** [AVTranscoder](capi-avtranscoder.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config *OH_AVTranscoderConfig_Create()](#oh_avtranscoderconfig_create) | 创建转码配置参数实例。 |
| [OH_AVErrCode OH_AVTranscoderConfig_Release(OH_AVTranscoder_Config* config)](#oh_avtranscoderconfig_release) | 释放转码配置参数资源。调用成功后，config实例会被释放并置为nullptr。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetSrcFD(OH_AVTranscoder_Config *config, int32_t srcFd, int64_t srcOffset, int64_t length)](#oh_avtranscoderconfig_setsrcfd) | 设置转码源视频的文件描述符。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstFD(OH_AVTranscoder_Config *config, int32_t dstFd)](#oh_avtranscoderconfig_setdstfd) | 设置转码输出视频的文件描述符。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoType(OH_AVTranscoder_Config *config, const char *mimeType)](#oh_avtranscoderconfig_setdstvideotype) | 设置用于转码的输出视频的编码格式。当前仅支持AVC和HEVC。若源视频编码格式为HEVC，则默认设置为HEVC，否则默认设置为AVC。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioType(OH_AVTranscoder_Config *config, const char *mimeType)](#oh_avtranscoderconfig_setdstaudiotype) | 设置用于转码的输出音频的编码格式。当前仅支持AAC。若开发者不设置，则默认设置为AAC。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstFileType(OH_AVTranscoder_Config *config, OH_AVOutputFormat mimeType)](#oh_avtranscoderconfig_setdstfiletype) | 设置用于转码的输出视频文件的封装格式。当前封装格式仅支持MP4。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)](#oh_avtranscoderconfig_setdstaudiobitrate) | 设置用于转码的输出音频的码率。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)](#oh_avtranscoderconfig_setdstvideobitrate) | 设置用于转码的输出视频的码率。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoResolution(OH_AVTranscoder_Config *config, int32_t width, int32_t height)](#oh_avtranscoderconfig_setdstvideoresolution) | 设置用于转码的输出视频的分辨率，单位为像素（px），其中width为输出视频帧的宽，height为输出视频帧的高。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。 |
| [OH_AVTranscoder *OH_AVTranscoder_Create(void)](#oh_avtranscoder_create) | 创建转码实例。 |
| [OH_AVErrCode OH_AVTranscoder_Prepare(OH_AVTranscoder *transcoder, OH_AVTranscoder_Config *config)](#oh_avtranscoder_prepare) | 进行视频转码的参数设置，准备转码。此函数必须在[OH_AVTranscoder_Start](capi-avtranscoder-h.md#oh_avtranscoder_start)之前调用，调用成功之后进入AVTRANSCODER_PREPARED状态。 |
| [OH_AVErrCode OH_AVTranscoder_Start(OH_AVTranscoder *transcoder)](#oh_avtranscoder_start) | 开始转码。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)成功调用之后调用，调用成功之后进入AVTRANSCODER_STARTED状态。 |
| [OH_AVErrCode OH_AVTranscoder_Pause(OH_AVTranscoder *transcoder)](#oh_avtranscoder_pause) | 暂停转码。此函数必须在转码实例处于AVTRANSCODER_STARTED状态时调用，调用成功之后进入AVTRANSCODER_PAUSED状态。 |
| [OH_AVErrCode OH_AVTranscoder_Resume(OH_AVTranscoder *transcoder)](#oh_avtranscoder_resume) | 恢复转码。此函数必须在转码实例处于AVTRANSCODER_PAUSED状态时调用，调用成功之后重新进入AVTRANSCODER_STARTED状态。 |
| [OH_AVErrCode OH_AVTranscoder_Cancel(OH_AVTranscoder *transcoder)](#oh_avtranscoder_cancel) | 取消转码。此函数须在转码实例处于AVTRANSCODER_STARTED和AVTRANSCODER_PAUSED状态时调用，调用成功之后进入AVTRANSCODER_CANCELLED状态。 |
| [OH_AVErrCode OH_AVTranscoder_Release(OH_AVTranscoder *transcoder)](#oh_avtranscoder_release) | 释放转码实例资源。 |
| [OH_AVErrCode OH_AVTranscoder_SetStateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnStateChange callback, void *userData)](#oh_avtranscoder_setstatecallback) | 注册触发转码状态修改事件的回调方法。当触发状态修改事件时，通过注册的回调方法通知开发者。开发者只能注册一个状态修改事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码状态修改，须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册转码状态回调。 |
| [OH_AVErrCode OH_AVTranscoder_SetErrorCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnError callback, void *userData)](#oh_avtranscoder_seterrorcallback) | 注册触发转码错误事件的回调方法。当触发错误事件时，通过注册的回调方法通知开发者。如果AVTranscoder上报error事件，开发者需要通过[OH_AVTranscoder_Release](capi-avtranscoder-h.md#oh_avtranscoder_release)操作退出转码操作。开发者只能注册一个错误事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码错误事件，须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册转码错误事件。 |
| [OH_AVErrCode OH_AVTranscoder_SetProgressUpdateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnProgressUpdate callback, void *userData)](#oh_avtranscoder_setprogressupdatecallback) | 注册触发转码进度更新事件的回调方法。当触发转码进度更新事件时，通过注册的回调方法通知开发者。开发者只能注册一个错误事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码处理进度，则须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册该事件。 |
| [OH_AVErrCode OH_AVTranscoderConfig_EnableBFrame(OH_AVTranscoder_Config *config, bool enabled)](#oh_avtranscoderconfig_enablebframe) | 转码设置输出视频B帧编码。B帧视频编码相关的约束和限制可以参考文档{@link B帧视频编码约束和限制}。如果当前不符合B帧视频编码的约束和限制，将忽略B帧，按不使能B帧进行编码。 |

## 函数说明

### OH_AVTranscoderConfig_Create()

```c
OH_AVTranscoder_Config *OH_AVTranscoderConfig_Create()
```

**描述**

创建转码配置参数实例。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVTranscoder_Config *](capi-avtranscoder-oh-avtranscoder-config.md) | 如果创建成功返回指向OH_AVTranscoder_Config实例的指针，否则返回空指针。 |

### OH_AVTranscoderConfig_Release()

```c
OH_AVErrCode OH_AVTranscoderConfig_Release(OH_AVTranscoder_Config* config)
```

**描述**

释放转码配置参数资源。调用成功后，config实例会被释放并置为nullptr。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md)* config | Pointer to an OH_AVTranscoder_Config instance. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：释放成功。<br> AV_ERR_INVALID_VAL：config是空指针。 |

### OH_AVTranscoderConfig_SetSrcFD()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetSrcFD(OH_AVTranscoder_Config *config, int32_t srcFd, int64_t srcOffset, int64_t length)
```

**描述**

设置转码源视频的文件描述符。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance. |
| int32_t srcFd | Source file descriptor. |
| int64_t srcOffset | The offset into the file where the data to be read, in bytes. |
| int64_t length | The length in bytes of the data to be read |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入config为空指针，或者源视频文件相关参数错误。 |

### OH_AVTranscoderConfig_SetDstFD()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstFD(OH_AVTranscoder_Config *config, int32_t dstFd)
```

**描述**

设置转码输出视频的文件描述符。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t dstFd | Destination file descriptor |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入config为空指针，或者输出视频文件描述符是无效的。 |

### OH_AVTranscoderConfig_SetDstVideoType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoType(OH_AVTranscoder_Config *config, const char *mimeType)
```

**描述**

设置用于转码的输出视频的编码格式。当前仅支持AVC和HEVC。若源视频编码格式为HEVC，则默认设置为HEVC，否则默认设置为AVC。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| const char *mimeType | Destination video mime type. See native_avcodec_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者mimeType是不被允许的。 |

### OH_AVTranscoderConfig_SetDstAudioType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioType(OH_AVTranscoder_Config *config, const char *mimeType)
```

**描述**

设置用于转码的输出音频的编码格式。当前仅支持AAC。若开发者不设置，则默认设置为AAC。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| const char *mimeType | Destination audio mime type. See native_avcodec_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者mimeType是不被允许的。 |

### OH_AVTranscoderConfig_SetDstFileType()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstFileType(OH_AVTranscoder_Config *config, OH_AVOutputFormat mimeType)
```

**描述**

设置用于转码的输出视频文件的封装格式。当前封装格式仅支持MP4。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| [OH_AVOutputFormat](../AVCodecKit/capi-native-avcodec-base-h.md#oh_avoutputformat) mimeType | Destination file type. See native_avcodec_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者mimeType是无效的。 |

### OH_AVTranscoderConfig_SetDstAudioBitrate()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstAudioBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)
```

**描述**

设置用于转码的输出音频的码率。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t bitrate | Destination audio bitrate, in bit/s. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者bitrate值是无效的。 |

### OH_AVTranscoderConfig_SetDstVideoBitrate()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoBitrate(OH_AVTranscoder_Config *config, int32_t bitrate)
```

**描述**

设置用于转码的输出视频的码率。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t bitrate | Destination video bitrate, in bit/s. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者bitrate值是无效的。 |

### OH_AVTranscoderConfig_SetDstVideoResolution()

```c
OH_AVErrCode OH_AVTranscoderConfig_SetDstVideoResolution(OH_AVTranscoder_Config *config, int32_t width, int32_t height)
```

**描述**

设置用于转码的输出视频的分辨率，单位为像素（px），其中width为输出视频帧的宽，height为输出视频帧的高。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| int32_t width | Destination for video width, in px. |
| int32_t height | Destination for video height, in px. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针，或者width、height值是无效的。 |

### OH_AVTranscoder_Create()

```c
OH_AVTranscoder *OH_AVTranscoder_Create(void)
```

**描述**

创建转码实例。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVTranscoder *](capi-avtranscoder-oh-avtranscoder.md) | 如果创建成功返回指向OH_AVTranscoder实例的指针，否则返回空指针。 |

### OH_AVTranscoder_Prepare()

```c
OH_AVErrCode OH_AVTranscoder_Prepare(OH_AVTranscoder *transcoder, OH_AVTranscoder_Config *config)
```

**描述**

进行视频转码的参数设置，准备转码。此函数必须在[OH_AVTranscoder_Start](capi-avtranscoder-h.md#oh_avtranscoder_start)之前调用，调用成功之后进入AVTRANSCODER_PREPARED状态。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance,see [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功设置视频转码的参数设置，进入AVTRANSCODER_PREPARED状态。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码准备操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Prepare操作，或者是不支持的格式。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_Start()

```c
OH_AVErrCode OH_AVTranscoder_Start(OH_AVTranscoder *transcoder)
```

**描述**

开始转码。此函数必须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)成功调用之后调用，调用成功之后进入AVTRANSCODER_STARTED状态。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功开始转码，进入AVTRANSCODER_STARTED状态。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码开始操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Start操作。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_Pause()

```c
OH_AVErrCode OH_AVTranscoder_Pause(OH_AVTranscoder *transcoder)
```

**描述**

暂停转码。此函数必须在转码实例处于AVTRANSCODER_STARTED状态时调用，调用成功之后进入AVTRANSCODER_PAUSED状态。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功暂停转码，进入AVTRANSCODER_PAUSED状态。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码暂停操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Pause操作。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_Resume()

```c
OH_AVErrCode OH_AVTranscoder_Resume(OH_AVTranscoder *transcoder)
```

**描述**

恢复转码。此函数必须在转码实例处于AVTRANSCODER_PAUSED状态时调用，调用成功之后重新进入AVTRANSCODER_STARTED状态。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功恢复转码，进入AVTRANSCODER_STARTED状态。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码恢复操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Resume操作。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_Cancel()

```c
OH_AVErrCode OH_AVTranscoder_Cancel(OH_AVTranscoder *transcoder)
```

**描述**

取消转码。此函数须在转码实例处于AVTRANSCODER_STARTED和AVTRANSCODER_PAUSED状态时调用，调用成功之后进入AVTRANSCODER_CANCELLED状态。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功取消转码，进入AVTRANSCODER_CANCELLED状态。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码取消操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Cancel操作。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_Release()

```c
OH_AVErrCode OH_AVTranscoder_Release(OH_AVTranscoder *transcoder)
```

**描述**

释放转码实例资源。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：成功释放转码实例资源。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者转码释放资源操作失败。<br> AV_ERR_OPERATE_NOT_PERMIT：当前状态不允许执行Release操作。<br> AV_ERR_IO：IO访问相关的错误。<br> AV_ERR_SERVICE_DIED：媒体服务已停止。 |

### OH_AVTranscoder_SetStateCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetStateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnStateChange callback, void *userData)
```

**描述**

注册触发转码状态修改事件的回调方法。当触发状态修改事件时，通过注册的回调方法通知开发者。开发者只能注册一个状态修改事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码状态修改，须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册转码状态回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |
| [OH_AVTranscoder_OnStateChange](capi-avtranscoder-base-h.md#oh_avtranscoder_onstatechange) callback | State callback function, see [OH_AVTranscoder_OnStateChange](capi-avtranscoder-base-h.md#oh_avtranscoder_onstatechange) |
| void *userData | Pointer to user specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：注册成功。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者callback是空指针。 |

### OH_AVTranscoder_SetErrorCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetErrorCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnError callback, void *userData)
```

**描述**

注册触发转码错误事件的回调方法。当触发错误事件时，通过注册的回调方法通知开发者。如果AVTranscoder上报error事件，开发者需要通过[OH_AVTranscoder_Release](capi-avtranscoder-h.md#oh_avtranscoder_release)操作退出转码操作。开发者只能注册一个错误事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码错误事件，须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册转码错误事件。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |
| [OH_AVTranscoder_OnError](capi-avtranscoder-base-h.md#oh_avtranscoder_onerror) callback | Error callback function, see [OH_AVTranscoder_OnError](capi-avtranscoder-base-h.md#oh_avtranscoder_onerror) |
| void *userData | Pointer to user specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：注册成功。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者callback是空指针。 |

### OH_AVTranscoder_SetProgressUpdateCallback()

```c
OH_AVErrCode OH_AVTranscoder_SetProgressUpdateCallback(OH_AVTranscoder *transcoder, OH_AVTranscoder_OnProgressUpdate callback, void *userData)
```

**描述**

注册触发转码进度更新事件的回调方法。当触发转码进度更新事件时，通过注册的回调方法通知开发者。开发者只能注册一个错误事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。若开发者需监听转码处理进度，则须在[OH_AVTranscoder_Prepare](capi-avtranscoder-h.md#oh_avtranscoder_prepare)之前注册该事件。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder](capi-avtranscoder-oh-avtranscoder.md) *transcoder | Pointer to an OH_AVTranscoder instance |
| [OH_AVTranscoder_OnProgressUpdate](capi-avtranscoder-base-h.md#oh_avtranscoder_onprogressupdate) callback | Uri callback function,see [OH_AVTranscoder_OnProgressUpdate](capi-avtranscoder-base-h.md#oh_avtranscoder_onprogressupdate) |
| void *userData | Pointer to user specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：注册成功。<br> AV_ERR_INVALID_VAL：输入的transcoder是空指针，或者callback是空指针。 |

### OH_AVTranscoderConfig_EnableBFrame()

```c
OH_AVErrCode OH_AVTranscoderConfig_EnableBFrame(OH_AVTranscoder_Config *config, bool enabled)
```

**描述**

转码设置输出视频B帧编码。B帧视频编码相关的约束和限制可以参考文档{@link B帧视频编码约束和限制}。如果当前不符合B帧视频编码的约束和限制，将忽略B帧，按不使能B帧进行编码。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVTranscoder_Config](capi-avtranscoder-oh-avtranscoder-config.md) *config | Pointer to an OH_AVTranscoder_Config instance |
| bool enabled | Whether enable B Frame. If this function is not called, B Frame is disabled. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：设置成功。<br> AV_ERR_INVALID_VAL：输入的config为空指针。 |


