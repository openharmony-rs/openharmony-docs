# native_audio_accessory_input_stream_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频配件输入流管理器相关接口。

**引用文件：** <ohaudio/native_audio_accessory_input_stream_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数指针

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) | 框架打开音频配件输入流时触发的回调。 |
| [OH_AudioAccessoryInputStream_StartCallback](#oh_audioaccessoryinputstream_startcallback) | 输入流启动后触发的回调。 |
| [OH_AudioAccessoryInputStream_StopCallback](#oh_audioaccessoryinputstream_stopcallback) | 输入流停止后触发的回调。 |
| [OH_AudioAccessoryInputStream_ReleaseCallback](#oh_audioaccessoryinputstream_releasecallback) | 输入流释放时触发的回调。 |
| [OH_AudioAccessoryInputStream_GetLatencyCallback](#oh_audioaccessoryinputstream_getlatencycallback) | 查询当前输入流底层时延的回调。 |
| [OH_AudioAccessoryInputStream_GetFramePositionCallback](#oh_audioaccessoryinputstream_getframepositioncallback) | 查询当前帧位置的回调。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStreamManager_RegisterStartCallback](#oh_audioaccessoryinputstreammanager_registerstartcallback) | 注册输入流启动回调。 |
| [OH_AudioAccessoryInputStreamManager_RegisterStopCallback](#oh_audioaccessoryinputstreammanager_registerstopcallback) | 注册输入流停止回调。 |
| [OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](#oh_audioaccessoryinputstreammanager_registerreleasecallback) | 注册输入流释放回调。 |
| [OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](#oh_audioaccessoryinputstreammanager_registerlatencycallback) | 注册输入流时延查询回调。 |
| [OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](#oh_audioaccessoryinputstreammanager_registerframepositioncallback) | 注册输入流帧位置查询回调。 |
| [OH_AudioAccessoryInputStreamManager_Write](#oh_audioaccessoryinputstreammanager_write) | 向音频配件输入流写入音频数据。 |
| [OH_AudioAccessoryInputStreamManager_GetWritableSize](#oh_audioaccessoryinputstreammanager_getwritablesize) | 获取输入流缓冲区当前可写大小。 |

## 函数指针说明

### OH_AudioAccessory_OpenInputStreamCallback

```c
typedef bool (*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)
```

**描述**

当应用请求从该音频配件采集音频时触发。调用方必须在此回调中注册启动、停止、释放、时延和帧位置回调。此回调执行期间是唯一允许注册流回调的时机。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示流打开成功；返回 **false** 表示流打开失败。

### OH_AudioAccessoryInputStream_StartCallback

```c
typedef bool (*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流启动并可接收音频数据后触发。此回调返回后，调用方可写入音频数据。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示启动事件处理成功；返回 **false** 表示启动事件处理失败。

### OH_AudioAccessoryInputStream_StopCallback

```c
typedef bool (*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流停止后触发。此回调返回后应停止写入音频数据。流句柄仍有效，可再次启动。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示停止事件处理成功；返回 **false** 表示停止事件处理失败。

### OH_AudioAccessoryInputStream_ReleaseCallback

```c
typedef bool (*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流释放时触发。这是流的最后一个回调。回调返回后，流句柄失效。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示释放事件处理成功；返回 **false** 表示释放事件处理失败。

### OH_AudioAccessoryInputStream_GetLatencyCallback

```c
typedef bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)
```

**描述**

框架需要获取当前底层时延时触发，时延单位为毫秒。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示获取时延成功；返回 **false** 表示获取时延失败。

### OH_AudioAccessoryInputStream_GetFramePositionCallback

```c
typedef bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)
```

**描述**

框架需要获取当前采集位置时触发。**framePosition** 表示自最近一次成功启动输入流以来累计采集的音频帧数。**timestamp** 使用 `CLOCK_MONOTONIC` 时基，单位为纳秒，表示 **framePosition** 所标识帧被采集时的单调时钟时间。

**起始版本：** 26.0.0

**返回值**

返回 **true** 表示获取帧位置成功；返回 **false** 表示获取帧位置失败。

## 函数说明

### OH_AudioAccessoryInputStreamManager_RegisterStartCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)
```

**描述**

注册输入流启动回调。该回调为必选回调，仅允许在 [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) 执行期间注册。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示未在打开输入流回调中调用或流已释放。

### OH_AudioAccessoryInputStreamManager_RegisterStopCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)
```

**描述**

注册输入流停止回调。该回调为必选回调，仅允许在 [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) 执行期间注册。

**起始版本：** 26.0.0

### OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)
```

**描述**

注册输入流释放回调。该回调为必选回调，仅允许在 [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) 执行期间注册。

**起始版本：** 26.0.0

### OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)
```

**描述**

注册输入流时延查询回调。该回调为必选回调，仅允许在 [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) 执行期间注册。

**起始版本：** 26.0.0

### OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)
```

**描述**

注册输入流帧位置查询回调。该回调为必选回调，仅允许在 [OH_AudioAccessory_OpenInputStreamCallback](#oh_audioaccessory_openinputstreamcallback) 执行期间注册。

**起始版本：** 26.0.0

### OH_AudioAccessoryInputStreamManager_Write()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)
```

**描述**

向输入流写入音频数据。该接口为阻塞接口。每次调用必须写入完整20ms的音频数据，调用方必须确保 **dataSize** 与当前流配置下20ms对应的字节数一致，两次连续调用之间也应保持20ms间隔。不支持写入非完整帧。最后一帧不足20ms时，可丢弃或补零到20ms后再写入。

该接口对同一输入流不可重入，建议使用一个线程串行写入同一输入流。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数为空；**AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH** 表示 **dataSize** 与当前流配置下20ms音频数据不对应；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示流未启动或必须注册的流回调未全部注册；**AUDIOCOMMON_RESULT_ERROR_SYSTEM** 表示音频服务进程死亡。

### OH_AudioAccessoryInputStreamManager_GetWritableSize()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)
```

**描述**

获取输入流缓冲区当前可写大小。返回值仅反映当前状态，函数返回后可能立即变化。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示流已释放。
