# native_audiorenderer.h

## 概述

OH_AudioRenderer提供音频播放流功能，目前主要用于播放PCM（Pulse Code Modulation）音频数据。在播放过程中， 需要持续向系统传递待播放的音频数据，适用于需要在播放前对音频数据进行预处理、 对播放过程有更灵活控制要求的场景，如专业媒体播放、游戏、语音通话等。 不同播放场景需通过[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)配置合适的播放流类型，以便让系统匹配合适的音效、音量、设备与焦点策略。 <br>使用OH_AudioRenderer实现音频播放功能时，需先设置音频核心参数（采样率、声道、编码类型、采样格式、使用场景等） 并设置数据写入回调，通过 [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建播放流实例，随后调用[OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start)开始播放。 播放过程中可通过 [OH_AudioRenderer_Pause](capi-native-audiorenderer-h.md#oh_audiorenderer_pause)控制播放暂停、[OH_AudioRenderer_Stop](capi-native-audiorenderer-h.md#oh_audiorenderer_stop)控制播放停止， 退出播放时通过[OH_AudioRenderer_Release](capi-native-audiorenderer-h.md#oh_audiorenderer_release)释放资源。 OH_AudioRenderer内具备状态机，仅在特定状态下调用相应方法才能正常工作。 <br>由于系统对音频流数量有限制，不再使用时应及时调用[OH_AudioRenderer_Release](capi-native-audiorenderer-h.md#oh_audiorenderer_release)释放资源， 避免后续创建音频流失败。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)](#oh_audiorenderer_release) | - | 释放音频播放流。 <br>输入的OH_AudioRenderer指针指向的内存也会释放，不能再被使用，建议开发者在释放后主动将指针置空。 |
| [OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)](#oh_audiorenderer_start) | - | 启动音频播放流。 <br>音频流开始运行后，注册的数据回调会被周期性的触发，让调用者写入要播放的音频数据。 |
| [OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)](#oh_audiorenderer_pause) | - | 暂停音频播放流。 <br>对比OH_AudioRenderer_Stop接口，暂停时已写入系统的音频数据缓存不会被播放完，而是立即停止输出。 |
| [OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)](#oh_audiorenderer_stop) | - | 停止音频播放流。 <br>对比OH_AudioRenderer_Pause接口，通常情况下，已写入系统的音频数据缓存会全部播放完，再停止输出。 但如果音频播放流处于低功耗运行模式，由于系统缓存数据很多，调用本接口仍会立即停止输出。 |
| [OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)](#oh_audiorenderer_flush) | - | 清空音频播放流缓冲区的音频数据。 <br>本接口主要用于音频播放器调节播放进度的场景，可以将已写入的数据清空，避免影响后续播放。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)](#oh_audiorenderer_getcurrentstate) | - | 获取当前音频播放流状态。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)](#oh_audiorenderer_getsamplingrate) | - | 获取当前音频播放流采样率，单位为Hz。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)](#oh_audiorenderer_getstreamid) | - | 获取当前音频播放流ID。 <br>音频系统会在创建时为每一个音频流分配全局唯一的音频流ID，此ID可以作为音频流的标识。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)](#oh_audiorenderer_getchannelcount) | - | 获取当前音频播放流声道数。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)](#oh_audiorenderer_getsampleformat) | - | 获取当前音频播放流采样格式。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)](#oh_audiorenderer_getlatencymode) | - | 获取当前音频播放流时延模式。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)](#oh_audiorenderer_getrendererinfo) | - | 获取当前音频播放流的使用场景类型。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)](#oh_audiorenderer_getencodingtype) | - | 获取当前音频播放流编码类型。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)](#oh_audiorenderer_getframeswritten) | - | 获取自创建音频播放流以来已写入的帧数。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_gettimestamp) | - | 获取音频播放流时间戳和位置信息。 <br>该接口可以获取到音频通道实际播放位置（framePosition）以及播放到该位置时的时间戳（timestamp）。 <br>播放位置单位为采样数（samples），时间戳单位为ns。 <br>当设备切换或暂停恢复时，由于播放通路本身需要一段时间恢复， 调用该接口获取的播放位置和时间戳会短暂地保持在切换或暂停前的状态。 <br>该接口通常用来实现音画同步，调用间隔建议不小于200ms，推荐频率为每秒一次。在能保证音画同步效果的情况下， 不需要频繁地查询时间戳，避免出现功耗问题。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)](#oh_audiorenderer_getframesizeincallback) | - | 获取当前音频播放流每次数据回调请求写入的音频数据帧长，单位为采样点数。 <br>当音频播放流运行模式发生变化时，如从低时延模式切换到普通模式，此帧长可能发生变化。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)](#oh_audiorenderer_getspeed) | - | 获取音频播放速率。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)](#oh_audiorenderer_setspeed) | - | 设置音频播放速率。 <br>默认播放速率为1.0。播放速率改变会影响音频数据的消耗速度，如设置2倍速时，数据消耗速度也会变为2倍， 调用者需确保写入足够的音频数据。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)](#oh_audiorenderer_setvolume) | - | 设置当前音频播放流音量值。 <br>此设置只会影响当前音频播放流，并且不会影响系统全局音量。默认音量为1.0，因此只能通过此接口降低音量。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)](#oh_audiorenderer_setvolumewithramp) | - | 在指定时间范围内使用渐变更改音量。 <br>此设置只会影响当前音频播放流，并且不会影响系统全局音量。默认音量为1.0，因此只能通过此接口降低音量。 <br>设置后，音频播放流会根据设置的时间，从当前音量逐渐变化到目标音量，通常用于实现播放淡入和淡出效果。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)](#oh_audiorenderer_getvolume) | - | 获取当前音频播放流音量值。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)](#oh_audiorenderer_setmarkposition) | - | 设置标记位置和对应回调函数。 <br>当播放的音频帧数达到标记位置时，会触发此回调函数。 <br>重复设置会覆盖已设置的标记位置和回调函数。 |
| [OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)](#oh_audiorenderer_cancelmark) | - | 取消由[OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition)设置的标记和回调函数。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)](#oh_audiorenderer_getunderflowcount) | - | 获取当前音频播放流欠载次数。 <br>在播放过程中，如果调用者没有及时通过数据回调写入音频数据，当系统将内部缓存全部输出后，就会触发欠载， 输出静音数据。 <br>欠载次数是按照音频系统的数据处理周期计算的，而不是以应用设置的回调长度作为周期。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)](#oh_audiorenderer_getchannellayout) | - | 获取当前音频播放流声道布局。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)](#oh_audiorenderer_geteffectmode) | - | 获取当前音频播放流音效模式。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)](#oh_audiorenderer_seteffectmode) | - | 设置当前音频播放流音效模式。 <br>对于媒体类音频，系统会根据[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)为音频流添加音效，以达到更好的用户体验。 但如果开发者不想使用系统默认音效，可通过此接口关闭。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)](#oh_audiorenderer_getrendererprivacy) | - | 获取当前音频播放流的隐私类型。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)](#oh_audiorenderer_setsilentmodeandmixwithothers) | - | 设置音频播放流的静音并发播放模式。 <br>设置为true表示打开静音并发播放模式，系统将让此音频流静音播放，其他音频流可以保持正常播放不被打断。设置为false， 将关闭静音并发播放，音频流可根据系统焦点策略抢占焦点。 <br>此接口适用于视频静音播放场景，避免打断正在播放的音乐。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)](#oh_audiorenderer_getsilentmodeandmixwithothers) | - | 获取当前音频播放流是否开启静音并发播放模式。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)](#oh_audiorenderer_setdefaultoutputdevice) | - | 设置默认本机内置发声设备。 <br>本接口仅适用于音频流类型[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)为语音消息、VoIP语音通话或者VoIP视频通话的场景， 可选的设备类型为听筒、扬声器和系统默认设备。 <br>本接口允许在AudioRenderer创建以后的任何时间被调用，系统会记录应用设置的默认本机内置发声设备。在应用启动播放时， 若有外接设备如蓝牙耳机/有线耳机接入，系统优先从外接设备发声； 否则系统遵循应用设置的默认本机内置发声设备发声。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)](#oh_audiorenderer_getaudiotimestampinfo) | - | 获取音频播放流时间戳和位置信息。 <br>相比OH_AudioRenderer_GetTimestamp适配了倍速接口。 <br>通常用于进行音画同步对齐，播放位置单位为采样数（samples），时间戳单位为ns。 <br>当设备切换或暂停恢复时，由于播放通路本身需要一段时间恢复， 调用该接口获取的播放位置和时间戳会短暂地保持在切换或暂停前的状态。 <br>该接口通常用来实现音画同步，调用间隔建议不小于200ms，推荐频率为每秒一次。在能保证音画同步效果的情况下， 不需要频繁地查询时间戳，避免出现功耗问题。 |
| [typedef void (\*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)](#oh_audiorenderer_oninterruptcallback) | OH_AudioRenderer_OnInterruptCallback | 音频播放流中断事件回调函数的原型定义。 |
| [typedef void (\*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)](#oh_audiorenderer_onerrorcallback) | OH_AudioRenderer_OnErrorCallback | 音频播放流错误事件回调函数的原型定义。 <br>系统内部故障时触发，如音频服务异常退出，非应用调用导致。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)](#oh_audiorenderer_getfaststatus) | - | 获取音频播放过程中的运行状态，是否在低时延运行状态下工作。 |
| [typedef void (\*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status)](#oh_audiorenderer_onfaststatuschange) | OH_AudioRenderer_OnFastStatusChange | 音频播放流低时延状态变化事件回调函数的原型定义。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)](#oh_audiorenderer_setloudnessgain) | - | 设置音频播放的响度值。 <br>默认的响度值是0.0dB。音频流播放类型必须是音乐[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC， 电影或视频[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage). AUDIOSTREAM_USAGE_MOVIE， 有声读物（包括听书、相声、评书）、听新闻、 播客等[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK。 音频流的时延模式必须是普通时延[OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL。 本接口不支持设置通过高清通路播放的音频流响度。 <br>由于音频框架与硬件之间存在缓冲区，响度调节实际生效存在延迟，时长取决于缓冲区长度。 <br>建议在不同音频开始播放前预先设置响度，以实现最佳均衡效果。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)](#oh_audiorenderer_getloudnessgain) | - | 获取音频播放流的响度值。 |
| [typedef int32_t (\*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallbackadvanced) | OH_AudioRenderer_OnWriteDataCallbackAdvanced | 音频播放流写入音频数据回调函数的原型定义。 <br>不同于OH_AudioRenderer_OnWriteDataCallback，此函数允许应用填充[0, audioDataSize]长度的数据。 <br>其中audioDataSize为回调buffer的长度。调用方通过返回值告知系统写入的数据长度。 <br>如果返回0，回调线程将会sleep一段时间。 <br>否则，系统可能会立刻进行下一次回调。 |
| [OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)](#oh_audiorenderer_getlatency) | - | 获取当前音频路由的估算时延（单位：ms）。无线连接的音频设备，时延估算可能存在误差，结果仅供参考。 <br>由于时延未计入实时缓冲区，建议仅在音频播放开始时获取，避免频繁调用，否则可能因路由切换而阻塞该接口调用。 <br>当音频数据输出到硬件后，建议使用[OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)进行音视频同步。 |
| [OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)](#oh_audiorenderer_setindependentaudiosessionstrategy) | - | 设置音频播放流的独立音频会话策略和行为参数，这些参数主要用于扩展音频流的默认并发策略。 <br>建议在音频流处于运行状态前设置。当在音频流运行时调用此接口， 只会在下次调用接口[OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start)启动音频流后参数才会生效。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint) | 音频播放流中断事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error) | 音频播放流错误事件回调函数的原型定义。 <br>系统内部故障时触发，如音频服务异常退出，非应用调用导致。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioRenderer_OnFastStatusChange)( OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status ) | 音频播放流低时延状态变化事件回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| int32_t (*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize) | 音频播放流写入音频数据回调函数的原型定义。 <br>不同于OH_AudioRenderer_OnWriteDataCallback，此函数允许应用填充[0, audioDataSize]长度的数据。 <br>其中audioDataSize为回调buffer的长度。调用方通过返回值告知系统写入的数据长度。 <br>如果返回0，回调线程将会sleep一段时间。 <br>否则，系统可能会立刻进行下一次回调。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 函数说明

### OH_AudioRenderer_Release()

```c
OH_AudioStream_Result OH_AudioRenderer_Release(OH_AudioRenderer* renderer)
```

**描述：**

释放音频播放流。 <br>输入的OH_AudioRenderer指针指向的内存也会释放，不能再被使用，建议开发者在释放后主动将指针置空。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_Start()

```c
OH_AudioStream_Result OH_AudioRenderer_Start(OH_AudioRenderer* renderer)
```

**描述：**

启动音频播放流。 <br>音频流开始运行后，注册的数据回调会被周期性的触发，让调用者写入要播放的音频数据。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_Pause()

```c
OH_AudioStream_Result OH_AudioRenderer_Pause(OH_AudioRenderer* renderer)
```

**描述：**

暂停音频播放流。 <br>对比OH_AudioRenderer_Stop接口，暂停时已写入系统的音频数据缓存不会被播放完，而是立即停止输出。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_Stop()

```c
OH_AudioStream_Result OH_AudioRenderer_Stop(OH_AudioRenderer* renderer)
```

**描述：**

停止音频播放流。 <br>对比OH_AudioRenderer_Pause接口，通常情况下，已写入系统的音频数据缓存会全部播放完，再停止输出。 但如果音频播放流处于低功耗运行模式，由于系统缓存数据很多，调用本接口仍会立即停止输出。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_Flush()

```c
OH_AudioStream_Result OH_AudioRenderer_Flush(OH_AudioRenderer* renderer)
```

**描述：**

清空音频播放流缓冲区的音频数据。 <br>本接口主要用于音频播放器调节播放进度的场景，可以将已写入的数据清空，避免影响后续播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_GetCurrentState()

```c
OH_AudioStream_Result OH_AudioRenderer_GetCurrentState(OH_AudioRenderer* renderer, OH_AudioStream_State* state)
```

**描述：**

获取当前音频播放流状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_State](capi-native-audiostream-base-h.md#oh_audiostream_state)* state | [out] 用于接收获取的音频播放流状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetSamplingRate()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSamplingRate(OH_AudioRenderer* renderer, int32_t* rate)
```

**描述：**

获取当前音频播放流采样率，单位为Hz。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| int32_t* rate | [out] 用于接收获取的音频播放流采样率，单位为Hz。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetStreamId()

```c
OH_AudioStream_Result OH_AudioRenderer_GetStreamId(OH_AudioRenderer* renderer, uint32_t* streamId)
```

**描述：**

获取当前音频播放流ID。 <br>音频系统会在创建时为每一个音频流分配全局唯一的音频流ID，此ID可以作为音频流的标识。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| uint32_t* streamId | [out] 用于接收获取的音频流ID。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetChannelCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelCount(OH_AudioRenderer* renderer, int32_t* channelCount)
```

**描述：**

获取当前音频播放流声道数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| int32_t* channelCount | [out] 用于接收获取的音频播放流声道数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetSampleFormat()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSampleFormat(OH_AudioRenderer* renderer, OH_AudioStream_SampleFormat* sampleFormat)
```

**描述：**

获取当前音频播放流采样格式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat)* sampleFormat | [out] 用于接收获取的音频播放流采样格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetLatencyMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatencyMode(OH_AudioRenderer* renderer, OH_AudioStream_LatencyMode* latencyMode)
```

**描述：**

获取当前音频播放流时延模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode)* latencyMode | [out] 用于接收获取的音频播放流时延模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetRendererInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererInfo(OH_AudioRenderer* renderer, OH_AudioStream_Usage* usage)
```

**描述：**

获取当前音频播放流的使用场景类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)* usage | [out] 用于接收获取的音频播放流使用场景类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetEncodingType()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEncodingType(OH_AudioRenderer* renderer, OH_AudioStream_EncodingType* encodingType)
```

**描述：**

获取当前音频播放流编码类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype)* encodingType | [out] 用于接收获取的音频播放流编码类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetFramesWritten()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFramesWritten(OH_AudioRenderer* renderer, int64_t* frames)
```

**描述：**

获取自创建音频播放流以来已写入的帧数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| int64_t* frames | [out] 用于接收获取的已写入帧数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetTimestamp()

```c
OH_AudioStream_Result OH_AudioRenderer_GetTimestamp(OH_AudioRenderer* renderer, clockid_t clockId, int64_t* framePosition, int64_t* timestamp)
```

**描述：**

获取音频播放流时间戳和位置信息。 <br>该接口可以获取到音频通道实际播放位置（framePosition）以及播放到该位置时的时间戳（timestamp）。 <br>播放位置单位为采样数（samples），时间戳单位为ns。 <br>当设备切换或暂停恢复时，由于播放通路本身需要一段时间恢复， 调用该接口获取的播放位置和时间戳会短暂地保持在切换或暂停前的状态。 <br>该接口通常用来实现音画同步，调用间隔建议不小于200ms，推荐频率为每秒一次。在能保证音画同步效果的情况下， 不需要频繁地查询时间戳，避免出现功耗问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| clockid_t clockId | [in] 时钟标识符，使用CLOCK_MONOTONIC。 |
| int64_t* framePosition | [out] 用于接收获取的最近输出音频帧位置，单位为采样数。 |
| int64_t* timestamp | [out] 用于接收获取的最近输出音频帧时间戳，与位置对应，单位为ns。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数clockId无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |

### OH_AudioRenderer_GetFrameSizeInCallback()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFrameSizeInCallback(OH_AudioRenderer* renderer, int32_t* frameSize)
```

**描述：**

获取当前音频播放流每次数据回调请求写入的音频数据帧长，单位为采样点数。 <br>当音频播放流运行模式发生变化时，如从低时延模式切换到普通模式，此帧长可能发生变化。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| int32_t* frameSize | [out] 用于接收获取的音频数据帧长，单位为采样点数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSpeed(OH_AudioRenderer* renderer, float* speed)
```

**描述：**

获取音频播放速率。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float* speed | [out] 用于接收获取的音频播放倍速。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_SetSpeed()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSpeed(OH_AudioRenderer* renderer, float speed)
```

**描述：**

设置音频播放速率。 <br>默认播放速率为1.0。播放速率改变会影响音频数据的消耗速度，如设置2倍速时，数据消耗速度也会变为2倍， 调用者需确保写入足够的音频数据。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float speed | [in] 设置播放的倍速值（倍速范围：[0.25, 4.0]）。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_SetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolume(OH_AudioRenderer* renderer, float volume)
```

**描述：**

设置当前音频播放流音量值。 <br>此设置只会影响当前音频播放流，并且不会影响系统全局音量。默认音量为1.0，因此只能通过此接口降低音量。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float volume | [in] 设置当前音频流音量，音量值范围[0.0, 1.0]。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数volume无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 出现系统错误。</li> </ul> |

### OH_AudioRenderer_SetVolumeWithRamp()

```c
OH_AudioStream_Result OH_AudioRenderer_SetVolumeWithRamp(OH_AudioRenderer* renderer, float volume, int32_t durationMs)
```

**描述：**

在指定时间范围内使用渐变更改音量。 <br>此设置只会影响当前音频播放流，并且不会影响系统全局音量。默认音量为1.0，因此只能通过此接口降低音量。 <br>设置后，音频播放流会根据设置的时间，从当前音量逐渐变化到目标音量，通常用于实现播放淡入和淡出效果。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float volume | [in] 目标音量值，取值范围[0.0, 1.0]。 |
| int32_t durationMs | [in] 音量渐变的持续时间，以ms为单位。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数volume无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 出现系统错误。</li> </ul> |

### OH_AudioRenderer_GetVolume()

```c
OH_AudioStream_Result OH_AudioRenderer_GetVolume(OH_AudioRenderer* renderer, float* volume)
```

**描述：**

获取当前音频播放流音量值。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float* volume | [out] 用于接收获取的音频播放流音量值。音量值的范围是[0.0, 1.0]。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数volume为空指针。</li> </ul> |

### OH_AudioRenderer_SetMarkPosition()

```c
OH_AudioStream_Result OH_AudioRenderer_SetMarkPosition(OH_AudioRenderer* renderer, uint32_t samplePos, OH_AudioRenderer_OnMarkReachedCallback callback, void* userData)
```

**描述：**

设置标记位置和对应回调函数。 <br>当播放的音频帧数达到标记位置时，会触发此回调函数。 <br>重复设置会覆盖已设置的标记位置和回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| uint32_t samplePos | [in] 设置目标标记位置，单位为帧数，即采样点数。 |
| [OH_AudioRenderer_OnMarkReachedCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onmarkreachedcallback) callback | [in] 当播放的音频帧数达到标记位置时，会触发此回调函数。 |
| void* userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数samplePos无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 出现系统错误。</li> </ul> |

### OH_AudioRenderer_CancelMark()

```c
OH_AudioStream_Result OH_AudioRenderer_CancelMark(OH_AudioRenderer* renderer)
```

**描述：**

取消由[OH_AudioRenderer_SetMarkPosition](capi-native-audiorenderer-h.md#oh_audiorenderer_setmarkposition)设置的标记和回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetUnderflowCount()

```c
OH_AudioStream_Result OH_AudioRenderer_GetUnderflowCount(OH_AudioRenderer* renderer, uint32_t* count)
```

**描述：**

获取当前音频播放流欠载次数。 <br>在播放过程中，如果调用者没有及时通过数据回调写入音频数据，当系统将内部缓存全部输出后，就会触发欠载， 输出静音数据。 <br>欠载次数是按照音频系统的数据处理周期计算的，而不是以应用设置的回调长度作为周期。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| uint32_t* count | [out] 用于接收获取的音频播放流欠载次数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数count为空指针。</li> </ul> |

### OH_AudioRenderer_GetChannelLayout()

```c
OH_AudioStream_Result OH_AudioRenderer_GetChannelLayout(OH_AudioRenderer* renderer, OH_AudioChannelLayout* channelLayout)
```

**描述：**

获取当前音频播放流声道布局。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout)* channelLayout | [out] 用于接收获取的音频播放流声道布局。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_GetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode* effectMode)
```

**描述：**

获取当前音频播放流音效模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_AudioEffectMode](capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode)* effectMode | [out] 用于接收获取的音频播放流音效模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_SetEffectMode()

```c
OH_AudioStream_Result OH_AudioRenderer_SetEffectMode(OH_AudioRenderer* renderer, OH_AudioStream_AudioEffectMode effectMode)
```

**描述：**

设置当前音频播放流音效模式。 <br>对于媒体类音频，系统会根据[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)为音频流添加音效，以达到更好的用户体验。 但如果开发者不想使用系统默认音效，可通过此接口关闭。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_AudioEffectMode](capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode) effectMode | [in] 目标音效模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetRendererPrivacy()

```c
OH_AudioStream_Result OH_AudioRenderer_GetRendererPrivacy(OH_AudioRenderer* renderer, OH_AudioStream_PrivacyType* privacy)
```

**描述：**

获取当前音频播放流的隐私类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_PrivacyType](capi-native-audiostream-base-h.md#oh_audiostream_privacytype)* privacy | [out] 用于接收获取的音频播放流隐私类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_SetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_SetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool on)
```

**描述：**

设置音频播放流的静音并发播放模式。 <br>设置为true表示打开静音并发播放模式，系统将让此音频流静音播放，其他音频流可以保持正常播放不被打断。设置为false， 将关闭静音并发播放，音频流可根据系统焦点策略抢占焦点。 <br>此接口适用于视频静音播放场景，避免打断正在播放的音乐。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| bool on | [in] 设置当前音频流的静音并发播放模式。 <br>true：设置当前音频播放流为静音播放，其他音频流可以保持正常播放不被打断。 <br>false：取消当前音频播放流静音播放，音频流可根据系统焦点策略抢占焦点。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_GetSilentModeAndMixWithOthers()

```c
OH_AudioStream_Result OH_AudioRenderer_GetSilentModeAndMixWithOthers(OH_AudioRenderer* renderer, bool* on)
```

**描述：**

获取当前音频播放流是否开启静音并发播放模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| bool* on | [out] 用于接收获取的音频流静音并发播放状态。返回true表示打开，返回false表示关闭。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> </ul> |

### OH_AudioRenderer_SetDefaultOutputDevice()

```c
OH_AudioStream_Result OH_AudioRenderer_SetDefaultOutputDevice(OH_AudioRenderer* renderer, OH_AudioDevice_Type deviceType)
```

**描述：**

设置默认本机内置发声设备。 <br>本接口仅适用于音频流类型[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)为语音消息、VoIP语音通话或者VoIP视频通话的场景， 可选的设备类型为听筒、扬声器和系统默认设备。 <br>本接口允许在AudioRenderer创建以后的任何时间被调用，系统会记录应用设置的默认本机内置发声设备。在应用启动播放时， 若有外接设备如蓝牙耳机/有线耳机接入，系统优先从外接设备发声； 否则系统遵循应用设置的默认本机内置发声设备发声。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) deviceType | [in] 目标发声设备类型。可设置的设备类型包括: <br>AUDIO_DEVICE_TYPE_EARPIECE：听筒 <br>AUDIO_DEVICE_TYPE_SPEAKER：扬声器 <br>AUDIO_DEVICE_TYPE_DEFAULT：系统默认设备 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针;2. 参数deviceType无效。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 出现系统错误。</li> </ul> |

### OH_AudioRenderer_GetAudioTimestampInfo()

```c
OH_AudioStream_Result OH_AudioRenderer_GetAudioTimestampInfo(OH_AudioRenderer* renderer, int64_t* framePosition, int64_t* timestamp)
```

**描述：**

获取音频播放流时间戳和位置信息。 <br>相比OH_AudioRenderer_GetTimestamp适配了倍速接口。 <br>通常用于进行音画同步对齐，播放位置单位为采样数（samples），时间戳单位为ns。 <br>当设备切换或暂停恢复时，由于播放通路本身需要一段时间恢复， 调用该接口获取的播放位置和时间戳会短暂地保持在切换或暂停前的状态。 <br>该接口通常用来实现音画同步，调用间隔建议不小于200ms，推荐频率为每秒一次。在能保证音画同步效果的情况下， 不需要频繁地查询时间戳，避免出现功耗问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| int64_t* framePosition | [out] 用于接收获取的最近输出音频帧位置，单位为采样数。 |
| int64_t* timestamp | [out] 用于接收获取的最近输出音频帧时间戳，与位置对应，单位为ns。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数framePosition或timestamp为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 当前流状态不为合法状态时返回。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 系统进程崩溃或被阻塞；2. 内部系统其他错误。</li> </ul> |

### OH_AudioRenderer_OnInterruptCallback()

```c
typedef void (*OH_AudioRenderer_OnInterruptCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioInterrupt_ForceType type, OH_AudioInterrupt_Hint hint)
```

**描述：**

音频播放流中断事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) type | 音频流中断类型。 |
| [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) hint | 音频流中断提示类型。 |

**参考：**

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnInterruptEvent


### OH_AudioRenderer_OnErrorCallback()

```c
typedef void (*OH_AudioRenderer_OnErrorCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_Result error)
```

**描述：**

音频播放流错误事件回调函数的原型定义。 <br>系统内部故障时触发，如音频服务异常退出，非应用调用导致。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) error | 音频流播放错误结果。 |

**参考：**

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnError


### OH_AudioRenderer_GetFastStatus()

```c
OH_AudioStream_Result OH_AudioRenderer_GetFastStatus(OH_AudioRenderer* renderer, OH_AudioStream_FastStatus* status)
```

**描述：**

获取音频播放过程中的运行状态，是否在低时延运行状态下工作。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus)* status | [out] 用于接收获取的低时延运行状态。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数renderer为空指针。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常，仅在释放状态之前可用。</li> </ul> |

### OH_AudioRenderer_OnFastStatusChange()

```c
typedef void (*OH_AudioRenderer_OnFastStatusChange)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_FastStatus status)
```

**描述：**

音频播放流低时延状态变化事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioStream_FastStatus](capi-native-audiostream-base-h.md#oh_audiostream_faststatus) status | 当前低时延运行状态。 |

### OH_AudioRenderer_SetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_SetLoudnessGain(OH_AudioRenderer* renderer, float loudnessGain)
```

**描述：**

设置音频播放的响度值。 <br>默认的响度值是0.0dB。音频流播放类型必须是音乐[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC， 电影或视频[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage). AUDIOSTREAM_USAGE_MOVIE， 有声读物（包括听书、相声、评书）、听新闻、 播客等[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK。 音频流的时延模式必须是普通时延[OH_AudioStream_LatencyMode](capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL。 本接口不支持设置通过高清通路播放的音频流响度。 <br>由于音频框架与硬件之间存在缓冲区，响度调节实际生效存在延迟，时长取决于缓冲区长度。 <br>建议在不同音频开始播放前预先设置响度，以实现最佳均衡效果。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float loudnessGain | [in] 设置播放的响度值（响度值范围为[-90.0, 24.0]，单位为dB）。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 音频流不支持设置响度；3. 参数loudnessGain不在响度值范围内。</li> </ul> |

### OH_AudioRenderer_GetLoudnessGain()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLoudnessGain(OH_AudioRenderer* renderer, float* loudnessGain)
```

**描述：**

获取音频播放流的响度值。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| float* loudnessGain | [out] 用于接收获取的播放响度值，单位为分贝。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数loudnessGain为空指针。</li> </ul> |

### OH_AudioRenderer_OnWriteDataCallbackAdvanced()

```c
typedef int32_t (*OH_AudioRenderer_OnWriteDataCallbackAdvanced)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**描述：**

音频播放流写入音频数据回调函数的原型定义。 <br>不同于OH_AudioRenderer_OnWriteDataCallback，此函数允许应用填充[0, audioDataSize]长度的数据。 <br>其中audioDataSize为回调buffer的长度。调用方通过返回值告知系统写入的数据长度。 <br>如果返回0，回调线程将会sleep一段时间。 <br>否则，系统可能会立刻进行下一次回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| void* audioData | 指向让应用写入的音频数据。 |
| int32_t audioDataSize | 应用可写入音频数据的数据长度，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 应用实际填充有效音频数据的长度。返回值必须在[0, audioDataSize]范围内。<br>如果返回值小于0，系统将调整为0。 并且，如果返回值大于audioDataSize，系统将其调整到audioDataSize。<br>注意返回值必须是单个采样点大小的整数倍。<br>比如，双声道S16格式的音频数据，必须是4(2 * 16 / 8)的整数倍。<br>否则，可能造成播放杂音。 |

**参考：**

[OH_AudioRenderer_OnWriteDataCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_onwritedatacallback)


### OH_AudioRenderer_GetLatency()

```c
OH_AudioStream_Result OH_AudioRenderer_GetLatency(OH_AudioRenderer* renderer, OH_AudioStream_LatencyType type, int32_t* latencyMs)
```

**描述：**

获取当前音频路由的估算时延（单位：ms）。无线连接的音频设备，时延估算可能存在误差，结果仅供参考。 <br>由于时延未计入实时缓冲区，建议仅在音频播放开始时获取，避免频繁调用，否则可能因路由切换而阻塞该接口调用。 <br>当音频数据输出到硬件后，建议使用[OH_AudioRenderer_GetAudioTimestampInfo](capi-native-audiorenderer-h.md#oh_audiorenderer_getaudiotimestampinfo)进行音视频同步。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [OH_AudioStream_LatencyType](capi-native-audiostream-base-h.md#oh_audiostream_latencytype) type | [in] 要获取的时延类型。 |
| int32_t* latencyMs | [out] 用于接收获取的音频时延，单位为ms。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 1. 参数renderer为空指针；2. 参数latencyMs为空指针；3. 参数type无效。</li> <li>[AUDIOSTREAM_ERROR_SYSTEM](capi-native-audiostream-base-h.md#oh_audiostream_result) 系统内部错误，例如音频服务异常。</li> </ul> |

### OH_AudioRenderer_SetIndependentAudioSessionStrategy()

```c
OH_AudioStream_Result OH_AudioRenderer_SetIndependentAudioSessionStrategy(OH_AudioRenderer* renderer, const OH_AudioSession_Strategy* strategy, uint32_t behavior)
```

**描述：**

设置音频播放流的独立音频会话策略和行为参数，这些参数主要用于扩展音频流的默认并发策略。 <br>建议在音频流处于运行状态前设置。当在音频流运行时调用此接口， 只会在下次调用接口[OH_AudioRenderer_Start](capi-native-audiorenderer-h.md#oh_audiorenderer_start)启动音频流后参数才会生效。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | [in] 指向[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频流实例。 |
| [const OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md)* strategy | [in] 用于设置独立的音频会话策略。 |
| uint32_t behavior | [in] 音频会话行为标志，可以是单个标志，也可以是多个标志的按位OR组合。 当前支持的音频会话行为详见[OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioStream_Result](capi-native-audiostream-base-h.md#oh_audiostream_result) | <ul> <li>[AUDIOSTREAM_SUCCESS](capi-native-audiostream-base-h.md#oh_audiostream_result) 函数执行成功。</li> <li>[AUDIOSTREAM_ERROR_INVALID_PARAM](capi-native-audiostream-base-h.md#oh_audiostream_result) 参数为空指针或超出范围。</li> <li>[AUDIOSTREAM_ERROR_ILLEGAL_STATE](capi-native-audiostream-base-h.md#oh_audiostream_result) 执行状态异常。</li> </ul> |


