# native_audiocapturer.h

## 概述

OH_AudioCapturer提供音频录制流功能，目前主要用于录制PCM（Pulse Code Modulation）音频数据。在录制过程中， 需要持续从系统读取已录到的音频数据，适用于需要在录制后对音频数据进行后处理、 对录制过程有更灵活控制要求的场景，如专业媒体录制、语音识别、语音消息、语音通话等。 不同录制场景需通过[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)配置合适的录音源类型，以便让系统匹配合适的音效、设备与焦点策略。 <br>使用OH_AudioCapturer实现音频录制功能时，需先设置音频核心参数（采样率、声道、编码类型、采样格式、使用场景等） 并设置数据读取回调，通过 [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建录制流实例，随后调用[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)开始录制。 录制过程中可通过 [OH_AudioCapturer_Pause](capi-native-audiocapturer-h.md#oh_audiocapturer_pause)控制录制暂停、[OH_AudioCapturer_Stop](capi-native-audiocapturer-h.md#oh_audiocapturer_stop)控制录制停止， 退出录制时通过[OH_AudioCapturer_Release](capi-native-audiocapturer-h.md#oh_audiocapturer_release)释放资源。 OH_AudioCapturer内具备状态机，仅在特定状态下调用相应方法才能正常工作。 <br>使用麦克风录制时，需申请ohos.permission.MICROPHONE权限，并且录制流只能在前台启动，启动后可退至后台保持运行。 <br>由于系统对音频流数量有限制，不再使用时应及时调用[OH_AudioCapturer_Release](capi-native-audiocapturer-h.md#oh_audiocapturer_release)释放资源， 避免后续创建音频流失败。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer)](#oh_audiocapturer_release) | - | 释放音频录制流。 <br>输入的OH_AudioCapturer指针指向的内存也会释放，不能再被使用，建议开发者在释放后主动将指针置空。 |
| [OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer)](#oh_audiocapturer_start) | - | 启动音频录制流。 <br>音频流开始运行后，注册的数据回调会被周期性的触发，让调用者读取已录到的音频数据。 |
| [OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer)](#oh_audiocapturer_pause) | - | 暂停音频录制流。 <br>在暂停音频后，后续需要恢复录音的场景，建议使用此接口。但在录音数据处理方面，此接口与OH_AudioCapturer_Stop无差异。 |
| [OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer)](#oh_audiocapturer_stop) | - | 停止音频录制流。 <br>在需要彻底结束录音的场景，建议使用此接口。但在录音数据处理方面，此接口与OH_AudioCapturer_Pause无差异。 |
| [OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer)](#oh_audiocapturer_flush) | - | 清空音频录制流缓冲区的音频数据。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetCurrentState(OH_AudioCapturer* capturer, OH_AudioStream_State* state)](#oh_audiocapturer_getcurrentstate) | - | 获取当前音频录制流状态。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetLatencyMode(OH_AudioCapturer* capturer, OH_AudioStream_LatencyMode* latencyMode)](#oh_audiocapturer_getlatencymode) | - | 获取当前音频录制流时延模式。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetStreamId(OH_AudioCapturer* capturer, uint32_t* streamId)](#oh_audiocapturer_getstreamid) | - | 获取当前音频录制流ID。 <br>音频系统会在创建时为每一个音频流分配全局唯一的音频流ID，此ID可以作为音频流的标识。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetSamplingRate(OH_AudioCapturer* capturer, int32_t* rate)](#oh_audiocapturer_getsamplingrate) | - | 获取当前音频录制流采样率，单位为Hz。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetChannelCount(OH_AudioCapturer* capturer, int32_t* channelCount)](#oh_audiocapturer_getchannelcount) | - | 获取当前音频录制流声道数。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetSampleFormat(OH_AudioCapturer* capturer, OH_AudioStream_SampleFormat* sampleFormat)](#oh_audiocapturer_getsampleformat) | - | 获取当前音频录制流采样格式。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetEncodingType(OH_AudioCapturer* capturer, OH_AudioStream_EncodingType* encodingType)](#oh_audiocapturer_getencodingtype) | - | 获取当前音频录制流编码类型。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetCapturerInfo(OH_AudioCapturer* capturer, OH_AudioStream_SourceType* sourceType)](#oh_audiocapturer_getcapturerinfo) | - | 获取当前音频录制流的使用场景类型。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetFrameSizeInCallback(OH_AudioCapturer* capturer, int32_t* frameSize)](#oh_audiocapturer_getframesizeincallback) | - | 获取当前音频录制流每次数据回调可读取的音频数据帧长，单位为采样点数。 <br>当音频录制流运行模式发生变化时，如从低时延模式切换到普通模式，此帧长可能发生变化。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetTimestamp(OH_AudioCapturer* capturer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)](#oh_audiocapturer_gettimestamp) | - | 获取音频录制流时间戳和当前数据帧位置信息。 <br>该接口可以获取到音频通道实际录制位置（framePosition）以及录制到该位置时的时间戳（timestamp），时间戳单位为ns。 主要用于录像音画同步场景。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetFramesRead(OH_AudioCapturer* capturer, int64_t* frames)](#oh_audiocapturer_getframesread) | - | 查询自创建音频录制流以来已读取的帧数，单位为采样点数。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetOverflowCount(OH_AudioCapturer* capturer, uint32_t* count)](#oh_audiocapturer_getoverflowcount) | - | 获取当前音频录制流过载次数。 <br>在录制过程中，如果调用者没有及时通过数据回调读取音频数据，系统内部缓存被录音数据填满，就会触发过载， 新录到的数据会覆盖缓存内的历史数据，导致数据丢失。 <br>过载次数是按照音频系统的数据处理周期计算的，而不是以应用设置的回调长度作为周期。 |
| [typedef void (\*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiocapturer_onreaddatacallback) | OH_AudioCapturer_OnReadDataCallback | 音频录制流读取音频数据回调函数的原型定义。 <br>为了消除麦克风硬件设计带来的上电杂音，通常会对录音启动后的前100ms数据进行静音。 |
| [typedef void (\*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray)](#oh_audiocapturer_ondevicechangecallback) | OH_AudioCapturer_OnDeviceChangeCallback | 音频录制流设备变化事件回调函数的原型定义。 |
| [typedef void (\*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)](#oh_audiocapturer_oninterruptcallback) | OH_AudioCapturer_OnInterruptCallback | 音频录制流中断事件回调函数的原型定义。 |
| [typedef void (\*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)](#oh_audiocapturer_onerrorcallback) | OH_AudioCapturer_OnErrorCallback | 音频录制流错误事件回调函数的原型定义。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetFastStatus(OH_AudioCapturer* capturer, OH_AudioStream_FastStatus* status)](#oh_audiocapturer_getfaststatus) | - | 获取音频录制过程中的运行状态，是否在低时延运行状态下工作。 |
| [typedef void (\*OH_AudioCapturer_OnFastStatusChange)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status)](#oh_audiocapturer_onfaststatuschange) | OH_AudioCapturer_OnFastStatusChange | 音频录制流低时延状态变化事件回调函数的原型定义。 |
| [typedef void (\*OH_AudioCapturer_OnPlaybackCaptureStartCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state)](#oh_audiocapturer_onplaybackcapturestartcallback) | OH_AudioCapturer_OnPlaybackCaptureStartCallback | 内录（录制系统内部音频）启动结果回调函数的原型定义。 <br>该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。 |
| [OH_AudioStream_Result OH_AudioCapturer_RequestPlaybackCaptureStart(OH_AudioCapturer* capturer, OH_AudioCapturer_OnPlaybackCaptureStartCallback callback, void* userData)](#oh_audiocapturer_requestplaybackcapturestart) | - |  |
| [OH_AudioStream_Result OH_AudioCapturer_SetMuteHint(OH_AudioCapturer* capturer, bool mute)](#oh_audiocapturer_setmutehint) | - | 将当前录制流的自身静音状态传递给音频系统。 <br>该接口用于在语音通话和语音会议场景，应用可向音频系统告知其进入录音静音状态（应用内实现录音静音）， 系统不会对录制流进行静音处理，而是会基于设置的状态调整数据处理策略以降低功耗。当前仅在部分PC/2in1设备上具备此效果。 <br>该接口仅在录制流处于运行态时允许调用，否则返回状态错误。 <br>应用同时设置音频流级静音提示接口（本接口） 和会话级静音提示接口OH_AudioSessionManager_SetCaptureMuteHint时，本接口优先级更高。 |
| [OH_AudioStream_Result OH_AudioCapturer_SetIndependentAudioSessionStrategy(OH_AudioCapturer* capturer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)](#oh_audiocapturer_setindependentaudiosessionstrategy) | - | 设置音频录制流的独立音频会话策略和行为参数，这些参数主要用于扩展音频流的默认并发策略。 <br>建议在音频流处于运行状态前设置。当在音频流运行时调用此接口， 只会在下次调用接口[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)启动音频流后参数才会生效。 |
| [typedef void (\*OH_AudioCapturer_SensitiveRecordPermitCallback)(OH_AudioCapturer* capturer, void* userData, bool isPermitted)](#oh_audiocapturer_sensitiverecordpermitcallback) | OH_AudioCapturer_SensitiveRecordPermitCallback | 蜂窝通话录音场景下，风险提示语播放结束回调函数的原型定义。 <br>应用必须等待回调返回许可结果，且isPermitted为true时，方可开始蜂窝通话录音。 |
| [OH_AudioStream_Result OH_AudioCapturer_SetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode noiseReductionMode)](#oh_audiocapturer_setnoisereductionmode) | - | 设置当前录制流的降噪模式。 建议先调用[OH_AudioCapturer_GetSupportedNoiseReductionModes](capi-native-audiocapturer-h.md#oh_audiocapturer_getsupportednoisereductionmodes)获取当前录制流支持的降噪模式后， 再通过本接口进行设置。 <br>当前仅支持使用[AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)创建的录制流进行降噪模式设置，其他录制流默认仅支持 [AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。降噪效果受设备平台、音频设备和录音并发情况影响。 存在多个录制流同时运行时，设置的降噪模式可能不生效。 <br>该接口仅可在录制流创建后未开始录音，或停止录音后调用； 录制流处于运行态或已释放时调用将返回[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result)。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionMode)](#oh_audiocapturer_getnoisereductionmode) | - | 获取当前录制流的降噪模式。返回结果仅反映当前录制流的降噪模式。 默认值为[AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。 |
| [OH_AudioStream_Result OH_AudioCapturer_GetSupportedNoiseReductionModes(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionModeArray, uint32_t inModeArraySize, uint32_t *outModeArraySize)](#oh_audiocapturer_getsupportednoisereductionmodes) | - | 获取当前设备平台支持的录音降噪模式。 当前仅使用[AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)创建的录制流会根据设备平台查询支持的降噪模式， 其他录制流默认仅返回 [AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。返回结果仅考虑音频格式和设备平台，不考虑当前输入设备和录音并发情况。 <br>当支持的模式数量大于入参inModeArraySize时，仅向noiseReductionModeArray写入前inModeArraySize个模式， outModeArraySize等于inModeArraySize。 建议应用预留较大的数组长度，例如20，以兼容后续新增模式。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize) | 音频录制流读取音频数据回调函数的原型定义。 <br>为了消除麦克风硬件设计带来的上电杂音，通常会对录音启动后的前100ms数据进行静音。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray) | 音频录制流设备变化事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint) | 音频录制流中断事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error) | 音频录制流错误事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_OnFastStatusChange)( OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status ) | 音频录制流低时延状态变化事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_OnPlaybackCaptureStartCallback)( OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state) | 内录（录制系统内部音频）启动结果回调函数的原型定义。 <br>该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。<br>**起始版本：** 23<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioCapturer_SensitiveRecordPermitCallback)( OH_AudioCapturer* capturer, void* userData, bool isPermitted) | 蜂窝通话录音场景下，风险提示语播放结束回调函数的原型定义。 <br>应用必须等待回调返回许可结果，且isPermitted为true时，方可开始蜂窝通话录音。<br>**起始版本：** 26.0.0<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 函数说明

### OH_AudioCapturer_Release()

```c
OH_AudioStream_Result OH_AudioCapturer_Release(OH_AudioCapturer* capturer)
```

**描述：**

释放音频录制流。 <br>输入的OH_AudioCapturer指针指向的内存也会释放，不能再被使用，建议开发者在释放后主动将指针置空。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**需要权限：** ohos.permission.MICROPHONE

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_Start()

```c
OH_AudioStream_Result OH_AudioCapturer_Start(OH_AudioCapturer* capturer)
```

**描述：**

启动音频录制流。 <br>音频流开始运行后，注册的数据回调会被周期性的触发，让调用者读取已录到的音频数据。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**需要权限：** ohos.permission.MICROPHONE

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_Pause()

```c
OH_AudioStream_Result OH_AudioCapturer_Pause(OH_AudioCapturer* capturer)
```

**描述：**

暂停音频录制流。 <br>在暂停音频后，后续需要恢复录音的场景，建议使用此接口。但在录音数据处理方面，此接口与OH_AudioCapturer_Stop无差异。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**需要权限：** ohos.permission.MICROPHONE

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_Stop()

```c
OH_AudioStream_Result OH_AudioCapturer_Stop(OH_AudioCapturer* capturer)
```

**描述：**

停止音频录制流。 <br>在需要彻底结束录音的场景，建议使用此接口。但在录音数据处理方面，此接口与OH_AudioCapturer_Pause无差异。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**需要权限：** ohos.permission.MICROPHONE

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_Flush()

```c
OH_AudioStream_Result OH_AudioCapturer_Flush(OH_AudioCapturer* capturer)
```

**描述：**

清空音频录制流缓冲区的音频数据。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_GetCurrentState()

```c
OH_AudioStream_Result OH_AudioCapturer_GetCurrentState(OH_AudioCapturer* capturer, OH_AudioStream_State* state)
```

**描述：**

获取当前音频录制流状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_State](capi-native-audiostream-base-h.md#oh_audiostream_state)* state | [out] 用于接收获取的音频录制流状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetLatencyMode()

```c
OH_AudioStream_Result OH_AudioCapturer_GetLatencyMode(OH_AudioCapturer* capturer, OH_AudioStream_LatencyMode* latencyMode)
```

**描述：**

获取当前音频录制流时延模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode)* latencyMode | [out] 用于接收获取的音频录制流时延模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetStreamId()

```c
OH_AudioStream_Result OH_AudioCapturer_GetStreamId(OH_AudioCapturer* capturer, uint32_t* streamId)
```

**描述：**

获取当前音频录制流ID。 <br>音频系统会在创建时为每一个音频流分配全局唯一的音频流ID，此ID可以作为音频流的标识。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| uint32_t* streamId | [out] 用于接收获取的音频流ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetSamplingRate()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSamplingRate(OH_AudioCapturer* capturer, int32_t* rate)
```

**描述：**

获取当前音频录制流采样率，单位为Hz。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| int32_t* rate | [out] 用于接收获取的音频录制流采样率，单位为Hz。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetChannelCount()

```c
OH_AudioStream_Result OH_AudioCapturer_GetChannelCount(OH_AudioCapturer* capturer, int32_t* channelCount)
```

**描述：**

获取当前音频录制流声道数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| int32_t* channelCount | [out] 用于接收获取的音频录制流声道数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetSampleFormat()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSampleFormat(OH_AudioCapturer* capturer, OH_AudioStream_SampleFormat* sampleFormat)
```

**描述：**

获取当前音频录制流采样格式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat)* sampleFormat | [out] 用于接收获取的音频录制流采样格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetEncodingType()

```c
OH_AudioStream_Result OH_AudioCapturer_GetEncodingType(OH_AudioCapturer* capturer, OH_AudioStream_EncodingType* encodingType)
```

**描述：**

获取当前音频录制流编码类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype)* encodingType | [out] 用于接收获取的音频录制流编码类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetCapturerInfo()

```c
OH_AudioStream_Result OH_AudioCapturer_GetCapturerInfo(OH_AudioCapturer* capturer, OH_AudioStream_SourceType* sourceType)
```

**描述：**

获取当前音频录制流的使用场景类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)* sourceType | [out] 用于接收获取的音频录制流使用场景类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFrameSizeInCallback(OH_AudioCapturer* capturer, int32_t* frameSize)
```

**描述：**

获取当前音频录制流每次数据回调可读取的音频数据帧长，单位为采样点数。 <br>当音频录制流运行模式发生变化时，如从低时延模式切换到普通模式，此帧长可能发生变化。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| int32_t* frameSize | [out] 用于接收获取的音频数据帧长，单位为采样点数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_GetTimestamp()

```c
OH_AudioStream_Result OH_AudioCapturer_GetTimestamp(OH_AudioCapturer* capturer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)
```

**描述：**

获取音频录制流时间戳和当前数据帧位置信息。 <br>该接口可以获取到音频通道实际录制位置（framePosition）以及录制到该位置时的时间戳（timestamp），时间戳单位为ns。 主要用于录像音画同步场景。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| clockid_t clockId | [in] 时钟标识符，使用CLOCK_MONOTONIC。 |
| int64_t* framePosition | [out] 用于接收获取的最近输入音频帧位置。 |
| int64_t* timestamp | [out] 用于接收获取的最近输入音频帧时间戳，与位置对应，单位为ns。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数capturer为空指针；2. 参数clockId无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_GetFramesRead()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFramesRead(OH_AudioCapturer* capturer, int64_t* frames)
```

**描述：**

查询自创建音频录制流以来已读取的帧数，单位为采样点数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| int64_t* frames | [out] 用于接收获取的已读取帧数，单位为采样点数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_GetOverflowCount()

```c
OH_AudioStream_Result OH_AudioCapturer_GetOverflowCount(OH_AudioCapturer* capturer, uint32_t* count)
```

**描述：**

获取当前音频录制流过载次数。 <br>在录制过程中，如果调用者没有及时通过数据回调读取音频数据，系统内部缓存被录音数据填满，就会触发过载， 新录到的数据会覆盖缓存内的历史数据，导致数据丢失。 <br>过载次数是按照音频系统的数据处理周期计算的，而不是以应用设置的回调长度作为周期。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| uint32_t* count | [out] 用于接收获取的音频录制流过载次数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> </ul> |

### OH_AudioCapturer_OnReadDataCallback()

```c
typedef void (*OH_AudioCapturer_OnReadDataCallback)(OH_AudioCapturer* capturer, void* userData, void* audioData, int32_t audioDataSize)
```

**描述：**

音频录制流读取音频数据回调函数的原型定义。 <br>为了消除麦克风硬件设计带来的上电杂音，通常会对录音启动后的前100ms数据进行静音。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| void* audioData | 指向让应用读取的录制数据。 |
| int32_t audioDataSize | 应用可读取的录制数据的数据长度，单位为Byte。 |

**参考：**

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnReadData


### OH_AudioCapturer_OnDeviceChangeCallback()

```c
typedef void (*OH_AudioCapturer_OnDeviceChangeCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioDeviceDescriptorArray* deviceArray)
```

**描述：**

音频录制流设备变化事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md)* deviceArray | 变化后的音频设备描述符数组。 |

**参考：**

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnStreamEvent


### OH_AudioCapturer_OnInterruptCallback()

```c
typedef void (*OH_AudioCapturer_OnInterruptCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)
```

**描述：**

音频录制流中断事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | 音频流中断类型。 |
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | 音频流中断提示类型。 |

**参考：**

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnInterruptEvent


### OH_AudioCapturer_OnErrorCallback()

```c
typedef void (*OH_AudioCapturer_OnErrorCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_Result error)
```

**描述：**

音频录制流错误事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | 音频流录制错误结果。 |

**参考：**

OH_AudioCapturer_Callbacks_Struct.OH_AudioCapturer_OnError


### OH_AudioCapturer_GetFastStatus()

```c
OH_AudioStream_Result OH_AudioCapturer_GetFastStatus(OH_AudioCapturer* capturer, OH_AudioStream_FastStatus* status)
```

**描述：**

获取音频录制过程中的运行状态，是否在低时延运行状态下工作。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus)* status | [out] 用于接收获取的低时延运行状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常，仅在释放状态之前可用。</li> </ul> |

### OH_AudioCapturer_OnFastStatusChange()

```c
typedef void (*OH_AudioCapturer_OnFastStatusChange)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_FastStatus status)
```

**描述：**

音频录制流低时延状态变化事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus) status | 当前低时延运行状态。 |

### OH_AudioCapturer_OnPlaybackCaptureStartCallback()

```c
typedef void (*OH_AudioCapturer_OnPlaybackCaptureStartCallback)(OH_AudioCapturer* capturer, void* userData, OH_AudioStream_PlaybackCaptureStartState state)
```

**描述：**

内录（录制系统内部音频）启动结果回调函数的原型定义。 <br>该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者通过[OH_AudioCapturer_RequestPlaybackCaptureStart](capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart)传入的userData数据。 |
| [OH_AudioStream_PlaybackCaptureStartState](capi-native-audiostream-base-h.md#oh_audiostream_playbackcapturestartstate) state | 表示内录请求是否成功的状态。 |

### OH_AudioCapturer_RequestPlaybackCaptureStart()

```c
OH_AudioStream_Result OH_AudioCapturer_RequestPlaybackCaptureStart(OH_AudioCapturer* capturer, OH_AudioCapturer_OnPlaybackCaptureStartCallback callback, void* userData)
```

**描述：**

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [OH_AudioCapturer_OnPlaybackCaptureStartCallback](capi-native-audiocapturer-h.md#oh_audiocapturer_onplaybackcapturestartcallback) callback | [in] 用于接收启动请求最终结果的回调函数。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) capturer或callback是无效的。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 如果流已经在运行中或者已释放则是非法状态。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 系统内部错误，比如音频服务错误。</li> </ul> |

### OH_AudioCapturer_SetMuteHint()

```c
OH_AudioStream_Result OH_AudioCapturer_SetMuteHint(OH_AudioCapturer* capturer, bool mute)
```

**描述：**

将当前录制流的自身静音状态传递给音频系统。 <br>该接口用于在语音通话和语音会议场景，应用可向音频系统告知其进入录音静音状态（应用内实现录音静音）， 系统不会对录制流进行静音处理，而是会基于设置的状态调整数据处理策略以降低功耗。当前仅在部分PC/2in1设备上具备此效果。 <br>该接口仅在录制流处于运行态时允许调用，否则返回状态错误。 <br>应用同时设置音频流级静音提示接口（本接口） 和会话级静音提示接口OH_AudioSessionManager_SetCaptureMuteHint时，本接口优先级更高。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| bool mute | [in] 应用内录音静音状态。true表示该录制流为静音状态，false表示该录制流为非静音状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 操作状态异常，录制流未处于运行状态。</li> </ul> |

### OH_AudioCapturer_SetIndependentAudioSessionStrategy()

```c
OH_AudioStream_Result OH_AudioCapturer_SetIndependentAudioSessionStrategy(OH_AudioCapturer* capturer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)
```

**描述：**

设置音频录制流的独立音频会话策略和行为参数，这些参数主要用于扩展音频流的默认并发策略。 <br>建议在音频流处于运行状态前设置。当在音频流运行时调用此接口， 只会在下次调用接口[OH_AudioCapturer_Start](capi-native-audiocapturer-h.md#oh_audiocapturer_start)启动音频流后参数才会生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| [const OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md)* strategy | [in] 用于设置独立的音频会话策略。 |
| uint32_t behavior | [in] 音频会话行为标志，可以是单个标志，也可以是多个标志的按位OR组合。 当前支持的音频会话行为详见[OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数为空指针或超出范围。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioCapturer_SensitiveRecordPermitCallback()

```c
typedef void (*OH_AudioCapturer_SensitiveRecordPermitCallback)(OH_AudioCapturer* capturer, void* userData, bool isPermitted)
```

**描述：**

蜂窝通话录音场景下，风险提示语播放结束回调函数的原型定义。 <br>应用必须等待回调返回许可结果，且isPermitted为true时，方可开始蜂窝通话录音。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | 指向触发回调的音频录制流实例。 |
| void* userData | 指向开发者通过[OH_AudioStreamBuilder_SetSensitiveRecordPermitCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setsensitiverecordpermitcallback)传入的userData数据。 |
| bool isPermitted | 表示风险提示语是否播放结束。若结果为true，表示可以开始录音；若为false，表示录音未被允许。 |

### OH_AudioCapturer_SetNoiseReductionMode()

```c
OH_AudioStream_Result OH_AudioCapturer_SetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode noiseReductionMode)
```

**描述：**

设置当前录制流的降噪模式。 建议先调用[OH_AudioCapturer_GetSupportedNoiseReductionModes](capi-native-audiocapturer-h.md#oh_audiocapturer_getsupportednoisereductionmodes)获取当前录制流支持的降噪模式后， 再通过本接口进行设置。 <br>当前仅支持使用[AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)创建的录制流进行降噪模式设置，其他录制流默认仅支持 [AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。降噪效果受设备平台、音频设备和录音并发情况影响。 存在多个录制流同时运行时，设置的降噪模式可能不生效。 <br>该接口仅可在录制流创建后未开始录音，或停止录音后调用； 录制流处于运行态或已释放时调用将返回[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result)。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| OH_AudioNoiseReductionMode noiseReductionMode | [in] 要设置的降噪模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针，或参数noiseReductionMode无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 录制流处于运行态或已释放。</li> <li>[AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY](capi-native-audiostream-base-h.md#oh_audiostream_result) 设置的降噪模式不支持。</li> <li>[AUDIOSTREAM_ERROR_SERVICE_DIED](capi-native-audiostream-base-h.md#oh_audiostream_result) 音频服务进程异常结束。</li> </ul> |

### OH_AudioCapturer_GetNoiseReductionMode()

```c
OH_AudioStream_Result OH_AudioCapturer_GetNoiseReductionMode(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionMode)
```

**描述：**

获取当前录制流的降噪模式。返回结果仅反映当前录制流的降噪模式。 默认值为[AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| OH_AudioNoiseReductionMode* noiseReductionMode | [out] 用于接收获取的录制流降噪模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数capturer为空指针，或参数noiseReductionMode为空指针。</li> </ul> |

### OH_AudioCapturer_GetSupportedNoiseReductionModes()

```c
OH_AudioStream_Result OH_AudioCapturer_GetSupportedNoiseReductionModes(OH_AudioCapturer* capturer, OH_AudioNoiseReductionMode* noiseReductionModeArray, uint32_t inModeArraySize, uint32_t *outModeArraySize)
```

**描述：**

获取当前设备平台支持的录音降噪模式。 当前仅使用[AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)创建的录制流会根据设备平台查询支持的降噪模式， 其他录制流默认仅返回 [AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。返回结果仅考虑音频格式和设备平台，不考虑当前输入设备和录音并发情况。 <br>当支持的模式数量大于入参inModeArraySize时，仅向noiseReductionModeArray写入前inModeArraySize个模式， outModeArraySize等于inModeArraySize。 建议应用预留较大的数组长度，例如20，以兼容后续新增模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md)* capturer | [in] 指向[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频流实例。 |
| OH_AudioNoiseReductionMode* noiseReductionModeArray | [out] 由应用分配的数组，用于接收支持的录音降噪模式， 默认支持[AUDIO_NOISE_REDUCTION_MODE_FIDELITY](capi-native-audio-common-h.md#oh_audionoisereductionmode)。 |
| uint32_t inModeArraySize | [in] noiseReductionModeArray数组的容量。 |
| uint32_t *outModeArraySize | [out] 用于接收实际获取的降噪模式数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result)参数capturer为空指针，或参数noiseReductionModeArray为空指针，或参数outModeArraySize为空指针。</li> <li>[AUDIOSTREAM_ERROR_SERVICE_DIED](capi-native-audiostream-base-h.md#oh_audiostream_result) 音频服务进程死亡。</li> </ul> |


