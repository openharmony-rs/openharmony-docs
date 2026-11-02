# native_audiostream_base.h

## Overview

Declare the underlying data structure.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-audio-kit-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) | - | Define the audio stream info structure, used to describe basic audio format. |
| [OH_AudioRenderer_Callbacks_Struct](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) | - | Declaring the callback struct for renderer stream. |
| [OH_AudioCapturer_Callbacks_Struct](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) | - | Declaring the callback struct for capturer stream. |
| [OH_AudioStreamBuilderStruct](capi-ohaudio-oh-audiostreambuilderstruct.md) | OH_AudioStreamBuilder | Declaring the audio stream builder. The instance of builder is used for creating audio stream. |
| [OH_AudioRendererStruct](capi-ohaudio-oh-audiorendererstruct.md) | OH_AudioRenderer | Declaring the audio renderer stream. The instance of renderer stream is used for playing audio data. |
| [OH_AudioCapturerStruct](capi-ohaudio-oh-audiocapturerstruct.md) | OH_AudioCapturer | Declaring the audio capturer stream. The instance of renderer stream is used for capturing audio data. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStream_Result](#oh_audiostream_result) | OH_AudioStream_Result | Define the result of the function execution. |
| [OH_AudioStream_Type](#oh_audiostream_type) | OH_AudioStream_Type | Define the audio stream type. |
| [OH_AudioStream_SampleFormat](#oh_audiostream_sampleformat) | OH_AudioStream_SampleFormat | Define the audio stream sample format. |
| [OH_AudioStream_EncodingType](#oh_audiostream_encodingtype) | OH_AudioStream_EncodingType | Define the audio encoding type. |
| [OH_AudioStream_Usage](#oh_audiostream_usage) | OH_AudioStream_Usage | Define the audio stream usage. Audio stream usage is used to describe what work scenario the current stream is used for. |
| [OH_AudioStream_LatencyMode](#oh_audiostream_latencymode) | OH_AudioStream_LatencyMode | Define the audio latency mode. |
| [OH_AudioStream_DirectPlaybackMode](#oh_audiostream_directplaybackmode) | OH_AudioStream_DirectPlaybackMode | Enumerates audio direct playback modes. |
| [OH_AudioStream_Event](#oh_audiostream_event) | OH_AudioStream_Event | Define the audio event.(Deprecated in API20) |
| [OH_AudioStream_State](#oh_audiostream_state) | OH_AudioStream_State | The audio stream states |
| [OH_AudioInterrupt_ForceType](#oh_audiointerrupt_forcetype) | OH_AudioInterrupt_ForceType | Defines the audio interrupt type. |
| [OH_AudioInterrupt_Hint](#oh_audiointerrupt_hint) | OH_AudioInterrupt_Hint | Defines the audio interrupt hint type. |
| [OH_AudioStream_SourceType](#oh_audiostream_sourcetype) | OH_AudioStream_SourceType | Defines the audio source type. |
| [OH_AudioInterrupt_Mode](#oh_audiointerrupt_mode) | OH_AudioInterrupt_Mode | Defines the audio interrupt mode. |
| [OH_AudioStream_AudioEffectMode](#oh_audiostream_audioeffectmode) | OH_AudioStream_AudioEffectMode | Defines the audio effect mode. |
| [OH_AudioStream_FastStatus](#oh_audiostream_faststatus) | OH_AudioStream_FastStatus | Defines the fast status. |
| [OH_AudioStream_DeviceChangeReason](#oh_audiostream_devicechangereason) | OH_AudioStream_DeviceChangeReason | Defines reason for device changes of one audio stream. |
| [OH_AudioStream_PrivacyType](#oh_audiostream_privacytype) | OH_AudioStream_PrivacyType | Defines Enumeration of audio stream privacy type for playback capture. |
| [OH_AudioData_Callback_Result](#oh_audiodata_callback_result) | OH_AudioData_Callback_Result | Defines enumeration of audio data callback result. |
| [OH_AudioStream_VolumeMode](#oh_audiostream_volumemode) | OH_AudioStream_VolumeMode | Define the audio stream volume mode. |
| [OH_AudioStream_LatencyType](#oh_audiostream_latencytype) | OH_AudioStream_LatencyType | Defines audio latency types. |
| [OH_AudioStream_PlaybackCaptureMode](#oh_audiostream_playbackcapturemode) | OH_AudioStream_PlaybackCaptureMode | Defines mode for playback capture, each mode means different target streams to capture. |
| [OH_AudioStream_PlaybackCaptureStartState](#oh_audiostream_playbackcapturestartstate) | OH_AudioStream_PlaybackCaptureStartState | Defines the playback capture start state, which is returned asynchronously after calling [OH_AudioCapturer_RequestPlaybackCaptureStart](capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart) function. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)](#oh_audiorenderer_outputdevicechangecallback) | OH_AudioRenderer_OutputDeviceChangeCallback | Callback when the output device of an audio renderer changed. |
| [typedef void (\*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)](#oh_audiorenderer_onmarkreachedcallback) | OH_AudioRenderer_OnMarkReachedCallback | Callback when the mark position reached. |
| [typedef int32_t (\*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)](#oh_audiorenderer_writedatawithmetadatacallback) | OH_AudioRenderer_WriteDataWithMetadataCallback | This function pointer will point to the callback function that is used to write audio data with metadata |
| [typedef OH_AudioData_Callback_Result (\*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallback) | OH_AudioRenderer_OnWriteDataCallback | Callback function of write data.<br> This function is similar with OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData instead of the return value. The return result of this function indicates whether the data filled in the buffer is valid or invalid. If result is invalid, the data filled by user will not be played. |

## Enum type description

### OH_AudioStream_Result

```c
enum OH_AudioStream_Result
```

**Description**

Define the result of the function execution.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_SUCCESS = 0 | &nbsp;The call was successful.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_INVALID_PARAM = 1 | &nbsp;This means that the function was executed with an invalid input parameter.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_ILLEGAL_STATE = 2 | &nbsp;Execution status exception.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_SYSTEM = 3 | &nbsp;An system error has occurred.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_FORMAT = 4 | &nbsp;Unsupported audio format, such as unsupported encoding type, sample format etc.<br>**Since**: 19 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY = 6800104 | &nbsp;Unsupported audio stream ability, including function and configuration.<br>**Since**: 26.0.0 |
| AUDIOSTREAM_ERROR_SERVICE_DIED = 6800302 | &nbsp;Audio server process died.<br>**Since**: 26.0.0 |

### OH_AudioStream_Type

```c
enum OH_AudioStream_Type
```

**Description**

Define the audio stream type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_TYPE_RENDERER = 1 | The type for audio stream is renderer.<br>**Since**: 10 |
| AUDIOSTREAM_TYPE_CAPTURER = 2 | The type for audio stream is capturer.<br>**Since**: 10 |

### OH_AudioStream_SampleFormat

```c
enum OH_AudioStream_SampleFormat
```

**Description**

Define the audio stream sample format.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_SAMPLE_U8 = 0 | Unsigned 8 format.<br>**Since**: 10 |
| AUDIOSTREAM_SAMPLE_S16LE = 1 | Signed 16 bit integer, little endian.<br>**Since**: 10 |
| AUDIOSTREAM_SAMPLE_S24LE = 2 | Signed 24 bit integer, little endian.<br>**Since**: 10 |
| AUDIOSTREAM_SAMPLE_S32LE = 3 | Signed 32 bit integer, little endian.<br>**Since**: 10 |
| AUDIOSTREAM_SAMPLE_F32LE = 4 | Float 32, little endian.<br>**Since**: 17 |

### OH_AudioStream_EncodingType

```c
enum OH_AudioStream_EncodingType
```

**Description**

Define the audio encoding type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_ENCODING_TYPE_RAW = 0 | PCM encoding type.<br>**Since**: 10 |
| AUDIOSTREAM_ENCODING_TYPE_AUDIOVIVID = 1 | AudioVivid encoding type.<br>**Since**: 12 |
| AUDIOSTREAM_ENCODING_TYPE_E_AC3 = 2 | E_AC3 encoding type.<br>**Since**: 19 |

### OH_AudioStream_Usage

```c
enum OH_AudioStream_Usage
```

**Description**

Define the audio stream usage. Audio stream usage is used to describe what work scenario the current stream is used for.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_USAGE_UNKNOWN = 0 | Unknown usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_MUSIC = 1 | Music usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_VOICE_COMMUNICATION = 2 | Voice communication usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_VOICE_ASSISTANT = 3 | Voice assistant usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_ALARM = 4 | Alarm usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_VOICE_MESSAGE = 5 | Voice message usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_RINGTONE = 6 | Ringtone usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_NOTIFICATION = 7 | Notification usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_ACCESSIBILITY = 8 | Accessibility usage, such as screen reader.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_MOVIE = 10 | Movie or video usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_GAME = 11 | Game sound effect usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_AUDIOBOOK = 12 | Audiobook usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_NAVIGATION = 13 | Navigation usage.<br>**Since**: 10 |
| AUDIOSTREAM_USAGE_VIDEO_COMMUNICATION = 17 | Video call usage.<br>**Since**: 12 |

### OH_AudioStream_LatencyMode

```c
enum OH_AudioStream_LatencyMode
```

**Description**

Define the audio latency mode.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_LATENCY_MODE_NORMAL = 0 | This is a normal audio scene.<br>**Since**: 10 |
| AUDIOSTREAM_LATENCY_MODE_FAST = 1 | This is a low latency audio scene.<br>**Since**: 10 |

### OH_AudioStream_DirectPlaybackMode

```c
enum OH_AudioStream_DirectPlaybackMode
```

**Description**

Enumerates audio direct playback modes.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_DIRECT_PLAYBACK_NOT_SUPPORTED = 0 | Direct playback is not supported.<br>**Since**: 19 |
| AUDIOSTREAM_DIRECT_PLAYBACK_BITSTREAM_SUPPORTED = 1 | Direct playback mode which is bitstream pass-through such as compressed pass-through.<br>**Since**: 19 |
| AUDIOSTREAM_DIRECT_PLAYBACK_PCM_SUPPORTED = 2 | Direct playback mode of pcm.<br>**Since**: 19 |

### OH_AudioStream_Event

```c
enum OH_AudioStream_Event
```

**Description**

Define the audio event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OutputDeviceChangeCallback.

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_EVENT_ROUTING_CHANGED = 0 | The routing of the audio has changed.<br>**Since**: 10<br>**Deprecated**: 20<br>**Replaced by**: OH_AudioRenderer_OutputDeviceChangeCallback. |

### OH_AudioStream_State

```c
enum OH_AudioStream_State
```

**Description**

The audio stream states

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_STATE_INVALID = -1 | The invalid state.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_NEW = 0 | Create new instance state.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_PREPARED = 1 | The prepared state.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_RUNNING = 2 | The stream is running.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_STOPPED = 3 | The stream is stopped.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_RELEASED = 4 | The stream is released.<br>**Since**: 10 |
| AUDIOSTREAM_STATE_PAUSED = 5 | The stream is paused.<br>**Since**: 10 |

### OH_AudioInterrupt_ForceType

```c
enum OH_AudioInterrupt_ForceType
```

**Description**

Defines the audio interrupt type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_FORCE = 0 | Force type, system change audio state.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_SHARE = 1 | Share type, application change audio state.<br>**Since**: 10 |

### OH_AudioInterrupt_Hint

```c
enum OH_AudioInterrupt_Hint
```

**Description**

Defines the audio interrupt hint type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_HINT_NONE = 0 | None.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_RESUME = 1 | Resume the stream.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_PAUSE = 2 | Pause the stream.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_STOP = 3 | Stop the stream.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_DUCK = 4 | Ducked the stream.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_UNDUCK = 5 | Unducked the stream.<br>**Since**: 10 |
| AUDIOSTREAM_INTERRUPT_HINT_MUTE = 6 | Mute the stream.<br>**Since**: 20 |
| AUDIOSTREAM_INTERRUPT_HINT_UNMUTE = 7 | Unmute the stream.<br>**Since**: 20 |

### OH_AudioStream_SourceType

```c
enum OH_AudioStream_SourceType
```

**Description**

Defines the audio source type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_SOURCE_TYPE_INVALID = -1 | Invalid type.<br>**Since**: 10 |
| AUDIOSTREAM_SOURCE_TYPE_MIC = 0 | Mic source type.<br>**Since**: 10 |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_RECOGNITION = 1 | Voice recognition source type.<br>**Since**: 10 |
| AUDIOSTREAM_SOURCE_TYPE_PLAYBACK_CAPTURE = 2 | Playback capture source type.<br>**Since**: 10<br>**Deprecated**: 12<br>**Replaced by**: OH_AVScreenCapture in native interface. |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION = 7 | Voice communication source type.<br>**Since**: 10 |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE = 10 | Voice message source type.<br>**Since**: 12 |
| AUDIOSTREAM_SOURCE_TYPE_CAMCORDER = 13 | Camcorder source type.<br>**Since**: 13 |
| AUDIOSTREAM_SOURCE_TYPE_UNPROCESSED = 14 | Unprocessed source type.<br>**Since**: 14 |
| AUDIOSTREAM_SOURCE_TYPE_LIVE = 17 | Live Broadcast source type.<br>**Since**: 20 |
| AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK = 22 | Voice call downlink source type. The audio capturer using this source type should be created after the voice call started. Note that ohos.permission.CAPTURE_PLAYBACK_DOWNLINK is needed when using [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer) to create the capturer stream, the function will return an error without permission.<br>**Since**: 26.0.0 |

### OH_AudioInterrupt_Mode

```c
enum OH_AudioInterrupt_Mode
```

**Description**

Defines the audio interrupt mode.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_MODE_SHARE = 0 | Share mode |
| AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT = 1 | Independent mode |

### OH_AudioStream_AudioEffectMode

```c
enum OH_AudioStream_AudioEffectMode
```

**Description**

Defines the audio effect mode.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_NONE = 0 | Audio Effect Mode effect none.<br>**Since**: 12 |
| EFFECT_DEFAULT = 1 | Audio Effect Mode effect default.<br>**Since**: 12 |

### OH_AudioStream_FastStatus

```c
enum OH_AudioStream_FastStatus
```

**Description**

Defines the fast status.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_FASTSTATUS_NORMAL = 0 | normal status |
| AUDIOSTREAM_FASTSTATUS_FAST = 1 | fast status |

### OH_AudioStream_DeviceChangeReason

```c
enum OH_AudioStream_DeviceChangeReason
```

**Description**

Defines reason for device changes of one audio stream.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| REASON_UNKNOWN = 0 | Unknown. |
| REASON_NEW_DEVICE_AVAILABLE = 1 | New Device available. |
| REASON_OLD_DEVICE_UNAVAILABLE = 2 | Old Device unavailable. Applications should consider to pause the audio playback when this reason is reported. |
| REASON_OVERRODE = 3 | Device is overrode by user or system. |
| REASON_SESSION_ACTIVATED = 4 | Device information when the audio session is activated.<br>**Since**: 20 |
| REASON_STREAM_PRIORITY_CHANGED = 5 | There is a higher-priority stream, causing the system device to change.<br>**Since**: 20 |

### OH_AudioStream_PrivacyType

```c
enum OH_AudioStream_PrivacyType
```

**Description**

Defines Enumeration of audio stream privacy type for playback capture.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_STREAM_PRIVACY_TYPE_PUBLIC = 0 | Privacy type that stream can be captured by third party applications.<br>**Since**: 12 |
| AUDIO_STREAM_PRIVACY_TYPE_PRIVATE = 1 | Privacy type that stream can not be captured.<br>**Since**: 12 |
| AUDIO_STREAM_PRIVACY_TYPE_SHARED = 2 | Privacy type that stream can be safely captured and screen casting. For example,[AUDIOSTREAM_USAGE_VOICE_COMMUNICATION](capi-native-audiostream-base-h.md#oh_audiostream_usage) will not be captured or screen casted by third party applications under AUDIO_STREAM_PRIVACY_TYPE_PUBLIC policy. However, the internal capture is allowed under the AUDIO_STREAM_PRIVACY_TYPE_SHARED policy.<br>**Since**: 21 |

### OH_AudioData_Callback_Result

```c
enum OH_AudioData_Callback_Result
```

**Description**

Defines enumeration of audio data callback result.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DATA_CALLBACK_RESULT_INVALID = -1 | Result of audio data callback is invalid. |
| AUDIO_DATA_CALLBACK_RESULT_VALID = 0 | Result of audio data callback is valid. |

### OH_AudioStream_VolumeMode

```c
enum OH_AudioStream_VolumeMode
```

**Description**

Define the audio stream volume mode.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL = 0 | Indicates this audio stream volume will be affected by system volume, also the default behavior.<br>**Since**: 19 |
| AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL = 1 | Indicates this audio stream volume will be affected by app's individual volume percentage which set by yourself using the app volume api.<br>**Since**: 19 |

### OH_AudioStream_LatencyType

```c
enum OH_AudioStream_LatencyType
```

**Description**

Defines audio latency types.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_LATENCY_TYPE_ALL = 0 | Type to get latency of all audio processing units, including software and hardware.<br>**Since**: 23 |
| AUDIOSTREAM_LATENCY_TYPE_SOFTWARE = 1 | Type to get latency of software part, including audio effects in software.<br>**Since**: 23 |
| AUDIOSTREAM_LATENCY_TYPE_HARDWARE = 2 | Type to get latency of hardware part, including audio effects in hal, driver and hardware.<br>**Since**: 23 |

### OH_AudioStream_PlaybackCaptureMode

```c
enum OH_AudioStream_PlaybackCaptureMode
```

**Description**

Defines mode for playback capture, each mode means different target streams to capture.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_DEFAULT = 0x0 | Default mode. Capture most of the audio streams, except tone streams and privacy streams.<br>**Since**: 23 |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_MEDIA = 0x1 | Media mode. Capture media, voice message and also unknown streams.<br>**Since**: 23 |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_EXCLUDING_SELF = 0x8000 | Excluding self mode. Capture streams excluding the audio played by application itself.<br>**Since**: 23 |

### OH_AudioStream_PlaybackCaptureStartState

```c
enum OH_AudioStream_PlaybackCaptureStartState
```

**Description**

Defines the playback capture start state, which is returned asynchronously after calling [OH_AudioCapturer_RequestPlaybackCaptureStart](capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart) function.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_SUCCESS = 0 | Start playback capture success state.<br>**Since**: 23 |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_FAILED = 1 | Start playback capture failed state, because the request for interrupt is denied or meet system internal error.<br>**Since**: 23 |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_NOT_AUTHORIZED = 2 | Start playback capture but user not authorized state.<br>**Since**: 23 |


## Function description

### OH_AudioRenderer_OutputDeviceChangeCallback()

```c
typedef void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)
```

**Description**

Callback when the output device of an audio renderer changed.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | AudioRenderer where this event occurs. |
| void* userData | User data which is passed by user. |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) reason | Indicates that why does the output device changes. |

### OH_AudioRenderer_OnMarkReachedCallback()

```c
typedef void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)
```

**Description**

Callback when the mark position reached.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | AudioRenderer where this event occurs. |
| uint32_t samplePos | Mark position in samples. |
| void* userData | User data which is passed by user. |

### OH_AudioRenderer_WriteDataWithMetadataCallback()

```c
typedef int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)
```

**Description**

This function pointer will point to the callback function that is used to write audio data with metadata

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | AudioRenderer where this event occurs. |
| void* userData | User data which is passed by user. |
| void* audioData | Audio data which is written by user. |
| int32_t audioDataSize | Audio data size which is the size of audio data written by user, unit is byte. |
| void* metadata | Metadata which is written by user. |
| int32_t metadataSize | Metadata size which is the size of metadata written by user, unit is byte. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Error code of the callback function returned by user. |

### OH_AudioRenderer_OnWriteDataCallback()

```c
typedef OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**Description**

Callback function of write data.<br> This function is similar with OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData instead of the return value. The return result of this function indicates whether the data filled in the buffer is valid or invalid. If result is invalid, the data filled by user will not be played.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | AudioRenderer where this callback occurs. |
| void* userData | User data which is passed by user. |
| void* audioData | Audio data pointer, where user should fill in audio data. |
| int32_t audioDataSize | Size of audio data that user should fill in, unit is byte. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioData_Callback_Result](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) | Audio Data callback result. |

**Reference**:

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData



