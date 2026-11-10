# native_audio_volume_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=138f7dcec9e99067f11a5ba1afa58271363a7ef2 translatedAt=2026-11-10T03:04:45.172Z pushedAt=2026-11-10T04:45:47.444Z nl=1 -->

## Overview

Declares the audio volume manager APIs.<br> The APIs in this file are used to create an AudioVolumeManager.

**File to include:** <ohaudio/native_audio_volume_manager.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) | OH_AudioVolumeManager | Declares the audio volume manager. The audio volume manager provides various functions for developers to obtain system volume information. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)](#oh_audiovolumemanager_onstreamvolumechangecallback) | OH_AudioVolumeManager_OnStreamVolumeChangeCallback | Defines the prototype of the volume change callback function, used to pass to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback). |
| [typedef void (\*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)](#oh_audiovolumemanager_onringermodechangecallback) | OH_AudioVolumeManager_OnRingerModeChangeCallback | Defines the prototype of the ringtone mode change callback function, used to pass to [OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback). |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)](#oh_audiomanager_getaudiovolumemanager) | - | Obtains the volume manager instance.<br>To use the volume manager related functions, you must first obtain the volume manager instance. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)](#oh_audiovolumemanager_getmaxvolumebyusage) | - | Gets the maximum volume level of the audio stream with the specified usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)](#oh_audiovolumemanager_getminvolumebyusage) | - | Gets the minimum volume level of the audio stream with the specified usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)](#oh_audiovolumemanager_getvolumebyusage) | - | Gets the system volume level of the audio stream with the specified usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)](#oh_audiovolumemanager_ismutebyusage) | - | Checks whether the audio stream with the specified usage type is muted. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerstreamvolumechangecallback) | - | Registers the callback function for audio stream volume changes. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)](#oh_audiovolumemanager_unregisterstreamvolumechangecallback) | - | Unregisters the callback function for audio stream volume changes. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)](#oh_audiovolumemanager_getringermode) | - | Gets the current ringtone mode. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerringermodechangecallback) | - | Registers the callback function for ringtone mode switching. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)](#oh_audiovolumemanager_unregisterringermodechangecallback) | - | Unregisters the callback function for ringtone mode switching. |

## Function Description

### OH_AudioVolumeManager_OnStreamVolumeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)
```

**Description**

Defines the prototype of the volume change callback function, which is used to pass to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback).

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| void *userData | Pointer to user-defined data. |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Usage type of the stream whose volume is adjusted. |
| int32_t volumeLevel | Volume after the change. |
| bool updateUi | Whether to display the volume change in the UI. The value **true** means to display, and **false** means not to display. |

### OH_AudioVolumeManager_OnRingerModeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)
```

**Description**

Defines the prototype of the ringtone mode change callback function, which is used to pass to [OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback).

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| void *userData | Pointer to user-defined data. |
| [OH_AudioRingerMode](capi-native-audio-common-h.md#oh_audioringermode) ringerMode | Ringtone mode after the switch. |

### OH_AudioManager_GetAudioVolumeManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)
```

**Description**

Obtains a volume manager instance.<br>To use the volume manager functions, you must first obtain a volume manager instance.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) **volumeManager | Address of the pointer to the OH_AudioVolumeManager instance, used to receive the obtained volume manager instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The volumeManager parameter is nullptr. |

### OH_AudioVolumeManager_GetMaxVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)
```

**Description**

Gets the maximum volume level of the audio stream with the specified usage type.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage type used to map a specific volume type. |
| int32_t *maxVolumeLevel | Pointer to the maximum volume returned. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or maxVolumeLevel is nullptr, or usage is an invalid value.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_GetMinVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)
```

**Description**

Gets the minimum volume level of the audio stream with the specified usage type.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage type used to map a specific volume type. |
| int32_t *minVolumeLevel | Used to receive the minimum volume returned. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or minVolumeLevel is nullptr, or usage is an invalid value.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_GetVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)
```

**Description**

Gets the system volume level of the audio stream with the specified usage type.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage type used to map a specific volume type. |
| int32_t *volumeLevel | Used to receive the returned system volume. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or volumeLevel is nullptr, or usage is an invalid value.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_IsMuteByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)
```

**Description**

Checks whether the audio stream of the specified usage type is muted.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage type used to map a specific volume type. |
| bool *muted | Pointer to the parameter used to receive whether the audio stream is muted. true indicates muted, and false indicates not muted. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: function execution succeeded.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: volumeManager or muted is nullptr, or usage is an invalid value.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: system processing error. |

### OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)
```

**Description**

Registers a callback function for audio stream volume changes.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | Audio stream usage type monitored to map a specific volume type. |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) invoked when the volume of the monitored audio stream changes. |
| void *userData | Pointer to user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager, usage, or callback is nullptr, or if usage is an invalid value.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)
```

**Description**

Unregisters the callback function for audio stream volume changes.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | Callback for the audio stream volume change event, passed in [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback), used to unregister. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or callback is nullptr.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_GetRingerMode()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)
```

**Description**

Obtains the current ringtone mode.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioRingerMode](capi-native-audio-common-h.md#oh_audioringermode) *ringerMode | Used to receive the returned ringtone mode. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function is executed successfully.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or ringerMode is nullptr.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_RegisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)
```

**Description**

Registers a callback for ringtone mode changes.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | Callback invoked when the monitored ringtone mode changes. This callback is [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback). |
| void *userData | Pointer to user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or callback is nullptr.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |

### OH_AudioVolumeManager_UnregisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)
```

**Description**

Unregisters the ringtone mode change callback function.

**Since**: 20


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | Pointer to the volume manager instance obtained through [OH_AudioManager_GetAudioVolumeManager()](#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | Callback for the ringtone mode change event, which is passed in [OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback) and used to unregister. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the function execution is successful.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if volumeManager or callback is nullptr.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system processing error occurs. |


