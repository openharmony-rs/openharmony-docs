# native_audio_debugging_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:51:16.731Z pushedAt=2026-07-21T08:11:39.704Z -->

## Overview

Declares the APIs related to the Audio Debugging Manager. The APIs in this file are used to obtain an Audio Debugging Manager instance and provide audio runtime debugging capabilities, including snapshot information retrieval.

**File to include:** <ohaudio/native_audio_debugging_manager.h>

**Library:** libohaudio.so

**System capability:** SystemCapability.Multimedia.Audio.Core

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | Declares an audio debugging manager. Used for audio runtime debugging, including obtaining snapshot information. |

### Functions

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)](#oh_audiomanager_getaudiodebuggingmanager) | Obtains an Audio Debugging Manager instance (singleton). |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | Prints the snapshot information of all audio modules in the current process. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | Prints the snapshot information of a specified audio playback instance. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | Prints the snapshot information of a specified recording instance. |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | Prints the snapshot information of a specified session manager instance. |

## Function Description

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**Description**

Obtains an Audio Debugging Manager instance (singleton).

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) **manager | Output parameter, used to receive the OH_AudioDebuggingManager instance. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS: Function execution succeeded.</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The manager parameter is nullptr.</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**Description**

Prints the snapshot information of all audio modules in the current process.

> **NOTE**
> 
> The content and format of the snapshot information may change across versions. It is intended for manual debugging reference only. Developers are not advised to develop functional logic based on the snapshot information.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | Audio Debugging Manager instance obtained via [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| int32_t fd | File Descriptor. When fd is less than 0 or not writable, the snapshot information is output to the runtime log; otherwise, it is output to the file pointed to by fd. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS: Function execution successful.</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The manager parameter is nullptr.</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**Description**

Prints the snapshot information of a specified audio playback instance.

> **NOTE**
> 
> The content and format of the snapshot information are subject to change in future versions. It is for manual debugging reference only. Developers are advised not to develop functional logic based on the snapshot information.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | Audio Debugging Manager instance obtained through [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| OH_AudioRenderer *renderer | Pointer to the target audio playback instance, used to print snapshot information. |
| int32_t fd | File descriptor. When fd is less than 0 or not writable, snapshot information is output to the runtime log; otherwise, it is output to the file pointed to by fd. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS: Function execution is successful.</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The parameter manager or renderer is nullptr.</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**Description**

Prints the snapshot information of a specified recording instance.

> **NOTE**
> 
> The content and format of the snapshot information are subject to change across versions. It is intended for manual debugging reference only. Developers are advised not to develop feature logic based on the snapshot information.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | Audio Debugging Manager instance obtained through [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| OH_AudioCapturer *capturer | Pointer to the target recording instance, used to print snapshot information. |
| int32_t fd | File descriptor. When fd is less than 0 or not writable, the snapshot information is output to the runtime log; otherwise, it is output to the file pointed to by fd. |

**Returns**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         <li>AUDIOCOMMON_RESULT_SUCCESS: function execution successful.</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the parameter manager or capturer is nullptr.</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**Description**

Prints the snapshot information of a specified session manager instance.

> **NOTE**
> 
> The content and format of the snapshot information may change with version iterations. It is for manual debugging reference only, and developers are not advised to develop functional logic based on the snapshot information.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | Pointer to the Audio Debugging Manager instance obtained via [OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager). |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *session | Pointer to the target session manager instance, used to print snapshot information. |
| int32_t fd | File descriptor. When fd is less than 0 or not writable, the snapshot information is output to the runtime log; otherwise, it is output to the file pointed to by fd. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS: Function execution successful.</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The parameter manager or session is nullptr.</li><br>         </ul> |