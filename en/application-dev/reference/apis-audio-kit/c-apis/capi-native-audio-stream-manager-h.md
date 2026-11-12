# native_audio_stream_manager.h

## Overview

Declare audio stream manager related interfaces.<br> This file interface is used for the creation of audioStreamManager as well as the audio stream settings and management.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Related module**: [OHAudio](capi-audio-kit-ohaudio.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) | OH_AudioStreamManager | Declare the audio stream manager. Audio stream manager provides many functions about audio streams, like monitoring audio streams status, getting different stream types supported information and so on. |

### Functions

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)](#oh_audiomanager_getaudiostreammanager) | Fetch the audio streammanager handle, which is a singleton. |
| [OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)](#oh_audiostreammanager_getdirectplaybacksupport) | Gets the mode of direct playback available for a given audio format with current active device. |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)](#oh_audiostreammanager_isacousticechocancelersupported) | Query whether acoustic echo canceler is supported by input source. |
| [bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isfastplaybacksupported) | Return if fast playback is supported for the specific audio stream info and usage type in current device situation. |
| [bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isfastrecordingsupported) | Return if fast recording is supported for the specific audio stream info and source type in current device situation. |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, bool *supported)](#oh_audiostreammanager_isultrafastplaybacksupported) | This API is used to query whether the current device supports ultra-low latency playback in specific audio stream information and application scenarios. |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source, bool *supported)](#oh_audiostreammanager_isultrafastrecordingsupported) | This API is used to query whether the current device supports ultra-low latency recording in specific audio stream information and application scenarios. |
| [bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isintelligentnoisereductionenabledforcurrentdevice) | Return if the system recording enables intelligent noise reduction for current device. |
| [bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_ismultichannelplaybacksupported) | Returns if multichannel playback is supported for the specific audio stream info and usage type in current device situation. |
| [bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isdirectplaybacksupported) | Returns if direct playback is supported for the specific audio stream info and usage type in current device situation. |
| [bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isoffloadplaybacksupported) | Returns if offload playback is supported for the specific audio stream info and usage type in current device situation. |

## Function description

### OH_AudioManager_GetAudioStreamManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)
```

**Description**

Fetch the audio streammanager handle, which is a singleton.

<!--Device-OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)--><!--Device-OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) **streamManager | output parameter to get the [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md). |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioStreamManager_GetDirectPlaybackSupport()

```c
OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)
```

**Description**

Gets the mode of direct playback available for a given audio format with current active device.

<!--Device-OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)--><!--Device-OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *audioStreamManager | the [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | the [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | the [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage). |
| [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode) *directPlaybackMode | the [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode) pointer to a variable which receives the result. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Function result code: [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful. [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result): 1.The param of audioStreamManager is nullptr; 2.The param of streamInfo is nullptr; 3.The param of usage invalid; 4.The param of directPlaybackMode is nullptr. |

### OH_AudioStreamManager_IsAcousticEchoCancelerSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)
```

**Description**

Query whether acoustic echo canceler is supported by input source.

<!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)--><!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | The [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | Related source type. |
| bool *supported | Pointer to get the result. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Function result code: [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful. [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result): 1.The input param streamManager is nullptr; 2.Source type is invalid. 3.The input param supported is nullptr. |

### OH_AudioStreamManager_IsFastPlaybackSupported()

```c
bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Return if fast playback is supported for the specific audio stream info and usage type in current device situation.

<!--Device-bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)--><!--Device-bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | reference of stream info structure to describe basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | stream usage type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | {@code true} if fast playback is supported in this situation. |

### OH_AudioStreamManager_IsFastRecordingSupported()

```c
bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)
```

**Description**

Return if fast recording is supported for the specific audio stream info and source type in current device situation.

<!--Device-bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)--><!--Device-bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | reference of stream info structure to describe basic audio format. |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | stream source type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | {@code true} if fast recording is supported in this situation. |

### OH_AudioStreamManager_IsUltraFastPlaybackSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, bool *supported)
```

**Description**

This API is used to query whether the current device supports ultra-low latency playback in specific audio stream information and application scenarios.

<!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, bool *supported)--><!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, bool *supported)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] Handle of the audio stream manager. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] Pointer to audio stream information. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] Audio stream usage scenario. |
| bool *supported | [out] indicates the variable indicating whether the ultra-low latency playback result is supported. Only if the function returns [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result): This parameter is valid. The value true indicates that this parameter is supported, and the value false indicates that this parameter is not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS: The query is successful. </li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: streamManager, streamInfo, supported parameter null pointer The * or usage parameter is invalid. </li> <li>AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED: The audio service process exits unexpectedly. </li> </ul> |

### OH_AudioStreamManager_IsUltraFastRecordingSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source, bool *supported)
```

**Description**

This API is used to query whether the current device supports ultra-low latency recording in specific audio stream information and application scenarios.

<!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source, bool *supported)--><!--Device-OH_AudioCommon_Result OH_AudioStreamManager_IsUltraFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source, bool *supported)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] Handle of the audio stream manager. Obtain the handle through [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] Pointer to audio stream information. |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | [in] Audio stream usage scenario. |
| bool *supported | [out] indicates whether to receive the result of ultra-low-latency recording. Only if the function returns [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result): This parameter is valid. The value true indicates that this parameter is supported, and the value false indicates that this parameter is not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS: The query is successful. </li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: streamManager, streamInfo, supported parameter null pointer The * or source parameter is invalid. </li> <li>AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED: The audio service process exits unexpectedly. </li> </ul> |

### OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice()

```c
bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)
```

**Description**

Return if the system recording enables intelligent noise reduction for current device.

<!--Device-bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)--><!--Device-bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | stream source type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | {@code true} if the system recording enables intelligent noise reduction for current device. |

### OH_AudioStreamManager_IsMultichannelPlaybackSupported()

```c
bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Returns if multichannel playback is supported for the specific audio stream info and usage type in current device situation.

<!--Device-bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)--><!--Device-bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | reference of stream info structure to describe basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | stream usage type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True if multichannel playback is supported in this situation. |

### OH_AudioStreamManager_IsDirectPlaybackSupported()

```c
bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Returns if direct playback is supported for the specific audio stream info and usage type in current device situation.

<!--Device-bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)--><!--Device-bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | reference of stream info structure to describe basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | stream usage type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True if direct playback is supported in this situation. |

### OH_AudioStreamManager_IsOffloadPlaybackSupported()

```c
bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**Description**

Returns if offload playback is supported for the specific audio stream info and usage type in current device situation.

<!--Device-bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)--><!--Device-bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) handle provided by [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager). |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | reference of stream info structure to describe basic audio format. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | stream usage type used to decide the audio device and pipe type selection result. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True if offload playback is supported in this situation. |


