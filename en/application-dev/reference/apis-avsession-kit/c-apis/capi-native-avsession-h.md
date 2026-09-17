# native_avsession.h

## Overview

Declare avsession interface.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md) | OH_AVSession | AVSession object<br> A pointer can be created using [OH_AVSession_Create](capi-native-avsession-h.md#oh_avsession_create) method. |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) | OH_AVCastController | OH_AVCastController object<br> A pointer can be created using the [OH_AVSession_CreateAVCastController](capi-native-avsession-h.md#oh_avsession_createavcastcontroller) method. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnCommand)(OH_AVSession* session, AVSession_ControlCommand command, void* userData)](#oh_avsessioncallback_oncommand) | OH_AVSessionCallback_OnCommand | Declaring the callback struct for playback command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnFastForward)(OH_AVSession* session, uint32_t seekTime, void* userData)](#oh_avsessioncallback_onfastforward) | OH_AVSessionCallback_OnFastForward | Declaring the callback struct for forward command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnRewind)(OH_AVSession* session, uint32_t seekTime, void* userData)](#oh_avsessioncallback_onrewind) | OH_AVSessionCallback_OnRewind | Declaring the callback struct for rewind command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnSeek)(OH_AVSession* session, uint64_t seekTime, void* userData)](#oh_avsessioncallback_onseek) | OH_AVSessionCallback_OnSeek | Declaring the callback struct for seek command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnSetLoopMode)(OH_AVSession* session, AVSession_LoopMode curLoopMode, void* userData)](#oh_avsessioncallback_onsetloopmode) | OH_AVSessionCallback_OnSetLoopMode | Declaring the callback struct for set loop mode command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnToggleFavorite)(OH_AVSession* session, const char* assetId, void* userData)](#oh_avsessioncallback_ontogglefavorite) | OH_AVSessionCallback_OnToggleFavorite | Declaring the callback struct for toggle favorite command |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OutputDeviceChange)(OH_AVSession* session, AVSession_ConnectionState state, AVSession_OutputDeviceInfo* outputDeviceInfo)](#oh_avsessioncallback_outputdevicechange) | OH_AVSessionCallback_OutputDeviceChange | Declaring the callback struct for output device change |
| [AVSession_ErrCode OH_AVSession_Create(AVSession_Type sessionType, const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)](#oh_avsession_create) | - | Request to create the avsession. |
| [AVSession_ErrCode OH_AVSession_Destroy(OH_AVSession* avsession)](#oh_avsession_destroy) | - | Request to destroy the avsession. |
| [AVSession_ErrCode OH_AVSession_Activate(OH_AVSession* avsession)](#oh_avsession_activate) | - | Activate the avsession. |
| [AVSession_ErrCode OH_AVSession_Deactivate(OH_AVSession* avsession)](#oh_avsession_deactivate) | - | Deactivate the avsession. |
| [AVSession_ErrCode OH_AVSession_GetSessionType(OH_AVSession* avsession, AVSession_Type* sessionType)](#oh_avsession_getsessiontype) | - | Get session type. |
| [AVSession_ErrCode OH_AVSession_GetSessionId(OH_AVSession* avsession, const char** sessionId)](#oh_avsession_getsessionid) | - | Get session id. |
| [AVSession_ErrCode OH_AVSession_SetAVMetadata(OH_AVSession* avsession, OH_AVMetadata* avmetadata)](#oh_avsession_setavmetadata) | - | Request to set av metadata. |
| [AVSession_ErrCode OH_AVSession_SetPlaybackState(OH_AVSession* avsession, AVSession_PlaybackState playbackState)](#oh_avsession_setplaybackstate) | - | Request to set av playbackstate. |
| [AVSession_ErrCode OH_AVSession_SetPlaybackPosition(OH_AVSession* avsession, AVSession_PlaybackPosition* playbackPosition)](#oh_avsession_setplaybackposition) | - | Request to set playback position. |
| [AVSession_ErrCode OH_AVSession_SetFavorite(OH_AVSession* avsession, bool favorite)](#oh_avsession_setfavorite) | - | Request to set favorite state. |
| [AVSession_ErrCode OH_AVSession_SetLoopMode(OH_AVSession* avsession, AVSession_LoopMode loopMode)](#oh_avsession_setloopmode) | - | Request to set loop mode. |
| [AVSession_ErrCode OH_AVSession_SetRemoteCastEnabled(OH_AVSession* avsession, bool enabled)](#oh_avsession_setremotecastenabled) | - | Request to enable remote cast. |
| [AVSession_ErrCode OH_AVSession_RegisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback, void* userData)](#oh_avsession_registercommandcallback) | - | Request to register command callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback)](#oh_avsession_unregistercommandcallback) | - | Request to unregister command callback. |
| [AVSession_ErrCode OH_AVSession_RegisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback, void* userData)](#oh_avsession_registerforwardcallback) | - | Request to register fastforward callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback)](#oh_avsession_unregisterforwardcallback) | - | Request to unregister fastforward callback. |
| [AVSession_ErrCode OH_AVSession_RegisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback, void* userData)](#oh_avsession_registerrewindcallback) | - | Request to register rewind callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback)](#oh_avsession_unregisterrewindcallback) | - | Request to unregister rewind callback. |
| [AVSession_ErrCode OH_AVSession_RegisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback, void* userData)](#oh_avsession_registerseekcallback) | - | Request to register seek callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback)](#oh_avsession_unregisterseekcallback) | - | Request to unregister seek callback. |
| [AVSession_ErrCode OH_AVSession_RegisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback, void* userData)](#oh_avsession_registersetloopmodecallback) | - | Request to register set loopmode callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback)](#oh_avsession_unregistersetloopmodecallback) | - | Request to unregister set loopmode callback. |
| [AVSession_ErrCode OH_AVSession_RegisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback, void* userData)](#oh_avsession_registertogglefavoritecallback) | - | Request to register toggle favorite callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback)](#oh_avsession_unregistertogglefavoritecallback) | - | Request to unregister toggle favorite callback. |
| [AVSession_ErrCode OH_AVSession_RegisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)](#oh_avsession_registeroutputdevicechangecallback) | - | Request to register output device change callback. |
| [AVSession_ErrCode OH_AVSession_UnregisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)](#oh_avsession_unregisteroutputdevicechangecallback) | - | Request to unregister output device change callback. |
| [AVSession_ErrCode OH_AVSession_AcquireSession(const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)](#oh_avsession_acquiresession) | - | Request to acquire an AVSession instance if already created. Call [OH_AVSession_Destroy](capi-native-avsession-h.md#oh_avsession_destroy) to release the OH_AVSession when it is not used anymore. |
| [AVSession_ErrCode OH_AVSession_CreateAVCastController(OH_AVSession* avsession, OH_AVCastController** avcastcontroller)](#oh_avsession_createavcastcontroller) | - | Create an AVCastController object. Call {@link OH_AVCastController_Destroy} to release the OH_AVCastController when it is not used anymore. |
| [AVSession_ErrCode OH_AVSession_StopCasting(OH_AVSession* avsession)](#oh_avsession_stopcasting) | - | Request to stop current cast and disconnect device connection. |
| [AVSession_ErrCode OH_AVSession_AcquireOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo** outputDeviceInfo)](#oh_avsession_acquireoutputdevice) | - | Acquire current output device. |
| [AVSession_ErrCode OH_AVSession_ReleaseOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo *outputDeviceInfo)](#oh_avsession_releaseoutputdevice) | - | Release outputDeviceInfo object. |

### Variable

| Name | Description |
| -- | -- |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnCommand)(OH_AVSession* session, AVSession_ControlCommand command, void* userData) | Declaring the callback struct for playback command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnFastForward)(OH_AVSession* session, uint32_t seekTime, void* userData) | Declaring the callback struct for forward command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnRewind)(OH_AVSession* session, uint32_t seekTime, void* userData) | Declaring the callback struct for rewind command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnSeek)(OH_AVSession* session, uint64_t seekTime, void* userData) | Declaring the callback struct for seek command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnSetLoopMode)(OH_AVSession* session, AVSession_LoopMode curLoopMode, void* userData) | Declaring the callback struct for set loop mode command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OnToggleFavorite)(OH_AVSession* session, const char* assetId, void* userData) | Declaring the callback struct for toggle favorite command<br>**Since**: 13 |
| AVSessionCallback_Result (*OH_AVSessionCallback_OutputDeviceChange)(OH_AVSession* session, AVSession_ConnectionState state, AVSession_OutputDeviceInfo* outputDeviceInfo) | Declaring the callback struct for output device change<br>**Since**: 23 |

## Function description

### OH_AVSessionCallback_OnCommand()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnCommand)(OH_AVSession* session, AVSession_ControlCommand command, void* userData)
```

**Description**

Declaring the callback struct for playback command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| AVSession_ControlCommand command | playback command |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OnFastForward()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnFastForward)(OH_AVSession* session, uint32_t seekTime, void* userData)
```

**Description**

Declaring the callback struct for forward command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| uint32_t seekTime | forward time, described by milliseconds. |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OnRewind()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnRewind)(OH_AVSession* session, uint32_t seekTime, void* userData)
```

**Description**

Declaring the callback struct for rewind command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| uint32_t seekTime | rewind time, described by milliseconds. |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OnSeek()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnSeek)(OH_AVSession* session, uint64_t seekTime, void* userData)
```

**Description**

Declaring the callback struct for seek command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| uint64_t seekTime | position after seek, described by milliseconds. |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OnSetLoopMode()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnSetLoopMode)(OH_AVSession* session, AVSession_LoopMode curLoopMode, void* userData)
```

**Description**

Declaring the callback struct for set loop mode command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| AVSession_LoopMode curLoopMode | current loop mode. |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OnToggleFavorite()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnToggleFavorite)(OH_AVSession* session, const char* assetId, void* userData)
```

**Description**

Declaring the callback struct for toggle favorite command

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| const char\* assetId | the assetId for which the favorite status needs to be switched. |
| void\* userData | userdata which is passed by register. |

### OH_AVSessionCallback_OutputDeviceChange()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OutputDeviceChange)(OH_AVSession* session, AVSession_ConnectionState state, AVSession_OutputDeviceInfo* outputDeviceInfo)
```

**Description**

Declaring the callback struct for output device change

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)\* session | the OH_AVSession instance pointer. |
| AVSession_ConnectionState state | the {@link AVSession_ConnectionState} of output device. |
| outputDeviceInfothe | {@link AVSession_OutputDeviceInfo} pointer variable which will be set current output device info. Do not release the outputDeviceInfo pointer separately, instead call [OH_AVSession_ReleaseOutputDevice](capi-native-avsession-h.md#oh_avsession_releaseoutputdevice) to release the outputDeviceInfo when it is not used anymore. |

### OH_AVSession_Create()

```c
AVSession_ErrCode OH_AVSession_Create(AVSession_Type sessionType, const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)
```

**Description**

Request to create the avsession.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| AVSession_Type sessionType | The session type to set |
| const char* sessionTag | The session tag set by the application |
| const char* bundleName | The bundle name to set |
| const char* abilityName | The abilityName to set |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)** avsession | Pointer to a variable to receive the OH_AVSession |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} If session already existed or internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}:                                                  1. The param of sessionType is invalid.                                                  2. The param of sessionTag is nullptr.                                                  3. The param of bundleName is nullptr.                                                  4. The param of abilityName is nullptr.                                                  5. The param of avsession is nullptr. |

### OH_AVSession_Destroy()

```c
AVSession_ErrCode OH_AVSession_Destroy(OH_AVSession* avsession)
```

**Description**

Request to destroy the avsession.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avsession is nullptr. |

### OH_AVSession_Activate()

```c
AVSession_ErrCode OH_AVSession_Activate(OH_AVSession* avsession)
```

**Description**

Activate the avsession.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avsession is nullptr. |

### OH_AVSession_Deactivate()

```c
AVSession_ErrCode OH_AVSession_Deactivate(OH_AVSession* avsession)
```

**Description**

Deactivate the avsession.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avsession is nullptr. |

### OH_AVSession_GetSessionType()

```c
AVSession_ErrCode OH_AVSession_GetSessionType(OH_AVSession* avsession, AVSession_Type* sessionType)
```

**Description**

Get session type.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_Type* sessionType | The returned session type |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is invalid.                                                  2. The param of sessionType is nullptr. |

### OH_AVSession_GetSessionId()

```c
AVSession_ErrCode OH_AVSession_GetSessionId(OH_AVSession* avsession, const char** sessionId)
```

**Description**

Get session id.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| const char** sessionId | The returned session id |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of sessionId is nullptr. |

### OH_AVSession_SetAVMetadata()

```c
AVSession_ErrCode OH_AVSession_SetAVMetadata(OH_AVSession* avsession, OH_AVMetadata* avmetadata)
```

**Description**

Request to set av metadata.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| OH_AVMetadata* avmetadata | The metadata to set |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of avmetadata is nullptr. |

### OH_AVSession_SetPlaybackState()

```c
AVSession_ErrCode OH_AVSession_SetPlaybackState(OH_AVSession* avsession, AVSession_PlaybackState playbackState)
```

**Description**

Request to set av playbackstate.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_PlaybackState playbackState | The playbackState to set |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of playbackState is invalid. |

### OH_AVSession_SetPlaybackPosition()

```c
AVSession_ErrCode OH_AVSession_SetPlaybackPosition(OH_AVSession* avsession, AVSession_PlaybackPosition* playbackPosition)
```

**Description**

Request to set playback position.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_PlaybackPosition* playbackPosition | The playbackPosition to set |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of playbackPosition is nullptr. |

### OH_AVSession_SetFavorite()

```c
AVSession_ErrCode OH_AVSession_SetFavorite(OH_AVSession* avsession, bool favorite)
```

**Description**

Request to set favorite state.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| bool favorite | true means making the resource to be liked, false means dislike. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avsession is nullptr. |

### OH_AVSession_SetLoopMode()

```c
AVSession_ErrCode OH_AVSession_SetLoopMode(OH_AVSession* avsession, AVSession_LoopMode loopMode)
```

**Description**

Request to set loop mode.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_LoopMode loopMode | The loopmode to be set for playback. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of loopMode is invalid. |

### OH_AVSession_SetRemoteCastEnabled()

```c
AVSession_ErrCode OH_AVSession_SetRemoteCastEnabled(OH_AVSession* avsession, bool enabled)
```

**Description**

Request to enable remote cast.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| bool enabled | enable or disable remote cast |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_CODE_SESSION_NOT_EXIST} session does not exist.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr. |

### OH_AVSession_RegisterCommandCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback, void* userData)
```

**Description**

Request to register command callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_ControlCommand command | The control command type to be registered. |
| [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) callback | the [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_CODE_COMMAND_INVALID} The command is invalid.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterCommandCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback)
```

**Description**

Request to unregister command callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_ControlCommand command | The control command type to be unregistered. |
| [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) callback | the [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_CODE_COMMAND_INVALID} The command is invalid.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterForwardCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback, void* userData)
```

**Description**

Request to register fastforward callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) callback | the [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterForwardCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback)
```

**Description**

Request to unregister fastforward callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) callback | the [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterRewindCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback, void* userData)
```

**Description**

Request to register rewind callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) callback | the [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterRewindCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback)
```

**Description**

Request to unregister rewind callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) callback | the [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterSeekCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback, void* userData)
```

**Description**

Request to register seek callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) callback | the [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterSeekCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback)
```

**Description**

Request to unregister seek callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) callback | the [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterSetLoopModeCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback, void* userData)
```

**Description**

Request to register set loopmode callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) callback | the [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterSetLoopModeCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback)
```

**Description**

Request to unregister set loopmode callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) callback | the [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterToggleFavoriteCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback, void* userData)
```

**Description**

Request to register toggle favorite callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) callback | the [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterToggleFavoriteCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback)
```

**Description**

Request to unregister toggle favorite callback.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) callback | the [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_RegisterOutputDeviceChangeCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)
```

**Description**

Request to register output device change callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) callback | the [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) to be registered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_UnregisterOutputDeviceChangeCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)
```

**Description**

Request to unregister output device change callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) callback | the [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVSession_AcquireSession()

```c
AVSession_ErrCode OH_AVSession_AcquireSession(const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)
```

**Description**

Request to acquire an AVSession instance if already created. Call [OH_AVSession_Destroy](capi-native-avsession-h.md#oh_avsession_destroy) to release the OH_AVSession when it is not used anymore.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* sessionTag | The session tag set by the application |
| const char* bundleName | The bundle name to set |
| const char* abilityName | The abilityName name to set |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)** avsession | Pointer to a variable to receive the OH_AVSession |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_CODE_SESSION_NOT_EXIST} If session is not existed.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}:                                                  1. The param of sessionTag is invalid.                                                  2. The param of bundleName is nullptr.                                                  3. The param of abilityName is nullptr.                                                  4. The param of avsession is nullptr. |

### OH_AVSession_CreateAVCastController()

```c
AVSession_ErrCode OH_AVSession_CreateAVCastController(OH_AVSession* avsession, OH_AVCastController** avcastcontroller)
```

**Description**

Create an AVCastController object. Call {@link OH_AVCastController_Destroy} to release the OH_AVCastController when it is not used anymore.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)** avcastcontroller | [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) Pointer to a variable to receive the avcastcontroller |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_CODE_SESSION_NOT_EXIST} The session does not exist.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of avcastcontroller is nullptr. |

### OH_AVSession_StopCasting()

```c
AVSession_ErrCode OH_AVSession_StopCasting(OH_AVSession* avsession)
```

**Description**

Request to stop current cast and disconnect device connection.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_CODE_SESSION_NOT_EXIST} The session does not exist.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr. |

### OH_AVSession_AcquireOutputDevice()

```c
AVSession_ErrCode OH_AVSession_AcquireOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo** outputDeviceInfo)
```

**Description**

Acquire current output device.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_OutputDeviceInfo** outputDeviceInfo | Pointer {@link AVSession_OutputDeviceInfo} to a variable to receive the OutputDeviceInfo Do not release the outputDeviceInfo pointer separately, instead call [OH_AVSession_ReleaseOutputDevice](capi-native-avsession-h.md#oh_avsession_releaseoutputdevice) to release the outputDeviceInfo when it is not used anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_CODE_SESSION_NOT_EXIST} The session does not exist.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avsession is nullptr.                                                  2. The param of outputDeviceInfo is nullptr. |

### OH_AVSession_ReleaseOutputDevice()

```c
AVSession_ErrCode OH_AVSession_ReleaseOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo *outputDeviceInfo)
```

**Description**

Release outputDeviceInfo object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | The avsession instance pointer |
| AVSession_OutputDeviceInfo *outputDeviceInfo | outputdeivce should be released. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1.The param of avsession is nullptr;                                                  2.The param of outputDeviceInfo is nullptr. |


