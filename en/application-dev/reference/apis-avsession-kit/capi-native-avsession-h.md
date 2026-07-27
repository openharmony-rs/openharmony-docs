# native_avsession.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the AVSession definition, which can be used to set metadata, playback state, and other information.

**File to include**: <multimedia/av_session/native_avsession.h>

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md) | OH_AVSession | Defines a struct for the playback control session object. You can use the [OH_AVSession_Create](capi-native-avsession-h.md#oh_avsession_create) method to create a playback control session object.|
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) | OH_AVCastController | Defines a struct for the casting controller object. You can use the [OH_AVSession_CreateAVCastController](capi-native-avsession-h.md#oh_avsession_createavcastcontroller) method to create a casting controller object.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnCommand)(OH_AVSession* session, AVSession_ControlCommand command, void* userData)](#oh_avsessioncallback_oncommand) | OH_AVSessionCallback_OnCommand | Defines a callback for a common playback control command.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnFastForward)(OH_AVSession* session, uint32_t seekTime, void* userData)](#oh_avsessioncallback_onfastforward) | OH_AVSessionCallback_OnFastForward | Defines a callback for the fast-forward operation.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnRewind)(OH_AVSession* session, uint32_t seekTime, void* userData)](#oh_avsessioncallback_onrewind) | OH_AVSessionCallback_OnRewind | Defines a callback for the rewind operation.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnSeek)(OH_AVSession* session, uint64_t seekTime, void* userData)](#oh_avsessioncallback_onseek) | OH_AVSessionCallback_OnSeek | Defines a callback for the seek operation.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnSetLoopMode)(OH_AVSession* session, AVSession_LoopMode curLoopMode, void* userData)](#oh_avsessioncallback_onsetloopmode) | OH_AVSessionCallback_OnSetLoopMode | Defines a callback for the operation of setting the loop mode.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OnToggleFavorite)(OH_AVSession* session, const char* assetId, void* userData)](#oh_avsessioncallback_ontogglefavorite) | OH_AVSessionCallback_OnToggleFavorite | Defines a callback for the operation of favoriting a media asset.|
| [typedef AVSessionCallback_Result (\*OH_AVSessionCallback_OutputDeviceChange)(OH_AVSession* session, AVSession_ConnectionState state, AVSession_OutputDeviceInfo* outputDeviceInfo)](#oh_avsessioncallback_outputdevicechange) | OH_AVSessionCallback_OutputDeviceChange | Defines a callback for the device changes.|
| [AVSession_ErrCode OH_AVSession_Create(AVSession_Type sessionType, const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)](#oh_avsession_create) | - | Creates a session object.|
| [AVSession_ErrCode OH_AVSession_Destroy(OH_AVSession* avsession)](#oh_avsession_destroy) | - | Destroys a session object.|
| [AVSession_ErrCode OH_AVSession_Activate(OH_AVSession* avsession)](#oh_avsession_activate) | - | Activates a session.|
| [AVSession_ErrCode OH_AVSession_Deactivate(OH_AVSession* avsession)](#oh_avsession_deactivate) | - | Deactivates a session.|
| [AVSession_ErrCode OH_AVSession_GetSessionType(OH_AVSession* avsession, AVSession_Type* sessionType)](#oh_avsession_getsessiontype) | - | Obtains the session type.|
| [AVSession_ErrCode OH_AVSession_GetSessionId(OH_AVSession* avsession, const char** sessionId)](#oh_avsession_getsessionid) | - | Obtains the session ID.|
| [AVSession_ErrCode OH_AVSession_SetAVMetadata(OH_AVSession* avsession, OH_AVMetadata* avmetadata)](#oh_avsession_setavmetadata) | - | Sets media metadata.|
| [AVSession_ErrCode OH_AVSession_SetPlaybackState(OH_AVSession* avsession, AVSession_PlaybackState playbackState)](#oh_avsession_setplaybackstate) | - | Sets the playback state.|
| [AVSession_ErrCode OH_AVSession_SetPlaybackPosition(OH_AVSession* avsession, AVSession_PlaybackPosition* playbackPosition)](#oh_avsession_setplaybackposition) | - | Sets the playback position.|
| [AVSession_ErrCode OH_AVSession_SetFavorite(OH_AVSession* avsession, bool favorite)](#oh_avsession_setfavorite) | - | Favorites or unfavorites the media asset.|
| [AVSession_ErrCode OH_AVSession_SetLoopMode(OH_AVSession* avsession, AVSession_LoopMode loopMode)](#oh_avsession_setloopmode) | - | Sets a loop mode.|
| [AVSession_ErrCode OH_AVSession_SetRemoteCastEnabled(OH_AVSession* avsession, bool enabled)](#oh_avsession_setremotecastenabled) | - | Requests to enable remote casting.|
| [AVSession_ErrCode OH_AVSession_RegisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback, void* userData)](#oh_avsession_registercommandcallback) | - | Registers a callback for a common playback control command.|
| [AVSession_ErrCode OH_AVSession_UnregisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback)](#oh_avsession_unregistercommandcallback) | - | Unregisters the callback for a common playback control command.|
| [AVSession_ErrCode OH_AVSession_RegisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback, void* userData)](#oh_avsession_registerforwardcallback) | - | Registers a callback for the fast-forward operation.|
| [AVSession_ErrCode OH_AVSession_UnregisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback)](#oh_avsession_unregisterforwardcallback) | - | Unregisters the callback for the fast-forward operation.|
| [AVSession_ErrCode OH_AVSession_RegisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback, void* userData)](#oh_avsession_registerrewindcallback) | - | Registers a callback for the rewind operation.|
| [AVSession_ErrCode OH_AVSession_UnregisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback)](#oh_avsession_unregisterrewindcallback) | - | Unregisters the callback for the rewind operation.|
| [AVSession_ErrCode OH_AVSession_RegisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback, void* userData)](#oh_avsession_registerseekcallback) | - | Registers a callback for the seek operation.|
| [AVSession_ErrCode OH_AVSession_UnregisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback)](#oh_avsession_unregisterseekcallback) | - | Unregisters the callback for the seek operation.|
| [AVSession_ErrCode OH_AVSession_RegisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback, void* userData)](#oh_avsession_registersetloopmodecallback) | - | Registers a callback for the operation of setting the loop mode.|
| [AVSession_ErrCode OH_AVSession_UnregisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback)](#oh_avsession_unregistersetloopmodecallback) | - | Unregisters the callback for the operation of setting the loop mode.|
| [AVSession_ErrCode OH_AVSession_RegisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback, void* userData)](#oh_avsession_registertogglefavoritecallback) | - | Registers a callback for the operation of favoriting a media asset.|
| [AVSession_ErrCode OH_AVSession_UnregisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback)](#oh_avsession_unregistertogglefavoritecallback) | - | Unregisters the callback for the operation of favoriting a media asset.|
| [AVSession_ErrCode OH_AVSession_RegisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)](#oh_avsession_registeroutputdevicechangecallback) | - | Registers a callback for device changes.|
| [AVSession_ErrCode OH_AVSession_UnregisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)](#oh_avsession_unregisteroutputdevicechangecallback) | - | Unregisters the callback for device changes.|
| [AVSession_ErrCode OH_AVSession_AcquireSession(const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)](#oh_avsession_acquiresession) | - | Obtains an existing media session object. When the media session object is no longer needed, call [OH_AVSession_Destroy](capi-native-avsession-h.md#oh_avsession_destroy) to release it.|
| [AVSession_ErrCode OH_AVSession_CreateAVCastController(OH_AVSession* avsession, OH_AVCastController** avcastcontroller)](#oh_avsession_createavcastcontroller) | - | Creates a casting controller object. When the casting controller object is no longer needed, call [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) to release it.|
| [AVSession_ErrCode OH_AVSession_StopCasting(OH_AVSession* avsession)](#oh_avsession_stopcasting) | - | Stops the current casting and disconnects the device.|
| [AVSession_ErrCode OH_AVSession_AcquireOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo** outputDeviceInfo)](#oh_avsession_acquireoutputdevice) | - | Obtains the current output device.|
| [AVSession_ErrCode OH_AVSession_ReleaseOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo *outputDeviceInfo)](#oh_avsession_releaseoutputdevice) | - | Releases the output device object.|

## Function Description

### OH_AVSessionCallback_OnCommand()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnCommand)(OH_AVSession* session, AVSession_ControlCommand command, void* userData)
```

**Description**

Defines a callback for a common playback control command.

**Since**: 13

### OH_AVSessionCallback_OnFastForward()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnFastForward)(OH_AVSession* session, uint32_t seekTime, void* userData)
```

**Description**

Defines a callback for the fast-forward operation.

**Since**: 13

### OH_AVSessionCallback_OnRewind()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnRewind)(OH_AVSession* session, uint32_t seekTime, void* userData)
```

**Description**

Defines a callback for the rewind operation.

**Since**: 13

### OH_AVSessionCallback_OnSeek()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnSeek)(OH_AVSession* session, uint64_t seekTime, void* userData)
```

**Description**

Defines a callback for the seek operation.

**Since**: 13

### OH_AVSessionCallback_OnSetLoopMode()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnSetLoopMode)(OH_AVSession* session, AVSession_LoopMode curLoopMode, void* userData)
```

**Description**

Defines a callback for the operation of setting the loop mode.

**Since**: 13

### OH_AVSessionCallback_OnToggleFavorite()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OnToggleFavorite)(OH_AVSession* session, const char* assetId, void* userData)
```

**Description**

Defines a callback for the operation of favoriting a media asset.

**Since**: 13

### OH_AVSessionCallback_OutputDeviceChange()

```c
typedef AVSessionCallback_Result (*OH_AVSessionCallback_OutputDeviceChange)(OH_AVSession* session, AVSession_ConnectionState state, AVSession_OutputDeviceInfo* outputDeviceInfo)
```

**Description**

Defines a callback for the device changes.

**Since:** 23

### OH_AVSession_Create()

```c
AVSession_ErrCode OH_AVSession_Create(AVSession_Type sessionType, const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)
```

**Description**

Creates a session object.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [AVSession_Type](capi-native-avsession-base-h.md#avsession_type) sessionType |  Session type. For details about the available options, see [AVSession_Type](capi-native-avsession-base-h.md#avsession_type).|
| const char* sessionTag |   Pointer to the session tag.|
| const char* bundleName |   Pointer to the bundle name.|
| const char* abilityName |  Pointer to the ability name.|
| [OH_AVSession](capi-ohavsession-oh-avsession.md)** avsession |    Double pointer to the session object created.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. **sessionType** is invalid.<br>                                         2. The **sessionTag** parameter is **nullptr**.<br>                                         3. The **bundleName** parameter is **nullptr**.<br>                                         4. The **abilityName** parameter is **nullptr**.<br>                                         5. The **avsession** parameter is **nullptr**.|

### OH_AVSession_Destroy()

```c
AVSession_ErrCode OH_AVSession_Destroy(OH_AVSession* avsession)
```

**Description**

Destroys a session object.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_Activate()

```c
AVSession_ErrCode OH_AVSession_Activate(OH_AVSession* avsession)
```

**Description**

Activates a session.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_Deactivate()

```c
AVSession_ErrCode OH_AVSession_Deactivate(OH_AVSession* avsession)
```

**Description**

Deactivates a session.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_GetSessionType()

```c
AVSession_ErrCode OH_AVSession_GetSessionType(OH_AVSession* avsession, AVSession_Type* sessionType)
```

**Description**

Obtains the session type.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_Type](capi-native-avsession-base-h.md#avsession_type)* sessionType | Pointer to the session type obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **sessionType** parameter is **nullptr**.|

### OH_AVSession_GetSessionId()

```c
AVSession_ErrCode OH_AVSession_GetSessionId(OH_AVSession* avsession, const char** sessionId)
```

**Description**

Obtains the session ID.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| const char** sessionId | Double pointer to the session ID obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **sessionId** parameter is **nullptr**.|

### OH_AVSession_SetAVMetadata()

```c
AVSession_ErrCode OH_AVSession_SetAVMetadata(OH_AVSession* avsession, OH_AVMetadata* avmetadata)
```

**Description**

Sets media metadata.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVMetadata](capi-ohavsession-oh-avmetadatastruct.md)* avmetadata | Pointer to the media metadata.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **avmetadata** parameter is **nullptr**.|

### OH_AVSession_SetPlaybackState()

```c
AVSession_ErrCode OH_AVSession_SetPlaybackState(OH_AVSession* avsession, AVSession_PlaybackState playbackState)
```

**Description**

Sets the playback state.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_PlaybackState](capi-native-avsession-base-h.md#avsession_playbackstate) playbackState | Playback state.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **playbackState** parameter is invalid.|

### OH_AVSession_SetPlaybackPosition()

```c
AVSession_ErrCode OH_AVSession_SetPlaybackPosition(OH_AVSession* avsession, AVSession_PlaybackPosition* playbackPosition)
```

**Description**

Sets the playback position.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md)* playbackPosition | Pointer to the playback position.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **playbackPosition** parameter is **nullptr**.|

### OH_AVSession_SetFavorite()

```c
AVSession_ErrCode OH_AVSession_SetFavorite(OH_AVSession* avsession, bool favorite)
```

**Description**

Favorites or unfavorites the media asset.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| bool favorite | Whether to favorite or unfavorite the media asset. **true** means to favorite, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_SetLoopMode()

```c
AVSession_ErrCode OH_AVSession_SetLoopMode(OH_AVSession* avsession, AVSession_LoopMode loopMode)
```

**Description**

Sets a loop mode.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_LoopMode](capi-native-avsession-base-h.md#avsession_loopmode) loopMode | Loop mode.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **loopMode** parameter is invalid.|

### OH_AVSession_SetRemoteCastEnabled()

```c
AVSession_ErrCode OH_AVSession_SetRemoteCastEnabled(OH_AVSession* avsession, bool enabled)
```

**Description**

Requests to enable remote casting.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| bool enabled | Whether to enable remote casting. **true** to enable, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_CODE_SESSION_NOT_EXIST**: The session does not exist.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_RegisterCommandCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback, void* userData)
```

**Description**

Registers a callback for a common playback control command.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_ControlCommand](capi-native-avsession-base-h.md#avsession_controlcommand) command |   Playback control command.|
| [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) callback |  Callback for the control command.|
| void* userData |  Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_CODE_COMMAND_INVALID**: The playback control command is invalid.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterCommandCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterCommandCallback(OH_AVSession* avsession, AVSession_ControlCommand command, OH_AVSessionCallback_OnCommand callback)
```

**Description**

Unregisters the callback for a common playback control command.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_ControlCommand](capi-native-avsession-base-h.md#avsession_controlcommand) command |   Playback control command.|
| [OH_AVSessionCallback_OnCommand](capi-native-avsession-h.md#oh_avsessioncallback_oncommand) callback |  Callback for the control command.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_CODE_COMMAND_INVALID**: The playback control command is invalid.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterForwardCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback, void* userData)
```

**Description**

Registers a callback for the fast-forward operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) callback | Callback for the fast-forward operation.|
| void* userData | Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterForwardCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterForwardCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnFastForward callback)
```

**Description**

Unregisters the callback for the fast-forward operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnFastForward](capi-native-avsession-h.md#oh_avsessioncallback_onfastforward) callback | Callback for the fast-forward operation.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterRewindCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback, void* userData)
```

**Description**

Registers a callback for the rewind operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) callback | Callback for the rewind operation.|
| void* userData | Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterRewindCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterRewindCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnRewind callback)
```

**Description**

Unregisters the callback for the rewind operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnRewind](capi-native-avsession-h.md#oh_avsessioncallback_onrewind) callback | Callback for the rewind operation.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterSeekCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback, void* userData)
```

**Description**

Registers a callback for the seek operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) callback | Callback for the seek operation.|
| void* userData | Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterSeekCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterSeekCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSeek callback)
```

**Description**

Unregisters the callback for the seek operation.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnSeek](capi-native-avsession-h.md#oh_avsessioncallback_onseek) callback | Callback for the seek operation.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterSetLoopModeCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback, void* userData)
```

**Description**

Registers a callback for the operation of setting the loop mode.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) callback | Callback for the operation of setting the loop mode.|
| void* userData | Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterSetLoopModeCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterSetLoopModeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnSetLoopMode callback)
```

**Description**

Unregisters the callback for the operation of setting the loop mode.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnSetLoopMode](capi-native-avsession-h.md#oh_avsessioncallback_onsetloopmode) callback | Callback for the operation of setting the loop mode.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterToggleFavoriteCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback, void* userData)
```

**Description**

Registers a callback for the operation of favoriting a media asset.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) callback | Callback for the operation of favoriting a media asset.|
| void* userData | Pointer to the application data passed through the callback functions.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterToggleFavoriteCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterToggleFavoriteCallback(OH_AVSession* avsession, OH_AVSessionCallback_OnToggleFavorite callback)
```

**Description**

Unregisters the callback for the operation of favoriting a media asset.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OnToggleFavorite](capi-native-avsession-h.md#oh_avsessioncallback_ontogglefavorite) callback | Callback for the operation of favoriting a media asset.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_RegisterOutputDeviceChangeCallback()

```c
AVSession_ErrCode OH_AVSession_RegisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)
```

**Description**

Registers a callback for device changes.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) callback | Sets a callback for device changes.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_UnregisterOutputDeviceChangeCallback()

```c
AVSession_ErrCode OH_AVSession_UnregisterOutputDeviceChangeCallback(OH_AVSession* avsession, OH_AVSessionCallback_OutputDeviceChange callback)
```

**Description**

Unregisters the callback for device changes.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVSessionCallback_OutputDeviceChange](capi-native-avsession-h.md#oh_avsessioncallback_outputdevicechange) callback | Sets a callback for device changes.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVSession_AcquireSession()

```c
AVSession_ErrCode OH_AVSession_AcquireSession(const char* sessionTag, const char* bundleName, const char* abilityName, OH_AVSession** avsession)
```

**Description**

Obtains an existing media session object. When the media session object is no longer needed, call [OH_AVSession_Destroy](capi-native-avsession-h.md#oh_avsession_destroy) to release it.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| const char* sessionTag | Pointer to the custom session tag set by the application.|
| const char* bundleName | Pointer to the application bundle name.|
| const char* abilityName | Pointer to the application ability name.|
| [OH_AVSession](capi-ohavsession-oh-avsession.md)** avsession | Double pointer to the **OH_AVSession**.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_CODE_SESSION_NOT_EXIST**: The session does not exist.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **sessionTag** parameter is invalid.<br>                                         2. The **bundleName** parameter is invalid.<br>                                         3. The **abilityName** parameter is invalid.<br>                                         4. The **avsession** parameter is **nullptr**.|

### OH_AVSession_CreateAVCastController()

```c
AVSession_ErrCode OH_AVSession_CreateAVCastController(OH_AVSession* avsession, OH_AVCastController** avcastcontroller)
```

**Description**

Creates a casting controller object. When the casting controller object is no longer needed, call [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) to release it.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)** avcastcontroller | Double pointer to the **OH_AVCastController**.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_CODE_SESSION_NOT_EXIST**: The session does not exist.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **avcastcontroller** parameter is **nullptr**.|

### OH_AVSession_StopCasting()

```c
AVSession_ErrCode OH_AVSession_StopCasting(OH_AVSession* avsession)
```

**Description**

Stops the current casting and disconnects the device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_CODE_SESSION_NOT_EXIST**: The session does not exist.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avsession** parameter is **nullptr**.|

### OH_AVSession_AcquireOutputDevice()

```c
AVSession_ErrCode OH_AVSession_AcquireOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo** outputDeviceInfo)
```

**Description**

Obtains the current output device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_OutputDeviceInfo](capi-ohavsession-avsession-outputdeviceinfo.md)** outputDeviceInfo | Double pointer to the **AVSession_OutputDeviceInfo**. The **outputDeviceInfo** pointer cannot be released separately. When the **outputDeviceInfo** is no longer needed, call [OH_AVSession_ReleaseOutputDevice](capi-native-avsession-h.md#oh_avsession_releaseoutputdevice) to release it.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: The session service is abnormal.<br>         **AV_SESSION_ERR_CODE_SESSION_NOT_EXIST**: The session does not exist.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **outputDeviceInfo** parameter is **nullptr**.|

### OH_AVSession_ReleaseOutputDevice()

```c
AVSession_ErrCode OH_AVSession_ReleaseOutputDevice(OH_AVSession* avsession, AVSession_OutputDeviceInfo *outputDeviceInfo)
```

**Description**

Releases the output device object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession](capi-ohavsession-oh-avsession.md)* avsession | Pointer to a session object.|
| [AVSession_OutputDeviceInfo](capi-ohavsession-avsession-outputdeviceinfo.md) *outputDeviceInfo | Pointer to the output device to be released.|

**Returns**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avsession** parameter is **nullptr**.<br>                                         2. The **outputDeviceInfo** parameter is **nullptr**.|
