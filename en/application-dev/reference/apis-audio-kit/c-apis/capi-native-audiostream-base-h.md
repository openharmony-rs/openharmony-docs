# native_audiostream_base.h

## Overview

Declare the underlying data structure.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) | OH_AudioStreamInfo | Define the audio stream info structure, used to describe basic audio format. |
| [OH_AudioRenderer_Callbacks_Struct](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) | OH_AudioRenderer_Callbacks | Declaring the callback struct for renderer stream. |
| [OH_AudioCapturer_Callbacks_Struct](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) | OH_AudioCapturer_Callbacks | Declaring the callback struct for capturer stream. |
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

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)](#oh_audiorenderer_outputdevicechangecallback) | OH_AudioRenderer_OutputDeviceChangeCallback | Callback when the output device of an audio renderer changed. |
| [typedef void (\*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)](#oh_audiorenderer_onmarkreachedcallback) | OH_AudioRenderer_OnMarkReachedCallback | Callback when the mark position reached. |
| [typedef int32_t (\*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)](#oh_audiorenderer_writedatawithmetadatacallback) | OH_AudioRenderer_WriteDataWithMetadataCallback | This function pointer will point to the callback function that is used to write audio data with metadata |
| [typedef OH_AudioData_Callback_Result (\*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallback) | OH_AudioRenderer_OnWriteDataCallback | Callback function of write data.<br> This function is similar with OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData instead of the return value. The return result of this function indicates whether the data filled in the buffer is valid or invalid. If result is invalid, the data filled by user will not be played. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason) | Callback when the output device of an audio renderer changed.<br>**Since**: 11 |
| void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData) | Callback when the mark position reached.<br>**Since**: 12 |
| int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize) | This function pointer will point to the callback function that is used to write audio data with metadata<br>**Since**: 12 |
| OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize) | Callback function of write data.<br> This function is similar with OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData instead of the return value. The return result of this function indicates whether the data filled in the buffer is valid or invalid. If result is invalid, the data filled by user will not be played.<br>**Since**: 12 |

## Enum type description

### OH_AudioStream_Result

```c
enum OH_AudioStream_Result
```

**Description**

Define the result of the function execution.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_SUCCESS = 0 |  The call was successful.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_INVALID_PARAM = 1 |  This means that the function was executed with an invalid input parameter.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_ILLEGAL_STATE = 2 |  Execution status exception.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_SYSTEM = 3 |  An system error has occurred.<br>**Since**: 10 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_FORMAT = 4 |  Unsupported audio format, such as unsupported encoding type, sample format etc.<br>**Since**: 19 |
| AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY = 6800104 |  Unsupported audio stream ability, including function and configuration.<br>**Since**: 26.0.0 |
| AUDIOSTREAM_ERROR_SERVICE_DIED = 6800302 |  Audio server process died.<br>**Since**: 26.0.0 |

### OH_AudioStream_Type

```c
enum OH_AudioStream_Type
```

**Description**

Define the audio stream type.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_TYPE_RENDERER = 1 |  |
| AUDIOSTREAM_TYPE_CAPTURER = 2 |  |

### OH_AudioStream_SampleFormat

```c
enum OH_AudioStream_SampleFormat
```

**Description**

Define the audio stream sample format.

**Since**: 10

| Enum item | Description |
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

**Description**

Define the audio encoding type.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_ENCODING_TYPE_RAW = 0 |  |
| AUDIOSTREAM_ENCODING_TYPE_AUDIOVIVID = 1 |  |
| AUDIOSTREAM_ENCODING_TYPE_E_AC3 = 2 |  |

### OH_AudioStream_Usage

```c
enum OH_AudioStream_Usage
```

**Description**

Define the audio stream usage. Audio stream usage is used to describe what work scenario the current stream is used for.

**Since**: 10

| Enum item | Description |
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

**Description**

Define the audio latency mode.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_LATENCY_MODE_NORMAL = 0 |  |
| AUDIOSTREAM_LATENCY_MODE_FAST = 1 |  |

### OH_AudioStream_DirectPlaybackMode

```c
enum OH_AudioStream_DirectPlaybackMode
```

**Description**

Enumerates audio direct playback modes.

**Since**: 19

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_DIRECT_PLAYBACK_NOT_SUPPORTED = 0 |  |
| AUDIOSTREAM_DIRECT_PLAYBACK_BITSTREAM_SUPPORTED = 1 |  |
| AUDIOSTREAM_DIRECT_PLAYBACK_PCM_SUPPORTED = 2 |  |

### OH_AudioStream_Event

```c
enum OH_AudioStream_Event
```

**Description**

Define the audio event.

**Since**: 10

**Deprecated**: 20

**Replaced by**: OH_AudioRenderer_OutputDeviceChangeCallback.

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_EVENT_ROUTING_CHANGED = 0 |  |

### OH_AudioStream_State

```c
enum OH_AudioStream_State
```

**Description**

The audio stream states

**Since**: 10

| Enum item | Description |
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

**Description**

Defines the audio interrupt type.

**Since**: 10

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_INTERRUPT_FORCE = 0 |  |
| AUDIOSTREAM_INTERRUPT_SHARE = 1 |  |

### OH_AudioInterrupt_Hint

```c
enum OH_AudioInterrupt_Hint
```

**Description**

Defines the audio interrupt hint type.

**Since**: 10

| Enum item | Description |
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

**Description**

Defines the audio source type.

**Since**: 10

| Enum item | Description |
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

**Description**

Defines the audio interrupt mode.

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

**Since**: 12

| Enum item | Description |
| -- | -- |
| EFFECT_NONE = 0 |  |
| EFFECT_DEFAULT = 1 |  |

### OH_AudioStream_FastStatus

```c
enum OH_AudioStream_FastStatus
```

**Description**

Defines the fast status.

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

**Since**: 11

| Enum item | Description |
| -- | -- |
| REASON_UNKNOWN = 0 | Unknown. |
| REASON_NEW_DEVICE_AVAILABLE = 1 | New Device available. |
| REASON_OLD_DEVICE_UNAVAILABLE = 2 | Old Device unavailable. Applications should consider to pause the audio playback when this reason is |
| REASON_OVERRODE = 3 | Device is overrode by user or system. |
| REASON_SESSION_ACTIVATED = 4 | Device information when the audio session is activated.<br>**Since**: 20 |
| REASON_STREAM_PRIORITY_CHANGED = 5 | There is a higher-priority stream, causing the system device to change.<br>**Since**: 20 |

### OH_AudioStream_PrivacyType

```c
enum OH_AudioStream_PrivacyType
```

**Description**

Defines Enumeration of audio stream privacy type for playback capture.

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_STREAM_PRIVACY_TYPE_PUBLIC = 0 |  |
| AUDIO_STREAM_PRIVACY_TYPE_PRIVATE = 1 |  |
| AUDIO_STREAM_PRIVACY_TYPE_SHARED = 2 |  |

### OH_AudioData_Callback_Result

```c
enum OH_AudioData_Callback_Result
```

**Description**

Defines enumeration of audio data callback result.

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

**Since**: 19

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL = 0 |  |
| AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL = 1 |  |

### OH_AudioStream_LatencyType

```c
enum OH_AudioStream_LatencyType
```

**Description**

Defines audio latency types.

**Since**: 23

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_LATENCY_TYPE_ALL = 0 |  |
| AUDIOSTREAM_LATENCY_TYPE_SOFTWARE = 1 |  |
| AUDIOSTREAM_LATENCY_TYPE_HARDWARE = 2 |  |

### OH_AudioStream_PlaybackCaptureMode

```c
enum OH_AudioStream_PlaybackCaptureMode
```

**Description**

Defines mode for playback capture, each mode means different target streams to capture.

**Since**: 23

| Enum item | Description |
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_DEFAULT = 0x0 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_MEDIA = 0x1 |  |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_EXCLUDING_SELF = 0x8000 |  |


## Function description

### OH_AudioRenderer_OutputDeviceChangeCallback()

```c
typedef void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)
```

**Description**

Callback when the output device of an audio renderer changed.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)\* renderer | AudioRenderer where this event occurs. |
| void\* userData | User data which is passed by user. |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) reason | Indicates that why does the output device changes. |

### OH_AudioRenderer_OnMarkReachedCallback()

```c
typedef void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)
```

**Description**

Callback when the mark position reached.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)\* renderer | AudioRenderer where this event occurs. |
| uint32_t samplePos | Mark position in samples. |
| void\* userData | User data which is passed by user. |

### OH_AudioRenderer_WriteDataWithMetadataCallback()

```c
typedef int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)
```

**Description**

This function pointer will point to the callback function that is used to write audio data with metadata

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)\* renderer | AudioRenderer where this event occurs. |
| void\* userData | User data which is passed by user. |
| void\* audioData | Audio data which is written by user. |
| int32_t audioDataSize | Audio data size which is the size of audio data written by user, unit is byte. |
| void\* metadata | Metadata which is written by user. |
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

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)\* renderer | AudioRenderer where this callback occurs. |
| void\* userData | User data which is passed by user. |
| void\* audioData | Audio data pointer, where user should fill in audio data. |
| int32_t audioDataSize | Size of audio data that user should fill in, unit is byte. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioData_Callback_Result](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) | Audio Data callback result. |

**Reference**:

OH_AudioRenderer_Callbacks_Struct.OH_AudioRenderer_OnWriteData



