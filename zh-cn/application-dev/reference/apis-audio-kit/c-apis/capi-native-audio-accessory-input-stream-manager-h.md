# native_audio_accessory_input_stream_manager.h

## 概述

Declare audio accessory input stream manager related interfaces.

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [AudioAccessoryInputStreamManager](capi-audioaccessoryinputstreammanager.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)](#oh_audioaccessory_openinputstreamcallback) | OH_AudioAccessory_OpenInputStreamCallback | 在音频附件上打开输入流的回调。<b>When Called:</b>音频框架在应用程序从该音频附件请求音频捕获。框架将流的音频流信息传递给打开，这样附件就可以准备相应的数据路径了。<b>Usage Requirements:</b>在此回调中，您必须调用{@链接OH_AudioAccessoryInputStreamManager_RegisterStartCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterStopCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback}，以及{@链接OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback}到注册所需的流回调。这是唯一一次回电允许注册。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_startcallback) | OH_AudioAccessoryInputStream_StartCallback | 流开始事件的回调。<b>When Called:</b>流成功启动并就绪后来接收音频数据。在此回调返回后，您可以调用Write()来发送音频数据。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_stopcallback) | OH_AudioAccessoryInputStream_StopCallback | 流停止事件的回调。<b>When Called:</b>停止流后。在此回调之后返回，则必须停止调用Write()。流句柄仍然存在有效，可以再次启动。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_releasecallback) | OH_AudioAccessoryInputStream_ReleaseCallback | 流释放事件回调。<b>When Called:</b>流释放时。这一直都是流的最后一个回调。此回调返回后，流句柄不再有效，不得使用。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)](#oh_audioaccessoryinputstream_getlatencycallback) | OH_AudioAccessoryInputStream_GetLatencyCallback | 查询流的当前时延回调。<b>When Called:</b>框架何时需要当前延迟值由辅助流报告。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)](#oh_audioaccessoryinputstream_getframepositioncallback) | OH_AudioAccessoryInputStream_GetFramePositionCallback | 查询码流当前帧位置回调。<b>When Called:</b>框架何时需要当前捕获位置由辅助流报告。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)](#oh_audioaccessoryinputstreammanager_registerstartcallback) | - | 注册流启动事件的回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)](#oh_audioaccessoryinputstreammanager_registerstopcallback) | - | 注册流停止事件回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)](#oh_audioaccessoryinputstreammanager_registerreleasecallback) | - | 注册流释放事件回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)](#oh_audioaccessoryinputstreammanager_registerlatencycallback) | - | 注册码流时延查询回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)](#oh_audioaccessoryinputstreammanager_registerframepositioncallback) | - | 注册码流帧位置查询回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)](#oh_audioaccessoryinputstreammanager_write) | - | 将音频数据写入音频附件输入流。这是一个阻塞接口。函数被调用后，会阻塞，直到整帧写入成功或出错。每次调用都必须写入20毫秒的音频数据。调用者必须确保dataSize匹配当前流下20 ms对应的字节数配置。如果dataSize不匹配20 ms的音频数据，则此函数返回{@link AudioCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH}。调用方必须以20 ms的节奏调用此函数。也就是说，每次调用必须提交20 ms的音频数据，并且间隔两个连续呼叫也必须是20 ms。如果流缓冲区当前没有足够的可写空间供整个框架，此函数会阻塞，直到有足够的空间可用或发生错误。此接口不支持部分帧写入。如果最后一帧的音频数据少于20毫秒，主叫方可能会丢弃该帧或在调用此函数之前用0填充到20 ms。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)](#oh_audioaccessoryinputstreammanager_getwritablesize) | - | 获取音频配件输入码流buffer可写大小。调用方可以使用此函数来探测当前缓冲区的可用性在调用[OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write)之前。返回的可写大小仅反映当前状态，并可能立即更改函数返回后。 |

## 函数说明

### OH_AudioAccessory_OpenInputStreamCallback()

```c
typedef bool (*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)
```

**描述**

在音频附件上打开输入流的回调。<b>When Called:</b>音频框架在应用程序从该音频附件请求音频捕获。框架将流的音频流信息传递给打开，这样附件就可以准备相应的数据路径了。<b>Usage Requirements:</b>在此回调中，您必须调用{@链接OH_AudioAccessoryInputStreamManager_RegisterStartCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterStopCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback}，{@链接OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback}，以及{@链接OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback}到注册所需的流回调。这是唯一一次回电允许注册。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 打开流的音频附件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对新创建的输入流的引用。使用此句柄通过Register...Callback注册回调。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) \*streamInfo | 码流的音频码流信息指针。正在打开。该参数用于描述请求的码流格式。可以由附件用于配置其数据路径。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果接受流。</li><br> <li>`false`否则。</li><br> </ul> |

**参考：**

[OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback)


### OH_AudioAccessoryInputStream_StartCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

流开始事件的回调。<b>When Called:</b>流成功启动并就绪后来接收音频数据。在此回调返回后，您可以调用Write()来发送音频数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 拥有此流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对启动的输入流的引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果成功处理开始事件</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioAccessoryInputStream_StopCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

流停止事件的回调。<b>When Called:</b>停止流后。在此回调之后返回，则必须停止调用Write()。流句柄仍然存在有效，可以再次启动。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 拥有此流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对已停止的输入流的引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果停止事件处理成功</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioAccessoryInputStream_ReleaseCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

流释放事件回调。<b>When Called:</b>流释放时。这一直都是流的最后一个回调。此回调返回后，流句柄不再有效，不得使用。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 拥有此流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对被释放的输入流的引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果释放事件处理成功</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioAccessoryInputStream_GetLatencyCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)
```

**描述**

查询流的当前时延回调。<b>When Called:</b>框架何时需要当前延迟值由辅助流报告。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 拥有此流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对输入流的引用。 |
| int32_t \*latency | 输出参数。返回延迟（以毫秒为单位）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果成功获取延迟</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioAccessoryInputStream_GetFramePositionCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)
```

**描述**

查询码流当前帧位置回调。<b>When Called:</b>框架何时需要当前捕获位置由辅助流报告。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 拥有此流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | 对输入流的引用。 |
| int64_t \*framePosition | 输出参数。返回音频的累计数量自该输入最近一次成功启动以来捕获的帧流。 |
| int64_t \*timestamp | 输出参数。返回捕获时间戳对应{@p framePosition}上报的帧位置。时间戳必须使用{@link CLOCK_MONOTONIC}时基，并且是以纳秒表示。它表示单调时钟时间在捕获了{@p framePosition}所标识的帧。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果成功获取帧位置</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStartCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)
```

**描述**

注册流启动事件的回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_StartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_startcallback) callback | 回调函数指针。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> 如果在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用，则释放流。<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStopCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)
```

**描述**

注册流停止事件回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_StopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_stopcallback) callback | 回调函数指针。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> 如果在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用，则释放流。<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)
```

**描述**

注册流释放事件回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_ReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_releasecallback) callback | 回调函数指针。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> 如果在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用，则释放流。<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)
```

**描述**

注册码流时延查询回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_GetLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getlatencycallback) callback | 回调函数指针。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> 如果在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用，则释放流。<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)
```

**描述**

注册码流帧位置查询回调。<b>CRITICAL: Registration Timing Constraint</b>此函数必须仅在执行{@链接OH_AudioAccessory_OpenInputStreamCallback}。叫这个在任何其他时间执行的函数都将导致{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。<b>Requirement:</b>此回调是强制的。如果未注册，框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_GetFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getframepositioncallback) callback | 回调函数指针。不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> 如果在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用，则释放流。<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_Write()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)
```

**描述**

将音频数据写入音频附件输入流。这是一个阻塞接口。函数被调用后，会阻塞，直到整帧写入成功或出错。每次调用都必须写入20毫秒的音频数据。调用者必须确保dataSize匹配当前流下20 ms对应的字节数配置。如果dataSize不匹配20 ms的音频数据，则此函数返回{@link AudioCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH}。调用方必须以20 ms的节奏调用此函数。也就是说，每次调用必须提交20 ms的音频数据，并且间隔两个连续呼叫也必须是20 ms。如果流缓冲区当前没有足够的可写空间供整个框架，此函数会阻塞，直到有足够的空间可用或发生错误。此接口不支持部分帧写入。如果最后一帧的音频数据少于20毫秒，主叫方可能会丢弃该帧或在调用此函数之前用0填充到20 ms。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| const uint8_t *data | 指向音频数据缓冲区的指针。不能为空。 |
| uint32_t dataSize | 音频数据的大小，以字节为单位。必须大于0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> <li>[AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH](capi-native-audio-common-h.md#oh_audiocommon_result)如果dataSize不对应当前流配置下的20 ms音频数据。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}如果流未启动或所需的流回调未完全注册。</li><br> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果音频服务器进程死掉。</li><br> </ul> |

### OH_AudioAccessoryInputStreamManager_GetWritableSize()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)
```

**描述**

获取音频配件输入码流buffer可写大小。调用方可以使用此函数来探测当前缓冲区的可用性在调用[OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write)之前。返回的可写大小仅反映当前状态，并可能立即更改函数返回后。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | 输入流句柄指针。 |
| uint32_t *writableSize | 输出参数。返回可以写入的字节数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数为空，则<li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)。</li><br> <li>{@link AudioCommon_RESULT_ERROR_ILAL_STATE}如果流被释放。</li><br> </ul> |


