# native_audio_stream_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1ff9e9cd1ebb6561090ad32be99073f8301559bf translatedAt=2026-11-10T03:06:04.682Z pushedAt=2026-11-10T04:43:00.649Z nl=1 -->

## Overview

Declares the APIs related to the audio stream manager.<br> The APIs in this file are used to create an AudioStreamManager and to set and manage audio streams.

**File to include:** <ohaudio/native_audio_stream_manager.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) | OH_AudioStreamManager | Declares an audio stream manager, which is used to manage audio streams. |

### Functions

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)](#oh_audiomanager_getaudiostreammanager) | Obtains the audio stream manager handle. |
| [OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)](#oh_audiostreammanager_getdirectplaybacksupport) | Obtains the direct path playback mode supported by the current audio stream. |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)](#oh_audiostreammanager_isacousticechocancelersupported) | Checks whether acoustic echo cancellation is supported for the specified recording stream type usage scenario. |
| [bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isfastplaybacksupported) | Checks whether low-latency playback is supported on the current device for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isfastrecordingsupported) | Checks whether low-latency recording is supported on the current device for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isintelligentnoisereductionenabledforcurrentdevice) | Checks whether intelligent noise reduction is enabled for the specified recording stream type. |
| [bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_ismultichannelplaybacksupported) | Checks whether multichannel playback is supported on the current device for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isdirectplaybacksupported) | Checks whether direct playback is supported on the current device for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isoffloadplaybacksupported) | Checks whether offload playback is supported on the current device for the specified audio stream information and usage scenario. |

## Function Description

### OH_AudioManager_GetAudioStreamManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)
```

**Description**

Obtains the audio stream manager handle.

**Since**: 19

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) **streamManager | Audio stream manager handle. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS = 0: function execution success.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301: system state error. |

### OH_AudioStreamManager_GetDirectPlaybackSupport()

```c
OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)
```

**Description**

Obtains the direct path playback mode supported by the current audio stream.

**Since**: 19

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *audioStreamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario. |
| [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode) *directPlaybackMode | Pointer to [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode), used to obtain the direct path playback mode supported by the current audio stream. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS = 0: function execution success.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101:<br>                                                        1. The audioStreamManager parameter is nullptr;<br>                                                        2. The streamInfo parameter is nullptr;<br>                                                        3. The usage parameter is invalid;<br>                                                        4. The directPlaybackMode parameter is nullptr. |

### OH_AudioStreamManager_IsAcousticEchoCancelerSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)
```

**Description**

Queries whether acoustic echo cancellation is supported for the specified recording stream usage scenario.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Pointer to the audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | Usage scenario of the specified audio input stream. |
| bool *supported | Pointer to the result indicating whether acoustic echo cancellation is supported for the specified source type. true indicates that acoustic echo cancellation is supported, and false indicates that it is not supported. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>          Returns AUDIOCOMMON_RESULT_SUCCESS = 0 if the function is executed successfully.<br>          Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101 if:<br>                                                    1. the audioStreamManager parameter is nullptr;<br>                                                    2. the sourceType parameter is invalid;<br>                                                    3. the supported parameter is nullptr. |

### OH_AudioStreamManager_IsFastPlaybackSupported()

```c
bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Checks whether low-latency playback is supported for the current device under the specific audio stream information and usage scenario.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario. |

**Return**

| Type | Description |
| -- | -- |
| bool | true indicates that low-latency playback is supported, and false indicates that it is not supported. |

### OH_AudioStreamManager_IsFastRecordingSupported()

```c
bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)
```

**Description**

Queries whether low latency recording is supported for the current device under specific audio stream information and usage scenario.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | Audio stream usage scenario. |

**Return**

| Type | Description |
| -- | -- |
| bool | true indicates that low latency recording is supported, and false indicates that it is not supported. |

### OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice()

```c
bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)
```

**Description**

Queries whether the intelligent noise reduction switch is enabled for the specified recording stream type.

**Since**: 21

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | Audio stream usage scenario derived from the selection result based on the audio device and path type. |

**Return**

| Type | Description |
| -- | -- |
| bool | true indicates that the intelligent noise reduction switch is enabled, and false indicates that it is disabled. |

### OH_AudioStreamManager_IsMultichannelPlaybackSupported()

```c
bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Checks whether multichannel playback is supported on the current device for the specific audio stream information and usage scenario.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Pointer to the audio stream information, which describes the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return**

| Type | Description |
| -- | -- |
| bool | true indicates that multichannel playback is supported, and false indicates that it is not supported. |

### OH_AudioStreamManager_IsDirectPlaybackSupported()

```c
bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports direct playback under specific audio stream information and usage scenario.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Pointer to the audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Pointer to the audio stream information, which describes the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return**

| Type | Description |
| -- | -- |
| bool | The value **true** indicates that direct playback is supported, and the value **false** indicates the opposite. |

### OH_AudioStreamManager_IsOffloadPlaybackSupported()

```c
bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports offload playback under specific audio stream information and usage scenario.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Pointer to the audio stream information, which is used to describe the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, which determines the audio device and path type selection. |

**Return**

| Type | Description |
| -- | -- |
| bool | true indicates support for offload playback, and false indicates not supported. |


