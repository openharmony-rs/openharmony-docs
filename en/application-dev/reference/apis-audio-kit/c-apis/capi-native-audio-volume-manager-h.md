# native_audio_volume_manager.h

## Overview

Declare audio volume manager related interfaces.<br> This file interfaces are used for the creation of AudioVolumeManager.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) | OH_AudioVolumeManager | Declare the audio volume manager. Audio volume manager provides many functions for developer to get the information about system volume. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)](#oh_audiovolumemanager_onstreamvolumechangecallback) | OH_AudioVolumeManager_OnStreamVolumeChangeCallback | Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback). |
| [typedef void (\*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)](#oh_audiovolumemanager_onringermodechangecallback) | OH_AudioVolumeManager_OnRingerModeChangeCallback | Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback). |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)](#oh_audiomanager_getaudiovolumemanager) | - | Fetch the audio volume manager handle, which is a singleton. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)](#oh_audiovolumemanager_getmaxvolumebyusage) | - | Obtains the maximum volume level for a specific stream usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)](#oh_audiovolumemanager_getminvolumebyusage) | - | Obtains the minimum volume level for a specific stream usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)](#oh_audiovolumemanager_getvolumebyusage) | - | Obtains the system volume level for a specific stream usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)](#oh_audiovolumemanager_ismutebyusage) | - | Checks whether a stream is muted for a specific stream usage type. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerstreamvolumechangecallback) | - | Register callback to receive stream volume changed events. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)](#oh_audiovolumemanager_unregisterstreamvolumechangecallback) | - | Unregister stream volume change callback. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)](#oh_audiovolumemanager_getringermode) | - | Get current ringer mode. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerringermodechangecallback) | - | Register callback to receive ringer mode changed events. |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)](#oh_audiovolumemanager_unregisterringermodechangecallback) | - | Unregister ringer mode change callback. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)( void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi ) | Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback).<br>**Since**: 20 |
| void (*OH_AudioVolumeManager_OnRingerModeChangeCallback)( void *userData, OH_AudioRingerMode ringerMode ) | Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback).<br>**Since**: 20 |

## Function description

### OH_AudioVolumeManager_OnStreamVolumeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)
```

**Description**

Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback).

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | userdata which is passed by register. |
| OH_AudioStream_Usage usage | the stream usage type for which volume changed. |
| int32_t volumeLevel | the latest volume level. |
| bool updateUi | whether to show the volume change in UI. |

### OH_AudioVolumeManager_OnRingerModeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)
```

**Description**

Prototype for the volume change function that is passed to [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback).

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | userdata which is passed by register. |
| OH_AudioRingerMode ringerMode | the latest ringer mode. |

### OH_AudioManager_GetAudioVolumeManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)
```

**Description**

Fetch the audio volume manager handle, which is a singleton.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) **volumeManager | output parameter to get [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr |

### OH_AudioVolumeManager_GetMaxVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)
```

**Description**

Obtains the maximum volume level for a specific stream usage type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioStream_Usage usage | the stream usage type used to map a specific volume type. |
| int32_t *maxVolumeLevel | output parameter to get maximum volume level. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_GetMinVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)
```

**Description**

Obtains the minimum volume level for a specific stream usage type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioStream_Usage usage | the stream usage type used to map a specific volume type. |
| int32_t *minVolumeLevel | output parameter to get minimum volume level. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_GetVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)
```

**Description**

Obtains the system volume level for a specific stream usage type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioStream_Usage usage | the stream usage type used to map a specific volume type. |
| int32_t *volumeLevel | output parameter to get system volume level. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_IsMuteByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)
```

**Description**

Checks whether a stream is muted for a specific stream usage type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioStream_Usage usage | the stream usage type used to map a specific volume type. |
| bool *muted | output parameter to get whether the stream of this usage is muted. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)
```

**Description**

Register callback to receive stream volume changed events.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioStream_Usage usage | the stream usage type used to map a specific volume type which caller want to listen. |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | callback function which will be called when stream volume changed. |
| void *userData | pointer to a data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)
```

**Description**

Unregister stream volume change callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | callback function which registered in [OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_GetRingerMode()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)
```

**Description**

Get current ringer mode.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| OH_AudioRingerMode *ringerMode | output parameter to get the ringer mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_RegisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)
```

**Description**

Register callback to receive ringer mode changed events.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | callback function which will be called when ringer mode changed. |
| void *userData | pointer to a data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioVolumeManager_UnregisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)
```

**Description**

Unregister ringer mode change callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) handle provided by [OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager). |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | callback function which registered in [OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |


