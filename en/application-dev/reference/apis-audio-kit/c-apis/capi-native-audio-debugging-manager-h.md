# native_audio_debugging_manager.h

## Overview

Declare audio debugging manager related interfaces.<br> This file interfaces are used for the creation of AudioDebuggingManager.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | Declare the audio debugging manager. Audio debugging manager provides many functions for developer to get the information about audio system runtime info. |

### Function

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)](#oh_audiomanager_getaudiodebuggingmanager) | Gets the audio debugging manager handle, which is a singleton. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | Prints full audio runtime snapshot for current app process. The snapshot will contain all audio renderers, capturers, audio session information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | Prints full audio runtime snapshot for target audio renderer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | Prints full audio runtime snapshot for target audio capturer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | Prints full audio runtime snapshot for target audio session manager instance. The snapshot will contain the session status, scene, strategy and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction. |

## Function description

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**Description**

Gets the audio debugging manager handle, which is a singleton.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) **manager | The output parameter to get [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) The param of manager is nullptr. |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**Description**

Prints full audio runtime snapshot for current app process. The snapshot will contain all audio renderers, capturers, audio session information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) handle provided by [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| int32_t fd | is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) The param of manager is nullptr. |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**Description**

Prints full audio runtime snapshot for target audio renderer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) handle provided by [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| OH_AudioRenderer *renderer | Pointer to the target audio renderer instance to print snapshot. |
| int32_t fd | is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1.The param of manager is nullptr;                                                     2.The param of renderer is nullptr; |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**Description**

Prints full audio runtime snapshot for target audio capturer instance. The snapshot will contain the stream, pipe, volume and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) handle provided by [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| OH_AudioCapturer *capturer | Pointer to the target audio capturer instance to print snapshot. |
| int32_t fd | is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1.The param of manager is nullptr;                                                     2.The param of capturer is nullptr; |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**Description**

Prints full audio runtime snapshot for target audio session manager instance. The snapshot will contain the session status, scene, strategy and device information. Note that the information details and format may vary from different version, it can only be used for manual debugging, user should not rely on the information for actual function realization or file content extraction.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) handle provided by [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| OH_AudioSessionManager *session | Pointer to the target audio session manager instance to print snapshot. |
| int32_t fd | is a file descriptor, indicates the location that the snapshot information will be written to. If the fd is less than 0 or no writable, the snapshot information will be printed into the running log, otherwise the snapshot will be written into the file. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1.The param of manager is nullptr;                                                     2.The param of session is nullptr; |


