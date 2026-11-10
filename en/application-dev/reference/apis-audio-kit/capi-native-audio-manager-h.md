# native_audio_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=bead1a6d3edc23d7114be1e74f679f8512152b63 translatedAt=2026-11-10T03:03:24.892Z pushedAt=2026-11-10T04:38:47.837Z nl=1 -->

## Overview

The file declares the functions related to an audio manager.

**File to include**: <ohaudio/native_audio_manager.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) | OH_AudioManager | Describes an audio manager, which is used for audio management.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_AudioManager_OnAudioSceneChangeCallback)(void *userData, OH_AudioScene scene)](#oh_audiomanager_onaudioscenechangecallback) | OH_AudioManager_OnAudioSceneChangeCallback | Defines the prototype of the audio scene change callback function, which is passed in [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback).|
| [OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)](#oh_getaudiomanager) | - |Obtains an audio manager instance.<br>To use audio manager related features, you must first obtain an audio manager instance. |
| [OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)](#oh_getaudioscene) | - | Obtains the audio scene.|
| [OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)](#oh_audiomanager_registeraudioscenechangecallback) | - | Registers the audio scene change callback function.|
| [OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback)](#oh_audiomanager_unregisteraudioscenechangecallback) | - | Unregisters the audio scene change callback function.|

## Function Description

### OH_AudioManager_OnAudioSceneChangeCallback()

```c
typedef void (*OH_AudioManager_OnAudioSceneChangeCallback) (void *userData, OH_AudioScene scene)
```

**Description**

Defines the prototype of the audio scene change callback function, which is passed in [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback).

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| void *userData | Pointer to user data.|
| [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene) scene | Audio scene after change.|

### OH_GetAudioManager()

```c
OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)
```

**Description**

Obtains an audio manager instance.<br>To use audio manager related features, you must first obtain an audio manager instance.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) **audioManager | Address of the pointer to OH_AudioManager, used to receive the obtained audio manager instance. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | **AUDIOCOMMON_RESULT_SUCCESS**: The function is executed successfully.<br>         **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM**: The **audioManager** parameter is nullptr.|

### OH_GetAudioScene()

```c
OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)
```

**Description**

Obtains the audio scene.

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md)* manager | Pointer to the audio manager instance obtained through [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene) *scene | Pointer to an [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene), which is used to receive the audio scene.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. the manager parameter is nullptr;<br>                                                        2. the scene parameter is nullptr. |

### OH_AudioManager_RegisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager,OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)
```

**Description**

Registers the audio scene change callback function.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | Pointer to the audio manager instance obtained through [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | Callback invoked when the audio scene is switched. |
| void *userData | Pointer to user data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                    1. The parameter manager is nullptr;<br>                                                    2. The parameter callback is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: system error. |

### OH_AudioManager_UnregisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager,OH_AudioManager_OnAudioSceneChangeCallback callback)
```

**Description**

Unregisters the audio scene change callback function.

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | Pointer to the audio manager instance obtained through [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | Callback for the audio scene change event, passed in [OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback) and used for unregistration. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Returns AUDIOCOMMON_RESULT_SUCCESS if the function is executed successfully.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if:<br>                                                    1. the manager parameter is nullptr;<br>                                                    2. the callback parameter is nullptr.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if a system error occurs. |


