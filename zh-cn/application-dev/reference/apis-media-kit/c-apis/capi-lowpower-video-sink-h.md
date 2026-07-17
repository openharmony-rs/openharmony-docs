# lowpower_video_sink.h

## 概述

定义LowPowerVideoSink接口。使用LowPowerVideoSink提供的Native API进行视频通路的低功耗播放。

**库：** liblowpower_avsink.so

**系统能力：** SystemCapability.Multimedia.Media.LowPowerAVSink

**起始版本：** 20

**相关模块：** [LowPowerVideoSink](capi-lowpowervideosink.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_LowPowerVideoSink* OH_LowPowerVideoSink_CreateByMime(const char* mime)](#oh_lowpowervideosink_createbymime) | 创建低功耗LowPowerVideoSink。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Configure(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)](#oh_lowpowervideosink_configure) | 配置LowPowerVideoSink，需要在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)前完成。 |
| [OH_AVErrCode OH_LowPowerVideoSink_SetParameter(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)](#oh_lowpowervideosink_setparameter) | 为LowPowerVideoSink设置参数，支持[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)后动态设置。 |
| [OH_AVErrCode OH_LowPowerVideoSink_GetParameter(OH_LowPowerVideoSink* sink, OH_AVFormat* format)](#oh_lowpowervideosink_getparameter) | 获取LowPowerVideoSink的相关参数。 |
| [OH_AVErrCode OH_LowPowerVideoSink_SetVideoSurface(OH_LowPowerVideoSink* sink, const OHNativeWindow* surface)](#oh_lowpowervideosink_setvideosurface) | 为LowPowerVideoSink设置渲染画面窗口。 需要在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)前完成。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Prepare(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_prepare) | 开始LowPowerVideoSink准备，需要在[OH_LowPowerVideoSink_SetSyncAudioSink](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_setsyncaudiosink)之后调用。 |
| [OH_AVErrCode OH_LowPowerVideoSink_StartDecoder(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_startdecoder) | 开始LowPowerVideoSink解码，在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)后或非播放中[OH_LowPowerVideoSink_SetTargetStartFrame](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_settargetstartframe)后调用。启动成功后，LowPowerVideoSink将开始上报[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件。 |
| [OH_AVErrCode OH_LowPowerVideoSink_RenderFirstFrame(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_renderfirstframe) | 渲染LowPowerVideoSink解码出的第一帧，在[OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder)之后调用。 |
| [OH_AVErrCode OH_LowPowerVideoSink_StartRenderer(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_startrenderer) | 开始LowPowerVideoSink渲染，在[OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder)之后调用。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Pause(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_pause) | 暂停LowPowerVideoSink，在[OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer)或[OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume)后调用。暂停成功后，LowPowerVideoSink将暂停[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件的上报。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Resume(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_resume) | 恢复LowPowerVideoSink，在[OH_LowPowerVideoSink_Pause](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_pause)后调用。恢复成功后，LowPowerVideoSink将恢复[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件的上报。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Flush(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_flush) | 清除LowPowerVideoSink中所有解码器和渲染缓存的输入输出数据。此接口不建议在[OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer)或[OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume)之后调用。需要注意的是，如果编解码器之前已输入数据，则需要重新输入编解码器数据。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Stop(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_stop) | 停止LowPowerVideoSink。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Reset(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_reset) | 重置LowPowerVideoSink。如果要重新使用该实例，需要调用[OH_LowPowerVideoSink_Configure](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_configure)完成配置。 |
| [OH_AVErrCode OH_LowPowerVideoSink_Destroy(OH_LowPowerVideoSink* sink)](#oh_lowpowervideosink_destroy) | 清理解码器内部资源，销毁LowPowerVideoSink实例。不能重复销毁。 |
| [OH_AVErrCode OH_LowPowerVideoSink_SetSyncAudioSink(OH_LowPowerVideoSink* videoSink, OH_LowPowerAudioSink* audioSink)](#oh_lowpowervideosink_setsyncaudiosink) | LowPowerVideoSink设置用于音画同步的OH_LowPowerAudioSink。 |
| [OH_AVErrCode OH_LowPowerVideoSink_SetTargetStartFrame(OH_LowPowerVideoSink* sink, const int64_t framePts, OH_LowPowerVideoSink_OnTargetArrived onTargetArrived, const int64_t timeoutMs, void* userData)](#oh_lowpowervideosink_settargetstartframe) | 为LowPowerVideoSink设置目标渲染帧。 |
| [OH_AVErrCode OH_LowPowerVideoSink_SetPlaybackSpeed(OH_LowPowerVideoSink* sink, const float speed)](#oh_lowpowervideosink_setplaybackspeed) | 为LowPowerVideoSink设置播放倍速。 |
| [OH_AVErrCode OH_LowPowerVideoSink_ReturnSamples(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* samples)](#oh_lowpowervideosink_returnsamples) | 给LowPowerVideoSink输入buffer。 |
| [OH_AVErrCode OH_LowPowerVideoSink_RegisterCallback(OH_LowPowerVideoSink* sink, OH_LowPowerVideoSinkCallback* callback)](#oh_lowpowervideosink_registercallback) | 为LowPowerVideoSink注册回调。 |
| [OH_LowPowerVideoSinkCallback* OH_LowPowerVideoSinkCallback_Create(void)](#oh_lowpowervideosinkcallback_create) | 创建OH_LowPowerVideoSinkCallback。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_Destroy(OH_LowPowerVideoSinkCallback* callback)](#oh_lowpowervideosinkcallback_destroy) | 销毁OH_LowPowerVideoSinkCallback对象。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetDataNeededListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnDataNeeded onDataNeeded, void* userData)](#oh_lowpowervideosinkcallback_setdataneededlistener) | 为LowPowerVideoSinkCallback设置需要数据监听。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetErrorListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnError onError, void* userData)](#oh_lowpowervideosinkcallback_seterrorlistener) | 为LowPowerVideoSinkCallback回调设置错误监听。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetRenderStartListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnRenderStarted onRenderStarted, void* userData)](#oh_lowpowervideosinkcallback_setrenderstartlistener) | 为LowPowerVideoSinkCallback回调设置开始渲染监听。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetStreamChangedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnStreamChanged onStreamChanged, void* userData)](#oh_lowpowervideosinkcallback_setstreamchangedlistener) | 为LowPowerVideoSinkCallback回调设置流切换监听。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded, void* userData)](#oh_lowpowervideosinkcallback_setfirstframedecodedlistener) | 为LowPowerVideoSinkCallback回调设置首帧准备完成监听。 |
| [OH_AVErrCode OH_LowPowerVideoSinkCallback_SetEosListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnEos onEos, void* userData)](#oh_lowpowervideosinkcallback_seteoslistener) | 为LowPowerVideoSinkCallback回调设置播放结束监听。 |
| [OH_AVErrCode OH_LowPowerVideoSink_GetLatestPts(OH_LowPowerVideoSink *sink, int64_t *pts)](#oh_lowpowervideosink_getlatestpts) | 获取当前播放的视频显示时间戳（pts）。 |

## 函数说明

### OH_LowPowerVideoSink_CreateByMime()

```c
OH_LowPowerVideoSink* OH_LowPowerVideoSink_CreateByMime(const char* mime)
```

**描述**

创建低功耗LowPowerVideoSink。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* mime | mime type description string, refer to {@link AVCODEC_MIME_TYPE} |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_LowPowerVideoSink* | 如果创建成功返回指向OH_LowPowerVideoSink实例的指针，否则返回空指针。 |

### OH_LowPowerVideoSink_Configure()

```c
OH_AVErrCode OH_LowPowerVideoSink_Configure(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)
```

**描述**

配置LowPowerVideoSink，需要在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)前完成。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OH_AVFormat* format | A pointer to an OH_AVFormat to give the description of the video track to be decoded,key of format refer to lowpower_avsink_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_UNSUPPORT：不支持的格式。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_SetParameter()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetParameter(OH_LowPowerVideoSink* sink, const OH_AVFormat* format)
```

**描述**

为LowPowerVideoSink设置参数，支持[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)后动态设置。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OH_AVFormat* format | pointer to an OH_AVFormat instance, key of format refer to lowpower_avsink_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_UNSUPPORT：不支持的格式。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_GetParameter()

```c
OH_AVErrCode OH_LowPowerVideoSink_GetParameter(OH_LowPowerVideoSink* sink, OH_AVFormat* format)
```

**描述**

获取LowPowerVideoSink的相关参数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| OH_AVFormat* format | pointer to an OH_AVFormat instance, key of format refer to lowpower_avsink_base.h |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_SetVideoSurface()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetVideoSurface(OH_LowPowerVideoSink* sink, const OHNativeWindow* surface)
```

**描述**

为LowPowerVideoSink设置渲染画面窗口。 需要在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)前完成。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const OHNativeWindow* surface | A pointer to a OHNativeWindow instance, see [OHNativeWindow](../ArkGraphics2D/capi-nativewindow-nativewindow.md) |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Prepare()

```c
OH_AVErrCode OH_LowPowerVideoSink_Prepare(OH_LowPowerVideoSink* sink)
```

**描述**

开始LowPowerVideoSink准备，需要在[OH_LowPowerVideoSink_SetSyncAudioSink](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_setsyncaudiosink)之后调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_UNSUPPORT：不支持的格式。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_StartDecoder()

```c
OH_AVErrCode OH_LowPowerVideoSink_StartDecoder(OH_LowPowerVideoSink* sink)
```

**描述**

开始LowPowerVideoSink解码，在[OH_LowPowerVideoSink_Prepare](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_prepare)后或非播放中[OH_LowPowerVideoSink_SetTargetStartFrame](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_settargetstartframe)后调用。启动成功后，LowPowerVideoSink将开始上报[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_UNSUPPORT：不支持的格式。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_RenderFirstFrame()

```c
OH_AVErrCode OH_LowPowerVideoSink_RenderFirstFrame(OH_LowPowerVideoSink* sink)
```

**描述**

渲染LowPowerVideoSink解码出的第一帧，在[OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder)之后调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_StartRenderer()

```c
OH_AVErrCode OH_LowPowerVideoSink_StartRenderer(OH_LowPowerVideoSink* sink)
```

**描述**

开始LowPowerVideoSink渲染，在[OH_LowPowerVideoSink_StartDecoder](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startdecoder)之后调用。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_UNSUPPORT：不支持的格式。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Pause()

```c
OH_AVErrCode OH_LowPowerVideoSink_Pause(OH_LowPowerVideoSink* sink)
```

**描述**

暂停LowPowerVideoSink，在[OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer)或[OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume)后调用。暂停成功后，LowPowerVideoSink将暂停[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件的上报。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Resume()

```c
OH_AVErrCode OH_LowPowerVideoSink_Resume(OH_LowPowerVideoSink* sink)
```

**描述**

恢复LowPowerVideoSink，在[OH_LowPowerVideoSink_Pause](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_pause)后调用。恢复成功后，LowPowerVideoSink将恢复[OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded)事件的上报。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSinkinstance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Flush()

```c
OH_AVErrCode OH_LowPowerVideoSink_Flush(OH_LowPowerVideoSink* sink)
```

**描述**

清除LowPowerVideoSink中所有解码器和渲染缓存的输入输出数据。此接口不建议在[OH_LowPowerVideoSink_StartRenderer](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_startrenderer)或[OH_LowPowerVideoSink_Resume](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_resume)之后调用。需要注意的是，如果编解码器之前已输入数据，则需要重新输入编解码器数据。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Stop()

```c
OH_AVErrCode OH_LowPowerVideoSink_Stop(OH_LowPowerVideoSink* sink)
```

**描述**

停止LowPowerVideoSink。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Reset()

```c
OH_AVErrCode OH_LowPowerVideoSink_Reset(OH_LowPowerVideoSink* sink)
```

**描述**

重置LowPowerVideoSink。如果要重新使用该实例，需要调用[OH_LowPowerVideoSink_Configure](capi-lowpower-video-sink-h.md#oh_lowpowervideosink_configure)完成配置。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_Destroy()

```c
OH_AVErrCode OH_LowPowerVideoSink_Destroy(OH_LowPowerVideoSink* sink)
```

**描述**

清理解码器内部资源，销毁LowPowerVideoSink实例。不能重复销毁。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_SetSyncAudioSink()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetSyncAudioSink(OH_LowPowerVideoSink* videoSink, OH_LowPowerAudioSink* audioSink)
```

**描述**

LowPowerVideoSink设置用于音画同步的OH_LowPowerAudioSink。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* videoSink | Pointer to an OH_LowPowerVideoSink instance |
| OH_LowPowerAudioSink* audioSink | Pointer to an OH_LowPowerAudioSink instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_SetTargetStartFrame()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetTargetStartFrame(OH_LowPowerVideoSink* sink, const int64_t framePts, OH_LowPowerVideoSink_OnTargetArrived onTargetArrived, const int64_t timeoutMs, void* userData)
```

**描述**

为LowPowerVideoSink设置目标渲染帧。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const int64_t framePts | target video frame pts, in microseconds |
| OH_LowPowerVideoSink_OnTargetArrived onTargetArrived | OH_LowPowerVideoSink_OnTargetArrived func,will be called once, refer to [OH_LowPowerVideoSink_OnTargetArrived](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ontargetarrived) |
| const int64_t timeoutMs | if wait first frame over timeoutMs, onTargetArrived will be called directly,in milliseconds. |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_SetPlaybackSpeed()

```c
OH_AVErrCode OH_LowPowerVideoSink_SetPlaybackSpeed(OH_LowPowerVideoSink* sink, const float speed)
```

**描述**

为LowPowerVideoSink设置播放倍速。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| const float speed | Indicates the value of the playback rate.The current version is valid in the range of 0.25-4.0 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_ReturnSamples()

```c
OH_AVErrCode OH_LowPowerVideoSink_ReturnSamples(OH_LowPowerVideoSink* sink, OH_AVSamplesBuffer* samples)
```

**描述**

给LowPowerVideoSink输入buffer。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| [OH_AVSamplesBuffer](capi-avsinkbase-oh-avsamplesbuffer.md)* samples | Pointer to an OH_AVSamplesBuffer instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_RegisterCallback()

```c
OH_AVErrCode OH_LowPowerVideoSink_RegisterCallback(OH_LowPowerVideoSink* sink, OH_LowPowerVideoSinkCallback* callback)
```

**描述**

为LowPowerVideoSink注册回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink* sink | Pointer to an OH_LowPowerVideoSink instance |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_Create()

```c
OH_LowPowerVideoSinkCallback* OH_LowPowerVideoSinkCallback_Create(void)
```

**描述**

创建OH_LowPowerVideoSinkCallback。

**起始版本：** 20

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* | 返回指向OH_LowPowerVideoSinkCallback实例的指针。如果内存不足，则返回nullptr。 |

### OH_LowPowerVideoSinkCallback_Destroy()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_Destroy(OH_LowPowerVideoSinkCallback* callback)
```

**描述**

销毁OH_LowPowerVideoSinkCallback对象。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。 |

### OH_LowPowerVideoSinkCallback_SetDataNeededListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetDataNeededListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnDataNeeded onDataNeeded, void* userData)
```

**描述**

为LowPowerVideoSinkCallback设置需要数据监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnDataNeeded onDataNeeded | OH_LowPowerVideoSink_OnDataNeeded function,refer to [OH_LowPowerVideoSink_OnDataNeeded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_ondataneeded) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_SetErrorListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetErrorListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnError onError, void* userData)
```

**描述**

为LowPowerVideoSinkCallback回调设置错误监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnError onError | OH_LowPowerVideoSink_OnError function,refer to [OH_LowPowerVideoSink_OnError](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onerror) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_SetRenderStartListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetRenderStartListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnRenderStarted onRenderStarted, void* userData)
```

**描述**

为LowPowerVideoSinkCallback回调设置开始渲染监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnRenderStarted onRenderStarted | OH_LowPowerVideoSink_OnRenderStarted function,refer to [OH_LowPowerVideoSink_OnRenderStarted](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onrenderstarted) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_SetStreamChangedListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetStreamChangedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnStreamChanged onStreamChanged, void* userData)
```

**描述**

为LowPowerVideoSinkCallback回调设置流切换监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnStreamChanged onStreamChanged | OH_LowPowerVideoSink_OnStreamChanged function,refer to [OH_LowPowerVideoSink_OnStreamChanged](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onstreamchanged) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetFirstFrameDecodedListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded, void* userData)
```

**描述**

为LowPowerVideoSinkCallback回调设置首帧准备完成监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnFirstFrameDecoded onFirstFrameDecoded | OH_LowPowerVideoSink_OnFirstFrameDecodedfunction,refer to [OH_LowPowerVideoSink_OnFirstFrameDecoded](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_onfirstframedecoded) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSinkCallback_SetEosListener()

```c
OH_AVErrCode OH_LowPowerVideoSinkCallback_SetEosListener(OH_LowPowerVideoSinkCallback* callback, OH_LowPowerVideoSink_OnEos onEos, void* userData)
```

**描述**

为LowPowerVideoSinkCallback回调设置播放结束监听。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSinkCallback* callback | Pointer to an OH_LowPowerVideoSinkCallback instance |
| OH_LowPowerVideoSink_OnEos onEos | OH_LowPowerVideoSink_OnEos function,refer to [OH_LowPowerVideoSink_OnEos](capi-lowpower-video-sink-base-h.md#oh_lowpowervideosink_oneos) |
| void* userData | User specific data |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |

### OH_LowPowerVideoSink_GetLatestPts()

```c
OH_AVErrCode OH_LowPowerVideoSink_GetLatestPts(OH_LowPowerVideoSink *sink, int64_t *pts)
```

**描述**

获取当前播放的视频显示时间戳（pts）。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_LowPowerVideoSink *sink | Pointer to an OH_LowPowerVideoSink instance. |
| int64_t *pts | Pointer to store the latest PTS value (in microseconds). |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](../AVCodecKit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK：执行成功。<br> AV_ERR_INVALID_VAL：参数为nullptr或参数非法。<br> AV_ERR_SERVICE_DIED：媒体服务端已销毁。<br> AV_ERR_OPERATE_NOT_PERMIT：操作不支持。 |


