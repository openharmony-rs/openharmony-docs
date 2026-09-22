# native_audio_resource_manager.h

## Overview

Declare audio stream manager related interfaces.<br> This file interfaces are used for the creation of AudioResourceManager.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) | OH_AudioResourceManager | Declare the audio resource manager. Audio resource manager provides many functions for developer to manage system resources to avoid underrun or overrun in audio playback and recording. |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) | OH_AudioWorkgroup | Declare the audio workgroup. The handle of audio workgroup is used for workgroup related functions. The system will manage cpu resources on a workgroup basis instead of thread. For parallel task threads, you can add them into one workgroup, and for asynchronous task threads, use one workgroup for each thread. There is an upper limit to the total number of workgroups for each process, so application should release the workgroup which is no longer in use. |

### Function

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioResourceManager(OH_AudioResourceManager **resourceManager)](#oh_audiomanager_getaudioresourcemanager) | Fetch the audio resource manager handle, which is a singleton. |
| [OH_AudioCommon_Result OH_AudioResourceManager_CreateWorkgroup(OH_AudioResourceManager *resourceManager, const char *name, OH_AudioWorkgroup **group)](#oh_audioresourcemanager_createworkgroup) | Create a workgroup for audio data processing threads in application. System manages cpu resources by workgroup configuration. |
| [OH_AudioCommon_Result OH_AudioResourceManager_ReleaseWorkgroup(OH_AudioResourceManager *resourceManager, OH_AudioWorkgroup *group)](#oh_audioresourcemanager_releaseworkgroup) | Release the workgroup created before. |
| [OH_AudioCommon_Result OH_AudioWorkgroup_AddCurrentThread(OH_AudioWorkgroup *group, int32_t *tokenId)](#oh_audioworkgroup_addcurrentthread) | Add current thread into a specified audio workgroup as audio data processing thread. |
| [OH_AudioCommon_Result OH_AudioWorkgroup_RemoveThread(OH_AudioWorkgroup *group, int32_t tokenId)](#oh_audioworkgroup_removethread) | Remove the thread from a specified audio workgroup. |
| [OH_AudioCommon_Result OH_AudioWorkgroup_Start(OH_AudioWorkgroup *group, uint64_t startTime, uint64_t deadlineTime)](#oh_audioworkgroup_start) | Notify system the audio workgroup start working. Call this function before processing the audio frame. |
| [OH_AudioCommon_Result OH_AudioWorkgroup_Stop(OH_AudioWorkgroup *group)](#oh_audioworkgroup_stop) | Notify system the audio workgroup stop working. Call this function after the audio frame processing is completed. |

## Function description

### OH_AudioManager_GetAudioResourceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioResourceManager(OH_AudioResourceManager **resourceManager)
```

**Description**

Fetch the audio resource manager handle, which is a singleton.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) **resourceManager | output parameter to get [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr |

### OH_AudioResourceManager_CreateWorkgroup()

```c
OH_AudioCommon_Result OH_AudioResourceManager_CreateWorkgroup(OH_AudioResourceManager *resourceManager, const char *name, OH_AudioWorkgroup **group)
```

**Description**

Create a workgroup for audio data processing threads in application. System manages cpu resources by workgroup configuration.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) *resourceManager | [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) handle provided by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| const char *name | workgroup name |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) **group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle for managing audio data processing threads. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) out of workgroup resources      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioResourceManager_ReleaseWorkgroup()

```c
OH_AudioCommon_Result OH_AudioResourceManager_ReleaseWorkgroup(OH_AudioResourceManager *resourceManager, OH_AudioWorkgroup *group)
```

**Description**

Release the workgroup created before.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) *resourceManager | [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) handle provided by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle provided by [OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioWorkgroup_AddCurrentThread()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_AddCurrentThread(OH_AudioWorkgroup *group, int32_t *tokenId)
```

**Description**

Add current thread into a specified audio workgroup as audio data processing thread.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle provided by [OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup). |
| int32_t *tokenId | a token id that represent the thread added. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) out of resources for the new thread      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioWorkgroup_RemoveThread()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_RemoveThread(OH_AudioWorkgroup *group, int32_t tokenId)
```

**Description**

Remove the thread from a specified audio workgroup.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle provided by [OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup). |
| int32_t tokenId | id for thread returned by {link OH_AudioWorkgroup_AddCurrentThread} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr or token id is invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioWorkgroup_Start()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_Start(OH_AudioWorkgroup *group, uint64_t startTime, uint64_t deadlineTime)
```

**Description**

Notify system the audio workgroup start working. Call this function before processing the audio frame.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle provided by [OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup). |
| uint64_t startTime | the time when audio thread start working, using system time. The unit of time is milliseconds. |
| uint64_t deadlineTime | the time before which audio work should be finished, otherwise underrun may happens. The unit of time is milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr, or time is invalid      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |

### OH_AudioWorkgroup_Stop()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_Stop(OH_AudioWorkgroup *group)
```

**Description**

Notify system the audio workgroup stop working. Call this function after the audio frame processing is completed.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) handle provided by [OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | @return      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if input param is nullptr      [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) system process error occurs |


