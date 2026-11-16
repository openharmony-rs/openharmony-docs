# native_audio_stream_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1ff9e9cd1ebb6561090ad32be99073f8301559bf translatedAt=2026-11-09T10:24:51.528Z pushedAt=2026-11-09T11:26:14.032Z nl=1 -->

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
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) | OH_AudioStreamManager | Declares the audio stream manager, which is used to manage audio stream related functions. |

### Function

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)](#oh_audiomanager_getaudiostreammanager) | Obtains the audio stream manager handle. |
| [OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)](#oh_audiostreammanager_getdirectplaybacksupport) | Obtains the direct playback mode through a route supported by the current audio stream. |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)](#oh_audiostreammanager_isacousticechocancelersupported) | Queries whether the specified recording stream type usage scenario supports acoustic echo cancellation. |
| [bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isfastplaybacksupported) | Queries whether the current device supports low-latency playback for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isfastrecordingsupported) | Queries whether the current device supports low-latency recording for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isintelligentnoisereductionenabledforcurrentdevice) | Queries whether intelligent noise reduction is enabled for the specified recording stream type. |
| [bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_ismultichannelplaybacksupported) | Queries whether the current device supports multichannel playback for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isdirectplaybacksupported) | Queries whether the current device supports direct playback for the specified audio stream information and usage scenario. |
| [bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isoffloadplaybacksupported) | Queries whether the current device supports low-power playback for the specified audio stream information and usage scenario. |

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

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS = 0: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM = 6800301: system state error. |

### OH_AudioStreamManager_GetDirectPlaybackSupport()

```c
OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)
```

**Description**

Obtains the direct playback mode through a route supported by the current audio stream.

**Since**: 19

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *audioStreamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario. |
| [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode) *directPlaybackMode | Pointer to [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode), used to obtain the direct playback mode through a route supported by the current audio stream. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS = 0: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101:<br>                                                        1. The parameter audioStreamManager is nullptr;<br>                                                        2. The parameter streamInfo is nullptr;<br>                                                        3. The parameter usage is invalid;<br>                                                        4. The parameter directPlaybackMode is nullptr. |

### OH_AudioStreamManager_IsAcousticEchoCancelerSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)
```

**Description**

Queries whether the specified recording stream type usage scenario supports acoustic echo cancellation.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | Usage scenario of the specified audio input stream. |
| bool *supported | Pointer to the parameter indicating whether the specified source type supports acoustic echo cancellation. The value **true** indicates that acoustic echo cancellation is supported, and **false** indicates that it is not supported. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>          AUDIOCOMMON_RESULT_SUCCESS = 0: the function is executed successfully.<br>          AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM = 6800101:<br>                                                    1. The parameter audioStreamManager is nullptr;<br>                                                    2. The parameter sourceType is invalid;<br>                                                    3. The parameter supported is nullptr. |

### OH_AudioStreamManager_IsFastPlaybackSupported()

```c
bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports low-latency playback for the specified audio stream information and usage scenario.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario. |

**Returns**

| Type | Description |
| -- | -- |
| bool | true if low-latency playback is supported; false otherwise. |

### OH_AudioStreamManager_IsFastRecordingSupported()

```c
bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)
```

**Description**

Queries whether the current device supports low-latency recording for the specified audio stream information and usage scenario.

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer. |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | Audio stream usage scenario. |

**Returns**

| Type | Description |
| -- | -- |
| bool | true indicates that low-latency recording is supported, and false indicates the opposite. |

### OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice()

```c
bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)
```

**Description**

Queries whether intelligent noise reduction is enabled for the specified recording stream type.

**Since:** 21

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | Audio stream usage scenario determined based on the audio device and pipeline type selection result. |

**Returns**

| Type | Description |
| -- | -- |
| bool | true indicates that the intelligent noise reduction switch is enabled, and false indicates that the switch is disabled. |

### OH_AudioStreamManager_IsMultichannelPlaybackSupported()

```c
bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports multichannel playback for the specified audio stream information and usage scenario.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer, used to describe the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, used to determine the selection result of the audio device and route type. |

**Returns**

| Type | Description |
| -- | -- |
| bool | Returns true if multichannel playback is supported, and false otherwise. |

### OH_AudioStreamManager_IsDirectPlaybackSupported()

```c
bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports direct playback for the specified audio stream information and usage scenario.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer, used to describe the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, used to determine the selection result of the audio device and route type. |

**Returns**

| Type | Description |
| -- | -- |
| bool | The value**true** indicates that direct playback is supported, and **false** indicates the opposite. |

### OH_AudioStreamManager_IsOffloadPlaybackSupported()

```c
bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Queries whether the current device supports low-power playback for the specified audio stream information and usage scenario.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | Audio stream manager handle. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | Audio stream information pointer, used to describe the basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage scenario, used to determine the selection result of the audio device and route type. |

**Returns**

| Type | Description |
| -- | -- |
| bool | true if low-power playback is supported; false otherwise. |


