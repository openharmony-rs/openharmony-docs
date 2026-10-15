# native_audiostream_base.h

## 概述

声明音频播放和录制流模块使用的基础数据结构和枚举定义。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) | - | 声明音频流信息结构体，该结构体用于表示音频基础格式，包括采样率、声道布局、编码格式和采样格式信息。 |
| [OH_AudioRenderer_Callbacks_Struct](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) | - | 声明用于同时设置音频渲染器的4个回调函数的结构体， 包括写入音频数据、音频播放流事件、音频播放中断事件和音频播放错误回调函数。 [OH_AudioStreamBuilder_SetRendererCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setrenderercallback)接口会用此结构体设置回调。 <br>注意，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。可参考开发指南-推荐使用OHAudio开发音频播放功能(C/C++)。 |
| [OH_AudioCapturer_Callbacks_Struct](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) | - | 声明用于同时设置音频采集器的4个回调函数的结构体， 包括读取音频数据、音频录制流事件、音频录制中断事件和音频录制错误回调函数。 [OH_AudioStreamBuilder_SetCapturerCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setcapturercallback)接口会用此结构体设置回调。 <br>注意，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化， 避免未初始化的回调函数被系统调用，引起不可预知的行为。可参考开发指南-推荐使用OHAudio开发音频录制功能(C/C++)。<br> 说明，以下回调接口的返回值均没有对应枚举定义，当前版本系统并不处理返回值， 但考虑到后续系统版本的可扩展性，建议使用0作为返回值。 |
| [OH_AudioStreamBuilder](capi-ohaudio-oh-audiostreambuilder.md) | OH_AudioStreamBuilder | 声明音频流构造器结构体，该结构体用于调用设置音频流属性和创建音频流功能接口。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md) | OH_AudioRenderer | 声明音频渲染器结构体。该结构体用于调用音频播放流功能接口。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md) | OH_AudioCapturer | 声明音频采集器结构体，该结构体用于调用音频采集流功能接口。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStream_Result](#oh_audiostream_result) | OH_AudioStream_Result | 音频错误码。 |
| [OH_AudioStream_Type](#oh_audiostream_type) | OH_AudioStream_Type | 音频流类型。 |
| [OH_AudioStream_SampleFormat](#oh_audiostream_sampleformat) | OH_AudioStream_SampleFormat | 定义音频流采样格式。 |
| [OH_AudioStream_EncodingType](#oh_audiostream_encodingtype) | OH_AudioStream_EncodingType | 定义音频流编码类型。 |
| [OH_AudioStream_Usage](#oh_audiostream_usage) | OH_AudioStream_Usage | 定义音频播放流使用场景。 <br>使用场景影响音频播放流的音效、音量、设备与焦点策略。 |
| [OH_AudioStream_LatencyMode](#oh_audiostream_latencymode) | OH_AudioStream_LatencyMode | 定义音频时延模式。 |
| [OH_AudioStream_DirectPlaybackMode](#oh_audiostream_directplaybackmode) | OH_AudioStream_DirectPlaybackMode | 定义音频流直通通路播放模式。 <br>使用直通通路的音频播放流，不会与其他播放流混音，系统也不会对数据进行处理，直接输出到底层硬件。 通常用于高音质音源播放场景。 |
| [OH_AudioStream_Event](#oh_audiostream_event) | OH_AudioStream_Event | 定义音频事件。(API20废弃) |
| [OH_AudioStream_State](#oh_audiostream_state) | OH_AudioStream_State | 定义音频流的状态。 |
| [OH_AudioInterrupt_ForceType](#oh_audiointerrupt_forcetype) | OH_AudioInterrupt_ForceType | 定义音频打断强制类型。 <br>当用户监听到音频打断时，将获取此信息。 <br>此类型表示音频打断提示[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)获取。 <br>其中，AUDIOSTREAM_INTERRUPT_HINT_RESUME对应的forceType一定为AUDIOSTREAM_INTERRUPT_SHARE，即恢复操作无法由系统强制执行，需应用自行触发。 |
| [OH_AudioInterrupt_Hint](#oh_audiointerrupt_hint) | OH_AudioInterrupt_Hint | 定义音频中断提示类型。 <br>当用户监听到音频中断时，将获取此信息。 <br>此类型表示根据焦点策略，当前需要对音频流的具体操作（如暂停、调整音量等）。 <br>可以结合[OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype)信息，判断该操作是否已由系统强制执行。 |
| [OH_AudioStream_SourceType](#oh_audiostream_sourcetype) | OH_AudioStream_SourceType | 定义音频录制流使用场景。 <br>使用场景影响音频录制流的音效、设备与焦点策略。 |
| [OH_AudioInterrupt_Mode](#oh_audiointerrupt_mode) | OH_AudioInterrupt_Mode | 定义音频中断模式。 |
| [OH_AudioStream_AudioEffectMode](#oh_audiostream_audioeffectmode) | OH_AudioStream_AudioEffectMode | 定义音效模式。 |
| [OH_AudioStream_FastStatus](#oh_audiostream_faststatus) | OH_AudioStream_FastStatus | 定义低时延状态。 |
| [OH_AudioStream_DeviceChangeReason](#oh_audiostream_devicechangereason) | OH_AudioStream_DeviceChangeReason | 流设备变更原因。 |
| [OH_AudioStream_PrivacyType](#oh_audiostream_privacytype) | OH_AudioStream_PrivacyType | 用于标识对应播放音频流是否支持被其他应用录制。 |
| [OH_AudioData_Callback_Result](#oh_audiodata_callback_result) | OH_AudioData_Callback_Result | 定义音频数据回调结果。 |
| [OH_AudioStream_VolumeMode](#oh_audiostream_volumemode) | OH_AudioStream_VolumeMode | 定义音频流音量模式。 |
| [OH_AudioStream_LatencyType](#oh_audiostream_latencytype) | OH_AudioStream_LatencyType | 定义音频时延类型。 |
| [OH_AudioStream_PlaybackCaptureMode](#oh_audiostream_playbackcapturemode) | OH_AudioStream_PlaybackCaptureMode | 表示内录（录制设备内部应用的声音）的过滤类型，每种过滤类型可录制不同的播放流类型。 该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。 |
| [OH_AudioStream_PlaybackCaptureStartState](#oh_audiostream_playbackcapturestartstate) | OH_AudioStream_PlaybackCaptureStartState | 定义内录的启动状态，该状态在调用OH_AudioCapturer_RequestPlaybackCaptureStart函数后异步返回。 该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)](#oh_audiorenderer_outputdevicechangecallback) | OH_AudioRenderer_OutputDeviceChangeCallback | 音频播放流输出设备变化回调函数的原型定义。 |
| [typedef void (\*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)](#oh_audiorenderer_onmarkreachedcallback) | OH_AudioRenderer_OnMarkReachedCallback | 音频播放到达标记位置事件回调函数的原型定义。 |
| [typedef int32_t (\*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)](#oh_audiorenderer_writedatawithmetadatacallback) | OH_AudioRenderer_WriteDataWithMetadataCallback | 音频播放流写入音频数据和元数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。 |
| [typedef OH_AudioData_Callback_Result (\*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallback) | OH_AudioRenderer_OnWriteDataCallback | 音频播放流写入音频数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>该函数的返回结果表示填充到缓冲区的数据是否有效。如果结果是无效，用户填写的数据将不被播放。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。 <br>参数audioDataSize可以通过[OH_AudioStreamBuilder_SetFrameSizeInCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setframesizeincallback)设置。 <br>为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason) | 音频播放流输出设备变化回调函数的原型定义。<br>**起始版本：** 11<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData) | 音频播放到达标记位置事件回调函数的原型定义。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize) | 音频播放流写入音频数据和元数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize) | 音频播放流写入音频数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>该函数的返回结果表示填充到缓冲区的数据是否有效。如果结果是无效，用户填写的数据将不被播放。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。 <br>参数audioDataSize可以通过[OH_AudioStreamBuilder_SetFrameSizeInCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setframesizeincallback)设置。 <br>为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 枚举类型说明

### OH_AudioStream_Result

```c
enum OH_AudioStream_Result
```

**描述：**

音频错误码。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_SUCCESS = 0 | &nbsp;操作成功<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_INVALID_PARAM = 1 | &nbsp;入参错误。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_ILLEGAL_STATE = 2 | &nbsp;非法状态。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_SYSTEM = 3 | &nbsp;系统通用错误。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_FORMAT = 4 | &nbsp;不支持的音频格式，如不支持的编码类型、采样格式等。<br>**起始版本：** 19 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY = 6800104 | &nbsp;不支持的音频流功能，包括功能和配置。<br>**起始版本：** 26.0.0 |
| AUDIOSTREAM_ERROR_SERVICE_DIED = 6800302 | &nbsp;音频服务器进程死掉。<br>**起始版本：** 26.0.0 |

### OH_AudioStream_Type

```c
enum OH_AudioStream_Type
```

**描述：**

音频流类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_TYPE_RENDERER = 1 |  |
| AUDIOSTREAM_TYPE_CAPTURER = 2 |  |

### OH_AudioStream_SampleFormat

```c
enum OH_AudioStream_SampleFormat
```

**描述：**

定义音频流采样格式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_SAMPLE_U8 = 0 |  |
| AUDIOSTREAM_SAMPLE_S16LE = 1 |  |
| AUDIOSTREAM_SAMPLE_S24LE = 2 |  |
| AUDIOSTREAM_SAMPLE_S32LE = 3 |  |
| AUDIOSTREAM_SAMPLE_F32LE = 4 |  |

### OH_AudioStream_EncodingType

```c
enum OH_AudioStream_EncodingType
```

**描述：**

定义音频流编码类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_ENCODING_TYPE_RAW = 0 |  |
| AUDIOSTREAM_ENCODING_TYPE_AUDIOVIVID = 1 |  |
| AUDIOSTREAM_ENCODING_TYPE_E_AC3 = 2 |  |

### OH_AudioStream_Usage

```c
enum OH_AudioStream_Usage
```

**描述：**

定义音频播放流使用场景。 <br>使用场景影响音频播放流的音效、音量、设备与焦点策略。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_USAGE_UNKNOWN = 0 |  |
| AUDIOSTREAM_USAGE_MUSIC = 1 |  |
| AUDIOSTREAM_USAGE_VOICE_COMMUNICATION = 2 |  |
| AUDIOSTREAM_USAGE_VOICE_ASSISTANT = 3 |  |
| AUDIOSTREAM_USAGE_ALARM = 4 |  |
| AUDIOSTREAM_USAGE_VOICE_MESSAGE = 5 |  |
| AUDIOSTREAM_USAGE_RINGTONE = 6 |  |
| AUDIOSTREAM_USAGE_NOTIFICATION = 7 |  |
| AUDIOSTREAM_USAGE_ACCESSIBILITY = 8 |  |
| AUDIOSTREAM_USAGE_MOVIE = 10 |  |
| AUDIOSTREAM_USAGE_GAME = 11 |  |
| AUDIOSTREAM_USAGE_AUDIOBOOK = 12 |  |
| AUDIOSTREAM_USAGE_NAVIGATION = 13 |  |
| AUDIOSTREAM_USAGE_VIDEO_COMMUNICATION = 17 |  |

### OH_AudioStream_LatencyMode

```c
enum OH_AudioStream_LatencyMode
```

**描述：**

定义音频时延模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_LATENCY_MODE_NORMAL = 0 |  |
| AUDIOSTREAM_LATENCY_MODE_FAST = 1 |  |

### OH_AudioStream_DirectPlaybackMode

```c
enum OH_AudioStream_DirectPlaybackMode
```

**描述：**

定义音频流直通通路播放模式。 <br>使用直通通路的音频播放流，不会与其他播放流混音，系统也不会对数据进行处理，直接输出到底层硬件。 通常用于高音质音源播放场景。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_DIRECT_PLAYBACK_NOT_SUPPORTED = 0 |  |
| AUDIOSTREAM_DIRECT_PLAYBACK_BITSTREAM_SUPPORTED = 1 |  |
| AUDIOSTREAM_DIRECT_PLAYBACK_PCM_SUPPORTED = 2 |  |

### OH_AudioStream_Event

```c
enum OH_AudioStream_Event
```

**描述：**

定义音频事件。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**废弃版本：** 20

**替代接口：** OH_AudioRenderer_OutputDeviceChangeCallback.

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_EVENT_ROUTING_CHANGED = 0 |  |

### OH_AudioStream_State

```c
enum OH_AudioStream_State
```

**描述：**

定义音频流的状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_STATE_INVALID = -1 |  |
| AUDIOSTREAM_STATE_NEW = 0 |  |
| AUDIOSTREAM_STATE_PREPARED = 1 |  |
| AUDIOSTREAM_STATE_RUNNING = 2 |  |
| AUDIOSTREAM_STATE_STOPPED = 3 |  |
| AUDIOSTREAM_STATE_RELEASED = 4 |  |
| AUDIOSTREAM_STATE_PAUSED = 5 |  |

### OH_AudioInterrupt_ForceType

```c
enum OH_AudioInterrupt_ForceType
```

**描述：**

定义音频打断强制类型。 <br>当用户监听到音频打断时，将获取此信息。 <br>此类型表示音频打断提示[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)获取。 <br>其中，AUDIOSTREAM_INTERRUPT_HINT_RESUME对应的forceType一定为AUDIOSTREAM_INTERRUPT_SHARE，即恢复操作无法由系统强制执行，需应用自行触发。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_FORCE = 0 |  |
| AUDIOSTREAM_INTERRUPT_SHARE = 1 |  |

### OH_AudioInterrupt_Hint

```c
enum OH_AudioInterrupt_Hint
```

**描述：**

定义音频中断提示类型。 <br>当用户监听到音频中断时，将获取此信息。 <br>此类型表示根据焦点策略，当前需要对音频流的具体操作（如暂停、调整音量等）。 <br>可以结合[OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype)信息，判断该操作是否已由系统强制执行。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_HINT_NONE = 0 |  |
| AUDIOSTREAM_INTERRUPT_HINT_RESUME = 1 |  |
| AUDIOSTREAM_INTERRUPT_HINT_PAUSE = 2 |  |
| AUDIOSTREAM_INTERRUPT_HINT_STOP = 3 |  |
| AUDIOSTREAM_INTERRUPT_HINT_DUCK = 4 |  |
| AUDIOSTREAM_INTERRUPT_HINT_UNDUCK = 5 |  |
| AUDIOSTREAM_INTERRUPT_HINT_MUTE = 6 |  |
| AUDIOSTREAM_INTERRUPT_HINT_UNMUTE = 7 |  |

### OH_AudioStream_SourceType

```c
enum OH_AudioStream_SourceType
```

**描述：**

定义音频录制流使用场景。 <br>使用场景影响音频录制流的音效、设备与焦点策略。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_SOURCE_TYPE_INVALID = -1 |  |
| AUDIOSTREAM_SOURCE_TYPE_MIC = 0 |  |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_RECOGNITION = 1 |  |
| AUDIOSTREAM_SOURCE_TYPE_PLAYBACK_CAPTURE = 2 |  |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION = 7 |  |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE = 10 |  |
| AUDIOSTREAM_SOURCE_TYPE_CAMCORDER = 13 |  |
| AUDIOSTREAM_SOURCE_TYPE_UNPROCESSED = 14 |  |
| AUDIOSTREAM_SOURCE_TYPE_LIVE = 17 |  |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK = 22 |  |

### OH_AudioInterrupt_Mode

```c
enum OH_AudioInterrupt_Mode
```

**描述：**

定义音频中断模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_MODE_SHARE = 0 | 共享模式。应用进程的不同音频流共享一个焦点，不会相互打断。 |
| AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT = 1 | 独立模式。应用进程的不同音频流焦点独立，根据系统默认的焦点策略，可以相互打断。 |

### OH_AudioStream_AudioEffectMode

```c
enum OH_AudioStream_AudioEffectMode
```

**描述：**

定义音效模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| EFFECT_NONE = 0 |  |
| EFFECT_DEFAULT = 1 |  |

### OH_AudioStream_FastStatus

```c
enum OH_AudioStream_FastStatus
```

**描述：**

定义低时延状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_FASTSTATUS_NORMAL = 0 | 普通音频流状态。 |
| AUDIOSTREAM_FASTSTATUS_FAST = 1 |  |

### OH_AudioStream_DeviceChangeReason

```c
enum OH_AudioStream_DeviceChangeReason
```

**描述：**

流设备变更原因。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| REASON_UNKNOWN = 0 | 未知原因。 |
| REASON_NEW_DEVICE_AVAILABLE = 1 | 新设备可用。例如，音频播放过程中连接有线/蓝牙耳机。 |
| REASON_OLD_DEVICE_UNAVAILABLE = 2 | 旧设备不可用。例如，音频播放过程中断开有线/蓝牙耳机。当报告此原因时，应用程序应考虑暂停音频播放。 |
| REASON_OVERRODE = 3 | 用户或系统强制选择切换。例如，在播控中心强选设备。 |
| REASON_SESSION_ACTIVATED = 4 | 音频会话管理中激活音频会话触发的设备切换。<br>**起始版本：** 20 |
| REASON_STREAM_PRIORITY_CHANGED = 5 | 更高优先级的音频流出现导致的系统设备切换。例如，音乐播放过程中来电，通话流优先级更高导致音乐设备被切换。<br>**起始版本：** 20 |

### OH_AudioStream_PrivacyType

```c
enum OH_AudioStream_PrivacyType
```

**描述：**

用于标识对应播放音频流是否支持被其他应用录制。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_STREAM_PRIVACY_TYPE_PUBLIC = 0 |  |
| AUDIO_STREAM_PRIVACY_TYPE_PRIVATE = 1 |  |
| AUDIO_STREAM_PRIVACY_TYPE_SHARED = 2 |  |

### OH_AudioData_Callback_Result

```c
enum OH_AudioData_Callback_Result
```

**描述：**

定义音频数据回调结果。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DATA_CALLBACK_RESULT_INVALID = -1 | 表示音频数据回调结果无效，音频数据不播放。 |
| AUDIO_DATA_CALLBACK_RESULT_VALID = 0 | 表示音频数据回调结果有效，音频数据将被播放。 |

### OH_AudioStream_VolumeMode

```c
enum OH_AudioStream_VolumeMode
```

**描述：**

定义音频流音量模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL = 0 |  |
| AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL = 1 |  |

### OH_AudioStream_LatencyType

```c
enum OH_AudioStream_LatencyType
```

**描述：**

定义音频时延类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_LATENCY_TYPE_ALL = 0 |  |
| AUDIOSTREAM_LATENCY_TYPE_SOFTWARE = 1 |  |
| AUDIOSTREAM_LATENCY_TYPE_HARDWARE = 2 |  |

### OH_AudioStream_PlaybackCaptureMode

```c
enum OH_AudioStream_PlaybackCaptureMode
```

**描述：**

表示内录（录制设备内部应用的声音）的过滤类型，每种过滤类型可录制不同的播放流类型。 该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_DEFAULT = 0x0 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_MEDIA = 0x1 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_EXCLUDING_SELF = 0x8000 |  |

### OH_AudioStream_PlaybackCaptureStartState

```c
enum OH_AudioStream_PlaybackCaptureStartState
```

**描述：**

定义内录的启动状态，该状态在调用OH_AudioCapturer_RequestPlaybackCaptureStart函数后异步返回。 该API最初仅对特定系统应用可用，从API版本26.0.0开始，支持任意应用使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_SUCCESS = 0 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_FAILED = 1 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_NOT_AUTHORIZED = 2 |  |


## 函数说明

### OH_AudioRenderer_OutputDeviceChangeCallback()

```c
typedef void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)
```

**描述：**

音频播放流输出设备变化回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) reason | 播放流设备变化原因。 |

### OH_AudioRenderer_OnMarkReachedCallback()

```c
typedef void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)
```

**描述：**

音频播放到达标记位置事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| uint32_t samplePos | 设置的播放到达标记位置，单位为采样点数。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |

### OH_AudioRenderer_WriteDataWithMetadataCallback()

```c
typedef int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)
```

**描述：**

音频播放流写入音频数据和元数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| void* audioData | 指向让应用写入的音频数据。 |
| int32_t audioDataSize | 应用需写入音频数据的数据长度，单位为字节(Byte)。 |
| void* metadata | 指向让应用写入的元数据，元数据内容与音频流编码格式类型相关。 |
| int32_t metadataSize | 应用需写入元数据的数据长度，单位为字节(Byte)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 应用返回的回调函数的错误码。 |

### OH_AudioRenderer_OnWriteDataCallback()

```c
typedef OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**描述：**

音频播放流写入音频数据回调函数的原型定义。 <br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。 <br>该函数的返回结果表示填充到缓冲区的数据是否有效。如果结果是无效，用户填写的数据将不被播放。 <br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放， 因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据， 否则会导致音频服务播放杂音。 <br>参数audioDataSize可以通过[OH_AudioStreamBuilder_SetFrameSizeInCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setframesizeincallback)设置。 <br>为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md)* renderer | 指向触发回调的音频播放流实例。 |
| void* userData | 指向开发者在注册回调函数时传入的userData数据。 |
| void* audioData | 指向让应用写入的音频数据。 |
| int32_t audioDataSize | 应用需写入音频数据的数据长度，单位为字节(Byte)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioData_Callback_Result](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) | <ul> <li>[AUDIO_DATA_CALLBACK_RESULT_INVALID](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) 音频数据回调结果无效，音频数据不播放。</li> <li>[AUDIO_DATA_CALLBACK_RESULT_VALID](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) 音频数据回调结果有效，音频数据将被播放。</li> </ul> |

**参考：**

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData



