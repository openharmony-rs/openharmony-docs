# native_audiostream_base.h

## 概述

声明OHAudio基础的数据结构。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) | OH_AudioStreamInfo | 定义音频流信息结构体，用于描述基本音频格式。 |
| [OH_AudioRenderer_Callbacks_Struct](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) | OH_AudioRenderer_Callbacks | 声明输出音频流的回调函数指针。<br>为了避免不可预期的行为，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调函数或空指针初始化。<br>可参考{@link 推荐使用OHAudio开发音频播放功能(C/C++)}。(API20废弃) |
| [OH_AudioCapturer_Callbacks_Struct](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) | OH_AudioCapturer_Callbacks | 声明用于音频采集器的回调函数指针。<br>为了避免不可预期的行为，在设置音频回调函数时，请确保该结构体的每一个成员变量都被自定义的回调方法或空指针初始化。可参考{@link 推荐使用OHAudio开发音频录制功能(C/C++)}。(API20废弃) |
| [OH_AudioStreamBuilderStruct](capi-ohaudio-oh-audiostreambuilderstruct.md) | OH_AudioStreamBuilder | 声明音频流的构造器。构造器实例用于设置音频流属性和创建音频流。 |
| [OH_AudioRendererStruct](capi-ohaudio-oh-audiorendererstruct.md) | OH_AudioRenderer | 声明输出音频渲染器。输出音频渲染器的实例被用来播放音频数据。 |
| [OH_AudioCapturerStruct](capi-ohaudio-oh-audiocapturerstruct.md) | OH_AudioCapturer | 声明音频采集器结构体。音频采集器的实例用于获取输入音频（录音）数据。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStream_Result](#oh_audiostream_result) | OH_AudioStream_Result | 音频错误码。 |
| [OH_AudioStream_Type](#oh_audiostream_type) | OH_AudioStream_Type | 音频流类型。 |
| [OH_AudioStream_SampleFormat](#oh_audiostream_sampleformat) | OH_AudioStream_SampleFormat | 定义音频流采样格式。 |
| [OH_AudioStream_EncodingType](#oh_audiostream_encodingtype) | OH_AudioStream_EncodingType | 定义音频流编码类型。 |
| [OH_AudioStream_Usage](#oh_audiostream_usage) | OH_AudioStream_Usage | 定义音频流使用场景。<br>通常用来描述音频输出流的使用场景。 |
| [OH_AudioStream_LatencyMode](#oh_audiostream_latencymode) | OH_AudioStream_LatencyMode | 定义音频时延模式。 |
| [OH_AudioStream_DirectPlaybackMode](#oh_audiostream_directplaybackmode) | OH_AudioStream_DirectPlaybackMode | 定义音频流direct通路播放模式。 |
| [OH_AudioStream_Event](#oh_audiostream_event) | OH_AudioStream_Event | 定义音频事件。(API20废弃) |
| [OH_AudioStream_State](#oh_audiostream_state) | OH_AudioStream_State | 定义音频流的状态。 |
| [OH_AudioInterrupt_ForceType](#oh_audiointerrupt_forcetype) | OH_AudioInterrupt_ForceType | 定义音频中断类型。<br>当用户监听到音频中断时，将获取此信息。<br>此类型表示本次音频打断的操作是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)获取。 |
| [OH_AudioInterrupt_Hint](#oh_audiointerrupt_hint) | OH_AudioInterrupt_Hint | 定义音频中断提示类型。<br>当用户监听到音频中断时，将获取此信息。<br>此类型表示根据焦点策略，当前需要对音频流的具体操作（如暂停、调整音量等）。<br>可以结合[OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype)信息，判断该操作是否已由系统强制执行。 |
| [OH_AudioStream_SourceType](#oh_audiostream_sourcetype) | OH_AudioStream_SourceType | 定义音频流使用场景。<br>通常用来描述音频输入流的使用场景。 |
| [OH_AudioInterrupt_Mode](#oh_audiointerrupt_mode) | OH_AudioInterrupt_Mode | 定义音频中断模式。 |
| [OH_AudioStream_AudioEffectMode](#oh_audiostream_audioeffectmode) | OH_AudioStream_AudioEffectMode | 定义音效模式。 |
| [OH_AudioStream_FastStatus](#oh_audiostream_faststatus) | OH_AudioStream_FastStatus | 定义低时延状态。 |
| [OH_AudioStream_DeviceChangeReason](#oh_audiostream_devicechangereason) | OH_AudioStream_DeviceChangeReason | 流设备变更原因。 |
| [OH_AudioStream_PrivacyType](#oh_audiostream_privacytype) | OH_AudioStream_PrivacyType | 用于标识对应播放音频流是否支持被其他应用录制。 |
| [OH_AudioData_Callback_Result](#oh_audiodata_callback_result) | OH_AudioData_Callback_Result | 定义音频数据回调结果。 |
| [OH_AudioStream_VolumeMode](#oh_audiostream_volumemode) | OH_AudioStream_VolumeMode | 定义音频流音量模式。 |
| [OH_AudioStream_LatencyType](#oh_audiostream_latencytype) | OH_AudioStream_LatencyType | 定义音频时延类型。 |
| [OH_AudioStream_PlaybackCaptureMode](#oh_audiostream_playbackcapturemode) | OH_AudioStream_PlaybackCaptureMode | 表示内录（录制设备内部应用的声音）的过滤类型，每种过滤类型可录制不同的播放流类型。该API暂不对外支持。 |
| [OH_AudioStream_PlaybackCaptureStartState](#oh_audiostream_playbackcapturestartstate) | OH_AudioStream_PlaybackCaptureStartState | 定义内录的启动状态，该状态在调用{@link OH_AudioCapturer_RequestPlaybackCaptureStart}函数后异步返回。该API暂不对外支持。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)](#oh_audiorenderer_outputdevicechangecallback) | OH_AudioRenderer_OutputDeviceChangeCallback | 输出音频流设备变更的回调函数。 |
| [typedef void (\*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)](#oh_audiorenderer_onmarkreachedcallback) | OH_AudioRenderer_OnMarkReachedCallback | 到达标记位置时回调。 |
| [typedef int32_t (\*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)](#oh_audiorenderer_writedatawithmetadatacallback) | OH_AudioRenderer_WriteDataWithMetadataCallback | 该函数指针将指向用于同时写入音频数据和元数据的回调函数。 |
| [typedef OH_AudioData_Callback_Result (\*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallback) | OH_AudioRenderer_OnWriteDataCallback | 该函数指针将指向用于写入音频数据的回调函数。<br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。<br>该函数的返回结果表示填充到缓冲区的数据是否有效。如果结果无效，用户填写的数据将不被播放。<br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放，因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据，否则会导致音频服务播放杂音。<br>参数audioDataSize可以通过{@link OH_AudioStreamBuilder_SetFrameSizeInCallback}设置。<br>为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。 |

## 枚举类型说明

### OH_AudioStream_Result

```c
enum OH_AudioStream_Result
```

**描述**

音频错误码。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_SUCCESS = 0 | 操作成功<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_INVALID_PARAM = 1 | 入参错误。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_ILLEGAL_STATE = 2 | 非法状态。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_SYSTEM = 3 | 系统通用错误。<br>**起始版本：** 10 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_FORMAT = 4 | 不支持的音频格式，如不支持的编码类型、采样格式等。<br>**起始版本：** 19 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY = 6800104 | 不支持的音频流功能，包括功能和配置。<br>**起始版本：** 26.0.0 |
| AUDIOSTREAM_ERROR_SERVICE_DIED = 6800302 | 音频服务器进程死掉。<br>**起始版本：** 26.0.0 |

### OH_AudioStream_Type

```c
enum OH_AudioStream_Type
```

**描述**

音频流类型。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_TYPE_RENDERER = 1 |  |
| AUDIOSTREAM_TYPE_CAPTURER = 2 |  |

### OH_AudioStream_SampleFormat

```c
enum OH_AudioStream_SampleFormat
```

**描述**

定义音频流采样格式。

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

**描述**

定义音频流编码类型。

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

**描述**

定义音频流使用场景。<br>通常用来描述音频输出流的使用场景。

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

**描述**

定义音频时延模式。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_LATENCY_MODE_NORMAL = 0 |  |
| AUDIOSTREAM_LATENCY_MODE_FAST = 1 |  |

### OH_AudioStream_DirectPlaybackMode

```c
enum OH_AudioStream_DirectPlaybackMode
```

**描述**

定义音频流direct通路播放模式。

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

**描述**

定义音频事件。

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

**描述**

定义音频流的状态。

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

**描述**

定义音频中断类型。<br>当用户监听到音频中断时，将获取此信息。<br>此类型表示本次音频打断的操作是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)获取。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_FORCE = 0 |  |
| AUDIOSTREAM_INTERRUPT_SHARE = 1 |  |

### OH_AudioInterrupt_Hint

```c
enum OH_AudioInterrupt_Hint
```

**描述**

定义音频中断提示类型。<br>当用户监听到音频中断时，将获取此信息。<br>此类型表示根据焦点策略，当前需要对音频流的具体操作（如暂停、调整音量等）。<br>可以结合[OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype)信息，判断该操作是否已由系统强制执行。

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

**描述**

定义音频流使用场景。<br>通常用来描述音频输入流的使用场景。

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

**描述**

定义音频中断模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_MODE_SHARE = 0 | 共享模式。 |
| AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT = 1 | 独立模式。 |

### OH_AudioStream_AudioEffectMode

```c
enum OH_AudioStream_AudioEffectMode
```

**描述**

定义音效模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| EFFECT_NONE = 0 |  |
| EFFECT_DEFAULT = 1 |  |

### OH_AudioStream_FastStatus

```c
enum OH_AudioStream_FastStatus
```

**描述**

定义低时延状态。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_FASTSTATUS_NORMAL = 0 | 普通音频流状态。 |
| AUDIOSTREAM_FASTSTATUS_FAST = 1 | 低时延音频流状态。 |

### OH_AudioStream_DeviceChangeReason

```c
enum OH_AudioStream_DeviceChangeReason
```

**描述**

流设备变更原因。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| REASON_UNKNOWN = 0 | Unknown. |
| REASON_NEW_DEVICE_AVAILABLE = 1 | New Device available. |
| REASON_OVERRODE = 3 | Device is overrode by user or system. |
| REASON_SESSION_ACTIVATED = 4 | 音频会话激活触发的设备切换。<br>**起始版本：** 20 |
| REASON_STREAM_PRIORITY_CHANGED = 5 | 更高优先级的音频流出现导致的系统设备切换。<br>**起始版本：** 20 |

### OH_AudioStream_PrivacyType

```c
enum OH_AudioStream_PrivacyType
```

**描述**

用于标识对应播放音频流是否支持被其他应用录制。

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

**描述**

定义音频数据回调结果。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DATA_CALLBACK_RESULT_INVALID = -1 | 表示音频数据回调结果无效，音频数据不播放。 |
| AUDIO_DATA_CALLBACK_RESULT_VALID = 0 | 表示音频数据回调结果有效，音频数据将被播放。 |

### OH_AudioStream_VolumeMode

```c
enum OH_AudioStream_VolumeMode
```

**描述**

定义音频流音量模式。

**起始版本：** 19

| 枚举项 | 描述 |
| -- | -- |
| AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL = 0 |  |
| AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL = 1 |  |

### OH_AudioStream_LatencyType

```c
enum OH_AudioStream_LatencyType
```

**描述**

定义音频时延类型。

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

**描述**

表示内录（录制设备内部应用的声音）的过滤类型，每种过滤类型可录制不同的播放流类型。该API暂不对外支持。

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

**描述**

定义内录的启动状态，该状态在调用{@link OH_AudioCapturer_RequestPlaybackCaptureStart}函数后异步返回。该API暂不对外支持。

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

**描述**

输出音频流设备变更的回调函数。

**起始版本：** 11

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioRenderer\* renderer | 指向{@link OH_AudioStreamBuilder_GenerateRenderer}创建的音频流实例。 |
| void\* userData | 指向通过回调函数传递的应用数据指针。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) reason | 流设备变更原因。 |

### OH_AudioRenderer_OnMarkReachedCallback()

```c
typedef void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)
```

**描述**

到达标记位置时回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioRenderer\* renderer | 指向{@link OH_AudioStreamBuilder_GenerateRenderer}创建的音频流实例。 |
| uint32_t samplePos | 设置目标标记位置。 |
| void\* userData | 指向通过回调函数传递的应用数据指针。 |

### OH_AudioRenderer_WriteDataWithMetadataCallback()

```c
typedef int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)
```

**描述**

该函数指针将指向用于同时写入音频数据和元数据的回调函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioRenderer\* renderer | 指向{@link OH_AudioStreamBuilder_GenerateRenderer}创建的音频流实例。 |
| void\* userData | 指向通过回调函数传递的应用数据指针。 |
| void\* audioData | 指向用户写入的音频数据的指针。 |
| int32_t audioDataSize | 用户写入的音频数据的数据长度，以字节为单位。 |
| void\* metadata | 指向用户写入的元数据的指针。 |
| int32_t metadataSize | 用户写入的元数据的数据长度，以字节为单位。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 用户返回的回调函数的错误码。 |

### OH_AudioRenderer_OnWriteDataCallback()

```c
typedef OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**描述**

该函数指针将指向用于写入音频数据的回调函数。<br>回调函数仅用来写入音频数据，请勿在回调函数中调用AudioRenderer相关接口。<br>该函数的返回结果表示填充到缓冲区的数据是否有效。如果结果无效，用户填写的数据将不被播放。<br>回调函数结束后，音频服务会把audioData指针数据放入队列里等待播放，因此请勿在回调外再次更改audioData指向的数据，且务必保证往audioData填满audioDataSize长度的待播放数据，否则会导致音频服务播放杂音。<br>参数audioDataSize可以通过{@link OH_AudioStreamBuilder_SetFrameSizeInCallback}设置。<br>为避免音频播放启动和停止时数据不连续可能出现的杂音，系统通常会在启动和停止时对音频数据做20ms以内的淡入淡出处理。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioRenderer\* renderer | 指向{@link OH_AudioStreamBuilder_GenerateRenderer}创建的音频流实例。 |
| void\* userData | 指向通过回调函数传递的应用数据指针。 |
| void\* audioData | 指向用户写入的音频数据的指针。 |
| int32_t audioDataSize | 用户写入的音频数据的数据长度，以字节为单位。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioData_Callback_Result](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) | AUDIO_DATA_CALLBACK_RESULT_INVALID：音频数据回调结果无效，音频数据不播放。<br>     <br>AUDIO_DATA_CALLBACK_RESULT_VALID：音频数据回调结果有效，音频数据将被播放。 |

**参考：**

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData



