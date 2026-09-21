# native_audio_manager.h

## Overview

Declare audio manager related interfaces.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) | OH_AudioManager | Declare the audio manager. The handle of audio manager is used for audio management related functions. |

### Macro

| Name | Description |
| -- | -- |
| NATIVE_AUDIO_MANAGER_H | Declare audio manager related interfaces.<br>**Since**: 12<br>**System capability**: SystemCapability.Multimedia.Audio.Core |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioManager_OnAudioSceneChangeCallback)(void *userData, OH_AudioScene scene)](#oh_audiomanager_onaudioscenechangecallback) | OH_AudioManager_OnAudioSceneChangeCallback | Prototype for the audio scene change function that is passed to [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback). |
| [OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)](#oh_getaudiomanager) | - | Get audio manager handle. |
| [OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)](#oh_getaudioscene) | - | Get audio scene. |
| [OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)](#oh_audiomanager_registeraudioscenechangecallback) | - | Register callback to receive audio scene changed events. |
| [OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback)](#oh_audiomanager_unregisteraudioscenechangecallback) | - | Unregister audio scene change callback. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioManager_OnAudioSceneChangeCallback) ( void *userData, OH_AudioScene scene ) | Prototype for the audio scene change function that is passed to [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback).<br>**Since**: 20 |

## Function description

### OH_AudioManager_OnAudioSceneChangeCallback()

```c
typedef void (*OH_AudioManager_OnAudioSceneChangeCallback)(void *userData, OH_AudioScene scene)
```

**Description**

Prototype for the audio scene change function that is passed to [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback).

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | userdata which is passed by register. |
| OH_AudioScene scene | the latest audio scene. |

### OH_GetAudioManager()

```c
OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)
```

**Description**

Get audio manager handle.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) **audioManager | the [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) handle received from this function. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.          [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result):                                                         1.The param of audioManager is nullptr; |

### OH_GetAudioScene()

```c
OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)
```

**Description**

Get audio scene.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md)* manager | the [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) handle received from [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| OH_AudioScene *scene | the [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene) pointer to receive the result. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.          [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result):                                                         1.The param of audioManager is nullptr;                                                         2.The param of scene is nullptr. |

### OH_AudioManager_RegisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)
```

**Description**

Register callback to receive audio scene changed events.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) handle received from [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | callback function which will be called when audio scene changed. |
| void *userData | pointer to a data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if the execution is successful      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)                                                    1.param of manager is nullptr                                                    2.param of callback is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioManager_UnregisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback)
```

**Description**

Unregister audio scene change callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) handle received from [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | callback function which registered in [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if the execution is successful      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)                                                    1.param of manager is nullptr                                                    2.param of callback is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |


