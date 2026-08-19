# native_audio_accessory_input_stream_manager.h

## 概述

声明音频配件输入流管理器相关接口。该文件接口用于管理音频配件的输入音频流，包括回调注册、数据写入和缓冲区查询等功能。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)](#oh_audioaccessory_openinputstreamcallback) | OH_AudioAccessory_OpenInputStreamCallback | 音频配件打开输入流的回调函数。<b>触发时机：</b>当应用请求从该音频配件采集音频时，音频框架调用此回调。框架传递正在打开的音频流信息，以便配件准备相应的数据通路。<b>使用要求：</b>在此回调中，必须调用[OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback)、[OH_AudioAccessoryInputStreamManager_RegisterStopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstopcallback)、[OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerreleasecallback)、[OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerlatencycallback)和[OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerframepositioncallback)注册必需的流回调。此回调是唯一允许注册回调的时机。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_startcallback) | OH_AudioAccessoryInputStream_StartCallback | 输入流启动事件回调函数。<b>触发时机：</b>流成功启动并准备好接收音频数据后触发。此回调返回后，可以调用Write()发送音频数据。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_stopcallback) | OH_AudioAccessoryInputStream_StopCallback | 输入流停止事件回调函数。<b>触发时机：</b>流停止后触发。此回调返回后，必须停止调用Write()。流句柄仍然有效，可以再次启动。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)](#oh_audioaccessoryinputstream_releasecallback) | OH_AudioAccessoryInputStream_ReleaseCallback | 输入流释放事件回调函数。<b>触发时机：</b>流正在被释放时触发。这是流的最后一个回调。此回调返回后，流句柄不再有效，不得继续使用。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)](#oh_audioaccessoryinputstream_getlatencycallback) | OH_AudioAccessoryInputStream_GetLatencyCallback | 查询输入流当前时延的回调函数。<b>触发时机：</b>当框架需要获取配件流上报的当前时延值时触发。 |
| [typedef bool (\*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)](#oh_audioaccessoryinputstream_getframepositioncallback) | OH_AudioAccessoryInputStream_GetFramePositionCallback | 查询输入流当前帧位置的回调函数。<b>触发时机：</b>当框架需要获取该音频配件（外部音频设备，如大疆 Mic 2）上的输入流上报的当前采集位置时触发。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)](#oh_audioaccessoryinputstreammanager_registerstartcallback) | - | 注册输入流启动事件回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)](#oh_audioaccessoryinputstreammanager_registerstopcallback) | - | 注册输入流停止事件回调函数。此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)](#oh_audioaccessoryinputstreammanager_registerreleasecallback) | - | 注册输入流释放事件回调函数。此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)](#oh_audioaccessoryinputstreammanager_registerlatencycallback) | - | 注册输入流时延查询回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)](#oh_audioaccessoryinputstreammanager_registerframepositioncallback) | - | 注册输入流帧位置查询回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)](#oh_audioaccessoryinputstreammanager_write) | - | 向音频配件输入流写入音频数据。此接口为阻塞接口。调用后，函数将阻塞直到整帧数据写入成功或发生错误。每次调用必须写入完整20ms的音频数据。调用方必须确保dataSize与当前流配置下20ms对应的字节数一致。如果dataSize不匹配20ms的音频数据，本函数返回[AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH](capi-native-audio-common-h.md#oh_audiocommon_result)。调用方必须以20ms的节奏调用此函数，即每次调用提交20ms音频数据，连续两次调用之间的间隔也必须为20ms。如果流缓冲区当前没有足够的可写空间容纳整帧数据，本函数将阻塞直到有足够空间或发生错误。此接口不支持部分帧写入。如果最后一帧不足20ms的音频数据，调用方可以丢弃该帧或用零填充至20ms后再调用本函数。<b>调用上下文与并发：</b>本函数对同一流不可重入。建议调用方仅使用一个线程串行地向同一流写入音频数据。如果本函数与同一流的停止或释放回调并发调用，当停止或释放操作先于本函数获取锁完成时，本函数返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。 |
| [OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)](#oh_audioaccessoryinputstreammanager_getwritablesize) | - | 获取音频配件输入流缓冲区的可写大小。调用方可使用此函数在调用[OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write)之前探测当前缓冲区可用空间。返回的可写大小仅反映当前状态，函数返回后可能立即发生变化。 |

## 函数说明

### OH_AudioAccessory_OpenInputStreamCallback()

```c
typedef bool (*OH_AudioAccessory_OpenInputStreamCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, OH_AudioStreamInfo *streamInfo)
```

**描述**

音频配件打开输入流的回调函数。<b>触发时机：</b>当应用请求从该音频配件采集音频时，音频框架调用此回调。框架传递正在打开的音频流信息，以便配件准备相应的数据通路。<b>使用要求：</b>在此回调中，必须调用[OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback)、[OH_AudioAccessoryInputStreamManager_RegisterStopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstopcallback)、[OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerreleasecallback)、[OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerlatencycallback)和[OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerframepositioncallback)注册必需的流回调。此回调是唯一允许注册回调的时机。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 打开流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 新创建的输入流引用。使用此句柄通过Register...Callback注册回调。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) \*streamInfo | [in] 正在打开的流的音频流信息指针。此参数描述请求的流格式，配件可使用此信息配置数据通路。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：流打开成功。</li>          <li>false：流打开失败。</li>          </ul> |

**参考：**

[OH_AudioAccessoryInputStreamManager_RegisterStartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_registerstartcallback)


### OH_AudioAccessoryInputStream_StartCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StartCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流启动事件回调函数。<b>触发时机：</b>流成功启动并准备好接收音频数据后触发。此回调返回后，可以调用Write()发送音频数据。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 拥有该流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 已启动的输入流引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：启动事件处理成功。</li>          <li>false：启动事件处理失败。</li>          </ul> |

### OH_AudioAccessoryInputStream_StopCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_StopCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流停止事件回调函数。<b>触发时机：</b>流停止后触发。此回调返回后，必须停止调用Write()。流句柄仍然有效，可以再次启动。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 拥有该流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 已停止的输入流引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：停止事件处理成功。</li>          <li>false：停止事件处理失败。</li>          </ul> |

### OH_AudioAccessoryInputStream_ReleaseCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_ReleaseCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream)
```

**描述**

输入流释放事件回调函数。<b>触发时机：</b>流正在被释放时触发。这是流的最后一个回调。此回调返回后，流句柄不再有效，不得继续使用。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 拥有该流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 已释放的输入流（录音/采集流）引用。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：释放事件处理成功。</li>          <li>false：释放事件处理失败。</li>          </ul> |

### OH_AudioAccessoryInputStream_GetLatencyCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetLatencyCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int32_t *latency)
```

**描述**

查询输入流当前时延的回调函数。<b>触发时机：</b>当框架需要获取配件流上报的当前时延值时触发。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 拥有该流的音频配件。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 输入流引用。 |
| int32_t \*latency | [out] 输出参数，返回时延值，单位为毫秒。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：获取时延成功。</li>          <li>false：获取时延失败。</li>          </ul> |

### OH_AudioAccessoryInputStream_GetFramePositionCallback()

```c
typedef bool (*OH_AudioAccessoryInputStream_GetFramePositionCallback)(OH_AudioAccessory *accessory, OH_AudioAccessoryInputStream *stream, int64_t *framePosition, int64_t *timestamp)
```

**描述**

查询输入流当前帧位置的回调函数。<b>触发时机：</b>当框架需要获取该音频配件（外部音频设备，如大疆 Mic 2）上的输入流上报的当前采集位置时触发。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) \*accessory | [in] 拥有该流的音频配件（外部音频设备，如大疆 Mic 2）。 |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) \*stream | [in] 输入流引用。 |
| int64_t \*framePosition | [out] 输出参数，返回自该输入流最近一次成功启动以来累计采集的音频帧数。 |
| int64_t \*timestamp | [out] 输出参数，返回与framePosition对应的采集时间戳。时间戳必须使用{@link CLOCK_MONOTONIC}时间基准，以纳秒为单位，表示framePosition所标识帧被采集时的单调时钟时间。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul>          <li>true：获取帧位置成功。</li>          <li>false：获取帧位置失败。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStartCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStartCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StartCallback callback)
```

**描述**

注册输入流启动事件回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_StartCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_startcallback) callback | [in] 回调函数指针，不可为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：在              [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用或流已释放。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterStopCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterStopCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_StopCallback callback)
```

**描述**

注册输入流停止事件回调函数。此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_StopCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_stopcallback) callback | [in] 回调函数指针，不可为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：在              [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用或流已释放。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterReleaseCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_ReleaseCallback callback)
```

**描述**

注册输入流释放事件回调函数。此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_ReleaseCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_releasecallback) callback | [in] 回调函数指针，不可为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：在              [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用或流已释放。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterLatencyCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetLatencyCallback callback)
```

**描述**

注册输入流时延查询回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_GetLatencyCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getlatencycallback) callback | [in] 回调函数指针，不可为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：在              [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用或流已释放。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_RegisterFramePositionCallback(OH_AudioAccessoryInputStream *stream, OH_AudioAccessoryInputStream_GetFramePositionCallback callback)
```

**描述**

注册输入流帧位置查询回调函数。<b>关键约束：注册时机限制</b>此函数必须在[OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)执行期间调用。在其他任何时间调用此函数将返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。<b>要求：</b>此回调必须注册。如果未注册，音频框架将拒绝流创建并触发清理。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| [OH_AudioAccessoryInputStream_GetFramePositionCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstream_getframepositioncallback) callback | [in] 回调函数指针，不可为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：在              [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback)外部调用或流已释放。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_Write()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_Write(OH_AudioAccessoryInputStream *stream, const uint8_t *data, uint32_t dataSize)
```

**描述**

向音频配件输入流写入音频数据。此接口为阻塞接口。调用后，函数将阻塞直到整帧数据写入成功或发生错误。每次调用必须写入完整20ms的音频数据。调用方必须确保dataSize与当前流配置下20ms对应的字节数一致。如果dataSize不匹配20ms的音频数据，本函数返回[AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH](capi-native-audio-common-h.md#oh_audiocommon_result)。调用方必须以20ms的节奏调用此函数，即每次调用提交20ms音频数据，连续两次调用之间的间隔也必须为20ms。如果流缓冲区当前没有足够的可写空间容纳整帧数据，本函数将阻塞直到有足够空间或发生错误。此接口不支持部分帧写入。如果最后一帧不足20ms的音频数据，调用方可以丢弃该帧或用零填充至20ms后再调用本函数。<b>调用上下文与并发：</b>本函数对同一流不可重入。建议调用方仅使用一个线程串行地向同一流写入音频数据。如果本函数与同一流的停止或释放回调并发调用，当停止或释放操作先于本函数获取锁完成时，本函数返回[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| const uint8_t *data | [in] 音频数据缓冲区指针，不可为空。 |
| uint32_t dataSize | [in] 音频数据大小，单位为字节，必须大于0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_FRAME_LENGTH_MISMATCH](capi-native-audio-common-h.md#oh_audiocommon_result)：              dataSize与当前流配置下20ms音频数据不对应。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：流未启动或必须注册的流回调未全部注册。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)：音频服务进程死亡。</li>          </ul> |

### OH_AudioAccessoryInputStreamManager_GetWritableSize()

```c
OH_AudioCommon_Result OH_AudioAccessoryInputStreamManager_GetWritableSize(OH_AudioAccessoryInputStream *stream, uint32_t *writableSize)
```

**描述**

获取音频配件输入流缓冲区的可写大小。调用方可使用此函数在调用[OH_AudioAccessoryInputStreamManager_Write](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessoryinputstreammanager_write)之前探测当前缓冲区可用空间。返回的可写大小仅反映当前状态，函数返回后可能立即发生变化。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md) *stream | [in] 输入流句柄指针。 |
| uint32_t *writableSize | [out] 输出参数，返回可写入的字节数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul>          <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)：函数执行成功。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)：参数为空。</li>          <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)：流已释放。</li>          </ul> |


