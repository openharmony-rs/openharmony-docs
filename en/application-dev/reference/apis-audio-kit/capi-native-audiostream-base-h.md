# native_audiostream_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=0fde25f631d3ee2fada3354f6774fda4f0572fb3 translatedAt=2026-11-03T04:06:14.166Z pushedAt=2026-11-04T03:11:46.966Z nl=1 -->

## Overview

The file declares the basic data structure of OHAudio.

**File to include**: <ohaudio/native_audiostream_base.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) | OH_AudioStreamInfo | Describes the audio stream information, which is used to describe the basic audio format.|
| [OH_AudioRenderer_Callbacks_Struct](capi-ohaudio-oh-audiorenderer-callbacks-struct.md) | OH_AudioRenderer_Callbacks | Describes a pointer to the callbacks related to an audio renderer. (It is deprecated in API version 20.)|
| [OH_AudioCapturer_Callbacks_Struct](capi-ohaudio-oh-audiocapturer-callbacks-struct.md) | OH_AudioCapturer_Callbacks | Describes a pointer to the callbacks related to an audio capturer.<br>To avoid unexpected behavior, ensure that every member variable of the struct is initialized by a custom callback method or a null pointer when setting the audio callback functions. (It is deprecated in API version 20.)|
| [OH_AudioStreamBuilderStruct](capi-ohaudio-oh-audiostreambuilderstruct.md) | OH_AudioStreamBuilder | Defines a struct for an audio stream builder. An audio stream builder instance is often used to create an audio stream and set its attributes.|
| [OH_AudioRendererStruct](capi-ohaudio-oh-audiorendererstruct.md) | OH_AudioRenderer | Describes an audio renderer, which is used to render audio data.|
| [OH_AudioCapturerStruct](capi-ohaudio-oh-audiocapturerstruct.md) | OH_AudioCapturer | Describes an audio capturer, which is used to capture audio data.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioStream_Result](#oh_audiostream_result) | OH_AudioStream_Result | Enumerates the audio operation results.|
| [OH_AudioStream_Type](#oh_audiostream_type) | OH_AudioStream_Type | Enumerates the audio stream types.|
| [OH_AudioStream_SampleFormat](#oh_audiostream_sampleformat) | OH_AudioStream_SampleFormat | Enumerates the sampling formats of audio streams.|
| [OH_AudioStream_EncodingType](#oh_audiostream_encodingtype) | OH_AudioStream_EncodingType | Enumerates the encoding types of audio streams.|
| [OH_AudioStream_Usage](#oh_audiostream_usage) | OH_AudioStream_Usage | Enumerates the usage scenarios of audio streams.<br> Generally, it is used to describe usage scenarios of audio output streams.|
| [OH_AudioStream_LatencyMode](#oh_audiostream_latencymode) | OH_AudioStream_LatencyMode | Enumerates the latency modes of audio streams.|
| [OH_AudioStream_DirectPlaybackMode](#oh_audiostream_directplaybackmode) | OH_AudioStream_DirectPlaybackMode | Enumerates the direct playback modes of audio streams.|
| [OH_AudioStream_VolumeMode](#oh_audiostream_volumemode) | OH_AudioStream_VolumeMode | Enumerates the volume modes of audio streams.|
| [OH_AudioStream_State](#oh_audiostream_state) | OH_AudioStream_State | Enumerates the audio stream states.|
| [OH_AudioStream_SourceType](#oh_audiostream_sourcetype) | OH_AudioStream_SourceType | Enumerates the usage scenarios of audio streams.<br> Generally, it is used to describe usage scenarios of audio input streams.|
| [OH_AudioStream_Event](#oh_audiostream_event) | OH_AudioStream_Event | Enumerates the audio stream events. (It is deprecated in API version 20.)|
| [OH_AudioInterrupt_ForceType](#oh_audiointerrupt_forcetype) | OH_AudioInterrupt_ForceType | Defines whether an audio interruption is forced by the system.<br> When the user monitors an audio interruption, the user will obtain this information.<br> This type represents whether the operation corresponding to the audio interruption hint [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) has been forced by the system. The specific operation information (such as audio pause and stop) can be obtained through [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint). Among them, the [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) corresponding to AUDIOSTREAM_INTERRUPT_HINT_RESUME must be AUDIOSTREAM_INTERRUPT_SHARE, that is, the resume operation cannot be forced by the system and must be triggered by the application. |
| [OH_AudioInterrupt_Hint](#oh_audiointerrupt_hint) | OH_AudioInterrupt_Hint | Enumerates the hints provided along with audio interruption.<br> The force type is obtained when an audio interruption event is received.<br> The hint specifies the operation (such as audio pause or volume adjustment) to be performed on audio streams based on the focus strategy.<br> You can combine the [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) information to determine whether the operation has been forcibly performed by the system.|
| [OH_AudioInterrupt_Mode](#oh_audiointerrupt_mode) | OH_AudioInterrupt_Mode | Enumerates the audio interruption modes.|
| [OH_AudioStream_AudioEffectMode](#oh_audiostream_audioeffectmode) | OH_AudioStream_AudioEffectMode | Enumerates the audio effect modes.|
| [OH_AudioStream_FastStatus](#oh_audiostream_faststatus) | OH_AudioStream_FastStatus | Enumerates the low-latency statuses.|
| [OH_AudioStream_DeviceChangeReason](#oh_audiostream_devicechangereason) | OH_AudioStream_DeviceChangeReason | Enumerates the reasons for audio stream device changes.|
| [OH_AudioStream_PrivacyType](#oh_audiostream_privacytype) | OH_AudioStream_PrivacyType | Enumerates the privacy types of an audio stream. The privacy type specifies whether the audio stream can be recorded by other applications.|
| [OH_AudioData_Callback_Result](#oh_audiodata_callback_result) | OH_AudioData_Callback_Result | Enumerates the audio data callback results.|
| [OH_AudioStream_LatencyType](#oh_audiostream_latencytype) | OH_AudioStream_LatencyType | Enumerates the audio latency types.|
| [OH_AudioStream_PlaybackCaptureMode](#oh_audiostream_playbackcapturemode) | OH_AudioStream_PlaybackCaptureMode | Indicates the filter type of playback capture (recording the sound of applications inside the device). Each filter type can record different playback stream types. This API is initially available only to specific system applications. Since API version 26.0.0, it supports use by any application. |
| [OH_AudioStream_PlaybackCaptureStartState](#oh_audiostream_playbackcapturestartstate) | OH_AudioStream_PlaybackCaptureStartState | Defines the start state of playback capture. This state is returned asynchronously after the [OH_AudioCapturer_RequestPlaybackCaptureStart](./capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart) function is called. This API is initially available only to specific system applications. Since API version 26.0.0, it supports use by any application. |

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)](#oh_audiorenderer_outputdevicechangecallback) | OH_AudioRenderer_OutputDeviceChangeCallback | Defines a pointer to the callback invoked when the audio capturer device changes.|
| [typedef void (\*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)](#oh_audiorenderer_onmarkreachedcallback) | OH_AudioRenderer_OnMarkReachedCallback | Defines a pointer to the callback invoked when the mark position is reached.|
| [typedef int32_t (\*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)](#oh_audiorenderer_writedatawithmetadatacallback) | OH_AudioRenderer_WriteDataWithMetadataCallback | Defines a function pointer to the callback used to write audio data and metadata.|
| [typedef OH_AudioData_Callback_Result (\*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)](#oh_audiorenderer_onwritedatacallback) | OH_AudioRenderer_OnWriteDataCallback | This function pointer will point to the callback function used to write audio data.<br> The callback function is used only to write audio data. Do not call AudioRenderer-related APIs in the callback function.<br> The return result of this function indicates whether the data filled into the buffer is valid. If the result is invalid, the data written by the user will not be played.<br> After the callback function ends, the audio service places the data pointed to by audioData into a queue for playback. Therefore, do not modify the data pointed to by audioData outside the callback, and ensure that audioData is filled with audioDataSize bytes of data to be played; otherwise, the audio service may play noise.<br> The audioDataSize parameter can be set through [OH_AudioStreamBuilder_SetFrameSizeInCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setframesizeincallback).<br> To avoid noise caused by discontinuous data when audio playback starts and stops, the system usually applies fade-in and fade-out processing of no more than 20 ms to the audio data at startup and shutdown. |

## Enum Description

### OH_AudioStream_Result

```c
enum OH_AudioStream_Result
```

**Description**

Enumerates the audio operation results.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_SUCCESS = 0 | Operation successful.|
| AUDIOSTREAM_ERROR_INVALID_PARAM = 1 | Invalid input parameter.|
| AUDIOSTREAM_ERROR_ILLEGAL_STATE = 2 | Invalid state.|
| AUDIOSTREAM_ERROR_SYSTEM = 3 | System error.|
| AUDIOSTREAM_ERROR_UNSUPPORTED_FORMAT = 4 | Unsupported audio format, such as unsupported encoding type or sampling format.<br>**Since**: 19|
| AUDIOSTREAM_ERROR_UNSUPPORTED_ABILITY = 6800104 | Unsupported audio stream capability, for example, unsupported function or configuration.<br>**Since:** 26.0.0 |
| AUDIOSTREAM_ERROR_SERVICE_DIED = 6800302 | The audio service process terminated abnormally.<br>**Since:** 26.0.0 |

### OH_AudioStream_Type

```c
enum OH_AudioStream_Type
```

**Description**

Enumerates the audio stream types.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_TYPE_RENDERER = 1 | The audio stream is an output stream.|
| AUDIOSTREAM_TYPE_CAPTURER = 2 | The audio stream is an input stream.|

### OH_AudioStream_SampleFormat

```c
enum OH_AudioStream_SampleFormat
```

**Description**

Enumerates the sampling formats of audio streams.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_SAMPLE_U8 = 0 | Unsigned 8-bit.|
| AUDIOSTREAM_SAMPLE_S16LE = 1 | Signed 16-bit little-endian. |
| AUDIOSTREAM_SAMPLE_S24LE = 2 | Signed 24-bit little-endian. |
| AUDIOSTREAM_SAMPLE_S32LE = 3 | Signed 32-bit little-endian. |
| AUDIOSTREAM_SAMPLE_F32LE = 4 | Float 32-bit little-endian.<br>**Since**: 17|

### OH_AudioStream_EncodingType

```c
enum OH_AudioStream_EncodingType
```

**Description**

Enumerates the encoding types of audio streams.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_ENCODING_TYPE_RAW = 0 | PCM encoding.|
| AUDIOSTREAM_ENCODING_TYPE_AUDIOVIVID = 1 | Audio Vivid encoding.<br>**Since**: 12|
| AUDIOSTREAM_ENCODING_TYPE_E_AC3 = 2 | E_AC3 encoding.<br>**Since**: 19|

### OH_AudioStream_Usage

```c
enum OH_AudioStream_Usage
```

**Description**

Enumerates the usage scenarios of audio streams.<br> that is, usage scenarios of audio output streams.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_USAGE_UNKNOWN = 0 | Unknown content.|
| AUDIOSTREAM_USAGE_MUSIC = 1 | Music.|
| AUDIOSTREAM_USAGE_VOICE_COMMUNICATION = 2 | VoIP voice call.|
| AUDIOSTREAM_USAGE_VOICE_ASSISTANT = 3 | Voice assistant.|
| AUDIOSTREAM_USAGE_ALARM = 4 | Alarming.|
| AUDIOSTREAM_USAGE_VOICE_MESSAGE = 5 | Voice message.|
| AUDIOSTREAM_USAGE_RINGTONE = 6 | Ringtone.|
| AUDIOSTREAM_USAGE_NOTIFICATION = 7 | Notification.|
| AUDIOSTREAM_USAGE_ACCESSIBILITY = 8 | Accessibility.|
| AUDIOSTREAM_USAGE_MOVIE = 10 | Movie or video.|
| AUDIOSTREAM_USAGE_GAME = 11 | Gaming.|
| AUDIOSTREAM_USAGE_AUDIOBOOK = 12 | Audiobooks (including crosstalks and storytelling), news radio, and podcasts.|
| AUDIOSTREAM_USAGE_NAVIGATION = 13 | Navigation.|
| AUDIOSTREAM_USAGE_VIDEO_COMMUNICATION = 17 | VoIP video call.<br>**Since**: 12|

### OH_AudioStream_LatencyMode

```c
enum OH_AudioStream_LatencyMode
```

**Description**

Enumerates the latency modes of audio streams.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_LATENCY_MODE_NORMAL = 0 | Normal latency mode.|
| AUDIOSTREAM_LATENCY_MODE_FAST = 1 | Low latency mode.|

### OH_AudioStream_DirectPlaybackMode

```c
enum OH_AudioStream_DirectPlaybackMode
```

**Description**

Enumerates the direct playback modes of audio streams.

**Since**: 19

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_DIRECT_PLAYBACK_NOT_SUPPORTED = 0 | Direct playback is not supported.|
| AUDIOSTREAM_DIRECT_PLAYBACK_BITSTREAM_SUPPORTED = 1 | Direct playback of bit streams (without decoding) is supported.|
| AUDIOSTREAM_DIRECT_PLAYBACK_PCM_SUPPORTED = 2 | This mode represents direct path playback that supports PCM encoding. |

### OH_AudioStream_VolumeMode

```c
enum OH_AudioStream_VolumeMode
```

**Description**

Enumerates the volume modes of audio streams.

**Since**: 19

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_VOLUMEMODE_SYSTEM_GLOBAL = 0 | System-level volume (default mode).|
| AUDIOSTREAM_VOLUMEMODE_APP_INDIVIDUAL = 1 | Application-level volume.<br> In this mode, you can set and query the application volume through the provided functions.|

### OH_AudioStream_State

```c
enum OH_AudioStream_State
```

**Description**

Enumerates the audio stream states.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_STATE_INVALID = -1 | Invalid state.|
| AUDIOSTREAM_STATE_NEW = 0 | Newly created.|
| AUDIOSTREAM_STATE_PREPARED = 1 | Prepared.|
| AUDIOSTREAM_STATE_RUNNING = 2 | Running.|
| AUDIOSTREAM_STATE_STOPPED = 3 | Stopped.|
| AUDIOSTREAM_STATE_RELEASED = 4 | Released.|
| AUDIOSTREAM_STATE_PAUSED = 5 | Paused.|

### OH_AudioStream_SourceType

```c
enum OH_AudioStream_SourceType
```

**Description**

Enumerates the usage scenarios of audio streams,<br> that is, usage scenarios of audio input streams.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_SOURCE_TYPE_INVALID = -1 | Invalid state.|
| AUDIOSTREAM_SOURCE_TYPE_MIC = 0 | Audio recording.|
| AUDIOSTREAM_SOURCE_TYPE_VOICE_RECOGNITION = 1 | Voice recognition.|
| AUDIOSTREAM_SOURCE_TYPE_PLAYBACK_CAPTURE = 2 | Audio playback.<br>**Deprecated from**: 12<br>**Substitute**: [OH_AVScreenCapture](../apis-media-kit/capi-avscreencapture-oh-avscreencapture.md)|
| AUDIOSTREAM_SOURCE_TYPE_VOICE_COMMUNICATION = 7 | Voice communication.|
| AUDIOSTREAM_SOURCE_TYPE_VOICE_MESSAGE = 10 | Voice message.<br>**Since**: 12|
| AUDIOSTREAM_SOURCE_TYPE_CAMCORDER = 13 | Video recording.<br>**Since**: 13|
| AUDIOSTREAM_SOURCE_TYPE_UNPROCESSED = 14 | Raw microphone recording, where the system does not perform any algorithm processing.<br>**Since**: 14|
| AUDIOSTREAM_SOURCE_TYPE_LIVE = 17 | Live.<br>**Since**: 20|
| AUDIOSTREAM_SOURCE_TYPE_VOICE_DOWNLINK = 22 | Cellular call downlink recording (the voice of the other party during a call). The audio capturer using this input stream should be created after the cellular call starts. When [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer) is used to create the capture stream, the ohos.permission.CAPTURE_PLAYBACK_DOWNLINK permission is required; otherwise, the function returns an error.<br>**Since:** 26.0.0 |

### OH_AudioStream_Event

```c
enum OH_AudioStream_Event
```

**Description**

Enumerates the audio stream events.

**Since**: 10

**Deprecated from**: 20

**Substitute**: [OH_AudioRenderer_OutputDeviceChangeCallback](capi-native-audiostream-base-h.md#oh_audiorenderer_outputdevicechangecallback)

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_EVENT_ROUTING_CHANGED = 0 | The audio route has been changed.|

### OH_AudioInterrupt_ForceType

```c
enum OH_AudioInterrupt_ForceType
```

**Description**

Defines whether an audio interruption is forced by the system.<br> When a user monitors and hears an audio interruption, the user will obtain this information.<br> This type represents whether the operation corresponding to the audio interruption hint [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) has been forced by the system. The specific operation information (such as audio pause and stop) can be obtained through [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint). Among them, the [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) corresponding to AUDIOSTREAM_INTERRUPT_HINT_RESUME must be AUDIOSTREAM_INTERRUPT_SHARE, that is, the resume operation cannot be forced by the system and must be triggered by the application itself.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_INTERRUPT_FORCE = 0 | Forced execution type, that is, the corresponding operation indicated by the interrupt hint [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint) has been forced by the system. |
| AUDIOSTREAM_INTERRUPT_SHARE = 1 | Non-forced execution type, that is, the system does not execute the corresponding operation but only prompts the application through [OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint), and the application can decide the next processing method on its own. |

### OH_AudioInterrupt_Hint

```c
enum OH_AudioInterrupt_Hint
```

**Description**

Enumerates the hints provided along with audio interruption.<br> The force type is obtained when an audio interruption event is received.<br> The hint specifies the operation (such as audio pause or volume adjustment) to be performed on audio streams based on the focus strategy.<br> You can combine the [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) information to determine whether the operation has been forcibly performed by the system.

**Since**: 10

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_INTERRUPT_HINT_NONE = 0 | None.|
| AUDIOSTREAM_INTERRUPT_HINT_RESUME = 1 | A hint is displayed, indicating that the audio stream is restored. The application can proactively trigger operations related to rendering or recording.<br> This operation cannot be forcibly performed by the system. The corresponding [OH_AudioInterrupt_ForceType](capi-native-audiostream-base-h.md#oh_audiointerrupt_forcetype) must be **AUDIOSTREAM_INTERRUPT_SHARE**.|
| AUDIOSTREAM_INTERRUPT_HINT_PAUSE = 2 | A hint is displayed, indicating that the audio stream is paused and the audio focus is lost temporarily.<br> The **AUDIOSTREAM_INTERRUPT_HINT_RESUME** event will be triggered when the focus is gained.|
| AUDIOSTREAM_INTERRUPT_HINT_STOP = 3 | A hint is displayed, indicating that the audio stream stops and the audio focus is lost.|
| AUDIOSTREAM_INTERRUPT_HINT_DUCK = 4 | A hint is displayed, indicating that audio ducking starts and the audio is played at a lower volume.|
| AUDIOSTREAM_INTERRUPT_HINT_UNDUCK = 5 | A hint is displayed, indicating that audio ducking ends and the audio is played at the normal volume.|
| AUDIOSTREAM_INTERRUPT_HINT_MUTE = 6 | A hint is displayed, indicating that the audio is muted.<br>**Since**: 20|
| AUDIOSTREAM_INTERRUPT_HINT_UNMUTE = 7 | A hint is displayed, indicating that the audio is unmuted.<br>**Since**: 20|

### OH_AudioInterrupt_Mode

```c
enum OH_AudioInterrupt_Mode
```

**Description**

Enumerates the audio interruption modes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_INTERRUPT_MODE_SHARE = 0 | Shared mode.|
| AUDIOSTREAM_INTERRUPT_MODE_INDEPENDENT = 1 | Independent mode.|

### OH_AudioStream_AudioEffectMode

```c
enum OH_AudioStream_AudioEffectMode
```

**Description**

Enumerates the audio effect modes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| EFFECT_NONE = 0 | No audio effect used.|
| EFFECT_DEFAULT = 1 | Default audio effect mode.|

### OH_AudioStream_FastStatus

```c
enum OH_AudioStream_FastStatus
```

**Description**

Enumerates the low-latency statuses.

**Since**: 20

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_FASTSTATUS_NORMAL = 0 | Normal audio stream status.|
| AUDIOSTREAM_FASTSTATUS_FAST = 1 | Low-latency audio stream status.|

### OH_AudioStream_DeviceChangeReason

```c
enum OH_AudioStream_DeviceChangeReason
```

**Description**

Enumerates the reasons for audio stream device changes.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| REASON_UNKNOWN = 0 | Unknown reason.|
| REASON_NEW_DEVICE_AVAILABLE = 1 | A new device is available. For example, a wired or Bluetooth headset is connected during audio playback. |
| REASON_OLD_DEVICE_UNAVAILABLE = 2 | The old device is unavailable. For example, a wired or Bluetooth headset is disconnected during audio playback. When this reason is reported, the application should consider pausing audio playback. |
| REASON_OVERRODE = 3 | The user or system forces a device switch. For example, a device is forcibly selected in the playback control center. |
| REASON_SESSION_ACTIVATED = 4 | Device switch triggered by activating an audio session in [Audio Session Management (ArkTS)](../../media/audio/audio-session-management.md).<br>**Since:** 20 |
| REASON_STREAM_PRIORITY_CHANGED = 5 | System device switch caused by the appearance of a higher-priority audio stream. For example, when a call comes in during music playback, the call stream has a higher priority, causing the music device to be switched.<br>**Since:** 20 |

### OH_AudioStream_PrivacyType

```c
enum OH_AudioStream_PrivacyType
```

**Description**

Enumerates the privacy types of an audio stream. The privacy type specifies whether the audio stream can be recorded by other applications.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_STREAM_PRIVACY_TYPE_PUBLIC = 0 | The audio stream can be recorded or screen-projected by other applications and is not privacy-related.|
| AUDIO_STREAM_PRIVACY_TYPE_PRIVATE = 1 | The audio stream cannot be recorded or screen-projected by other applications.|
| AUDIO_STREAM_PRIVACY_TYPE_SHARED = 2 | The audio stream can be recorded or screen-projected by other applications and is privacy-related.<br>     For example, if the privacy policy is **PRIVACY_TYPE_PUBLIC**, the [AUDIOSTREAM_USAGE_VOICE_COMMUNICATION](capi-native-audiostream-base-h.md#oh_audiostream_usage) audio stream cannot be recorded or screen-projected by other applications. However, if the privacy policy is **PRIVACY_TYPE_SHARED**, these audio streams can be recorded or screen-projected by other applications.<br>**Since**: 21|

### OH_AudioData_Callback_Result

```c
enum OH_AudioData_Callback_Result
```

**Description**

Enumerates the audio data callback results.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DATA_CALLBACK_RESULT_INVALID = -1 | The audio data callback result is invalid, and the audio data will not be played.|
| AUDIO_DATA_CALLBACK_RESULT_VALID = 0 | The audio data callback result is valid, and the audio data will be played.|

### OH_AudioStream_LatencyType

```c
enum OH_AudioStream_LatencyType
```

**Description**

Enumerates the audio latency types.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_LATENCY_TYPE_ALL = 0 | Obtains the overall audio processing latency for both software and hardware components.|
| AUDIOSTREAM_LATENCY_TYPE_SOFTWARE = 1 | Obtains the software latency, including latency for sound effect processing on the software side.|
| AUDIOSTREAM_LATENCY_TYPE_HARDWARE = 2 | Obtains the latency of the hardware part, including the Hardware Abstraction Layer (HAL), driver, and hardware-side audio effect processing. |

### OH_AudioStream_PlaybackCaptureMode

```c
enum OH_AudioStream_PlaybackCaptureMode
```

**Description**

Indicates the filter type of playback capture (recording the sound of applications inside the device). Each filter type can record different playback stream types. This API is initially only available to specific system applications. Starting from API version 26.0.0, it supports use by any application.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_DEFAULT = 0x0 | Default mode. Most audio streams are recorded, excluding the prompt streams and privacy streams.<br>**Since**: 23|
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_MEDIA = 0x1 | Media mode. Media, voice messages, and unknown streams are retrieved.<br>**Since**: 23|
| AUDIOSTREAM_PLAYBACKCAPTURE_MODE_EXCLUDING_SELF = 0x8000 | Self-exclusion mode. All audio streams except for those played by the application itself are retrieved.<br>**Since**: 23|

### OH_AudioStream_PlaybackCaptureStartState

```c
enum OH_AudioStream_PlaybackCaptureStartState
```

**Description**

Defines the start state of playback capture. This state is returned asynchronously after the [OH_AudioCapturer_RequestPlaybackCaptureStart](./capi-native-audiocapturer-h.md#oh_audiocapturer_requestplaybackcapturestart) function is called. This API is initially only available to specific system applications. Starting from API version 26.0.0, it supports use by any application.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_SUCCESS = 0 | Internal audio recording is started successfully.<br>**Since**: 23|
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_FAILED = 1 | Internal audio recording fails to be started. The focus request (prioritized by stream type) is interrupted or an internal system error occurs.<br>**Since**: 23|
| AUDIOSTREAM_PLAYBACKCAPTURE_START_STATE_NOT_AUTHORIZED = 2 | Internal audio recording fails to be started due to lack of user authorization.<br>**Since**: 23|


## Function Description

### OH_AudioRenderer_OutputDeviceChangeCallback()

```c
typedef void (*OH_AudioRenderer_OutputDeviceChangeCallback)(OH_AudioRenderer* renderer, void* userData, OH_AudioStream_DeviceChangeReason reason)
```

**Description**

Defines a pointer to the callback invoked when the audio capturer device changes.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  void* userData | Pointer to the application data passed through the callback.|
| [OH_AudioStream_DeviceChangeReason](#oh_audiostream_devicechangereason) reason | Enumerates the reasons for audio stream device changes.|

### OH_AudioRenderer_OnMarkReachedCallback()

```c
typedef void (*OH_AudioRenderer_OnMarkReachedCallback)(OH_AudioRenderer* renderer, uint32_t samplePos, void* userData)
```

**Description**

Defines a pointer to the callback invoked when the mark position is reached.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  uint32_t samplePos | Mark position.|
|  void* userData | Pointer to the application data passed through the callback.|

### OH_AudioRenderer_WriteDataWithMetadataCallback()

```c
typedef int32_t (*OH_AudioRenderer_WriteDataWithMetadataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize, void* metadata, int32_t metadataSize)
```

**Description**

Defines a function pointer to the callback used to write audio data and metadata.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  void* userData | Pointer to the application data passed through the callback.|
|  void* audioData | Pointer to the audio data written by the user.|
|  int32_t audioDataSize | Length of the audio data, in bytes.|
|  void* metadata | Pointer to the metadata written by the user.|
|  int32_t metadataSize | Length of the metadata, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code of the callback.|

### OH_AudioRenderer_OnWriteDataCallback()

```c
typedef OH_AudioData_Callback_Result (*OH_AudioRenderer_OnWriteDataCallback)(OH_AudioRenderer* renderer, void* userData, void* audioData, int32_t audioDataSize)
```

**Description**

This function pointer will point to the callback function used to write audio data.<br> The callback function is only used to write audio data. Do not call AudioRenderer-related APIs in the callback function.<br> The return result of this function indicates whether the data filled into the buffer is valid. If the result is invalid, the data filled by the user will not be played.<br> After the callback function ends, the audio service will place the data pointed to by audioData into the queue to wait for playback. Therefore, do not modify the data pointed to by audioData again outside the callback, and ensure that audioData is filled with audioDataSize bytes of data to be played. Otherwise, the audio service may play noise.<br> The parameter audioDataSize can be set through [OH_AudioStreamBuilder_SetFrameSizeInCallback](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_setframesizeincallback).<br> To avoid noise that may be caused by discontinuous data when audio playback starts and stops, the system usually performs fade-in and fade-out processing on the audio data within 20 ms at startup and shutdown.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | Pointer to an audio renderer instance, which is created by calling [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer).|
|  void* userData | Pointer to the application data passed through the callback.|
|  void* audioData | Pointer to the audio data written by the user.|
|  int32_t audioDataSize | Length of the audio data, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioData_Callback_Result](capi-native-audiostream-base-h.md#oh_audiodata_callback_result) | **AUDIO_DATA_CALLBACK_RESULT_INVALID**: The audio data callback result is invalid, and the audio data will not be played.<br>         **AUDIO_DATA_CALLBACK_RESULT_VALID**: The audio data callback result is valid, and the audio data will be played.|


