# native_avcastcontroller.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

Declares the definitions of the playback controller.

**File to include:**: <multimedia/av_session/native_avcastcontroller.h>

**Library:** libohavsession.so

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) | OH_AVCastController | Defines the playback controller object. You can use the [OH_AVSession_CreateAVCastController](capi-native-avsession-h.md#oh_avsession_createavcastcontroller) method to create a pointer.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlaybackStateChanged)(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState* playbackState, void* userData)](#oh_avcastcontrollercallback_playbackstatechanged) | OH_AVCastControllerCallback_PlaybackStateChanged | Triggered when the playback state changes.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_MediaItemChange)(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avQueueItem, void* userData)](#oh_avcastcontrollercallback_mediaitemchange) | OH_AVCastControllerCallback_MediaItemChange | Triggered when the media item changes.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlayNext)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_playnext) | OH_AVCastControllerCallback_PlayNext | Triggered when the next track is played.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlayPrevious)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_playprevious) | OH_AVCastControllerCallback_PlayPrevious | Triggered when the previous track is played.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_SeekDone)(OH_AVCastController* avcastcontroller, int32_t position, void* userData)](#oh_avcastcontrollercallback_seekdone) | OH_AVCastControllerCallback_SeekDone | Triggered when the seek is complete.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_EndOfStream)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_endofstream) | OH_AVCastControllerCallback_EndOfStream | Triggered when the playback stream ends.|
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_Error)(OH_AVCastController* avcastcontroller, void* userData, AVSession_ErrCode error)](#oh_avcastcontrollercallback_error) | OH_AVCastControllerCallback_Error | Triggered when a playback error occurs.|
| [AVSession_ErrCode OH_AVCastController_Destroy(OH_AVCastController* avcastcontroller)](#oh_avcastcontroller_destroy) | - | Requests to destroy the playback controller object.|
| [AVSession_ErrCode OH_AVCastController_GetPlaybackState(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState** playbackState)](#oh_avcastcontroller_getplaybackstate) | - | Obtains the playback state of the current player. Do not release the **playbackState** pointer separately.<br> When [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) is called, the playback controller will be destroyed.|
| [AVSession_ErrCode OH_AVCastController_RegisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, int32_t filter, OH_AVCastControllerCallback_PlaybackStateChanged callback, void* userData)](#oh_avcastcontroller_registerplaybackstatechangedcallback) | - | Requests to register a callback for playback state changes.|
| [AVSession_ErrCode OH_AVCastController_UnregisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlaybackStateChanged callback)](#oh_avcastcontroller_unregisterplaybackstatechangedcallback) | - | Requests to unregister a callback for playback state changes.|
| [AVSession_ErrCode OH_AVCastController_RegisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback, void* userData)](#oh_avcastcontroller_registermediaitemchangedcallback) | - | Requests to register a callback for changes to the media item being played.|
| [AVSession_ErrCode OH_AVCastController_UnregisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback)](#oh_avcastcontroller_unregistermediaitemchangedcallback) | - | Requests to unregister a callback for changes to the media item being played.|
| [AVSession_ErrCode OH_AVCastController_RegisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback, void* userData)](#oh_avcastcontroller_registerplaynextcallback) | - | Requests to register a callback for the next track request sent by the remote device or media center.|
| [AVSession_ErrCode OH_AVCastController_UnregisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback)](#oh_avcastcontroller_unregisterplaynextcallback) | - | Requests to unregister a callback for the next track request sent by the remote device or media center.|
| [AVSession_ErrCode OH_AVCastController_RegisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback, void* userData)](#oh_avcastcontroller_registerplaypreviouscallback) | - | Requests to register a callback for the previous track request sent by the remote device or media center.|
| [AVSession_ErrCode OH_AVCastController_UnregisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback)](#oh_avcastcontroller_unregisterplaypreviouscallback) | - | Requests to unregister a callback for the previous track request sent by the remote device or media center.|
| [AVSession_ErrCode OH_AVCastController_RegisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback, void* userData)](#oh_avcastcontroller_registerseekdonecallback) | - | Requests to register a callback for the seek completion.|
| [AVSession_ErrCode OH_AVCastController_UnregisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback)](#oh_avcastcontroller_unregisterseekdonecallback) | - | Requests to unregister a callback for the seek completion.|
| [AVSession_ErrCode OH_AVCastController_RegisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback, void* userData)](#oh_avcastcontroller_registerendofstreamcallback) | - | Requests to register a callback for the end of stream. |
| [AVSession_ErrCode OH_AVCastController_UnregisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback)](#oh_avcastcontroller_unregisterendofstreamcallback) | - | Requests to unregister a callback for the end of stream.|
| [AVSession_ErrCode OH_AVCastController_RegisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback, void* userData)](#oh_avcastcontroller_registererrorcallback) | - | Requests to register a callback for the playback error event.|
| [AVSession_ErrCode OH_AVCastController_UnregisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback)](#oh_avcastcontroller_unregistererrorcallback) | - | Requests to unregister a callback for the playback error event.|
| [AVSession_ErrCode OH_AVCastController_SendCommonCommand(OH_AVCastController* avcastcontroller, AVSession_AVCastControlCommandType* avCastControlcommand)](#oh_avcastcontroller_sendcommoncommand) | - | Requests to send a common command to the remote device. Only commands such as play, pause, stop, next, and previous are supported.|
| [AVSession_ErrCode OH_AVCastController_SendSeekCommand(OH_AVCastController* avcastcontroller, int32_t seekTimeMS)](#oh_avcastcontroller_sendseekcommand) | - | Requests to send a search command to the remote device.|
| [AVSession_ErrCode OH_AVCastController_SendFastForwardCommand(OH_AVCastController* avcastcontroller, int32_t forwardTimeS)](#oh_avcastcontroller_sendfastforwardcommand) | - | Requests to send a fast-forward command to the remote device.|
| [AVSession_ErrCode OH_AVCastController_SendRewindCommand(OH_AVCastController* avcastcontroller, int32_t rewindTimeS)](#oh_avcastcontroller_sendrewindcommand) | - | Requests to send a rewind command to the remote device.|
| [AVSession_ErrCode OH_AVCastController_SendSetSpeedCommand(OH_AVCastController* avcastcontroller, AVSession_PlaybackSpeed speed)](#oh_avcastcontroller_sendsetspeedcommand) | - | Requests to send a speed setting command to the remote device.|
| [AVSession_ErrCode OH_AVCastController_SendVolumeCommand(OH_AVCastController* avcastcontroller, int32_t volume)](#oh_avcastcontroller_sendvolumecommand) | - | Requests to send a volume control command to the remote device.|
| [AVSession_ErrCode OH_AVCastController_Prepare(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)](#oh_avcastcontroller_prepare) | - | Requests to prepare the current playback queue item. This operation is a prerequisite for displaying output media information.|
| [AVSession_ErrCode OH_AVCastController_Start(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)](#oh_avcastcontroller_start) | - | Requests to play the current item.  It should contain media resources; otherwise, playback will fail.|

## Function Description

### OH_AVCastControllerCallback_PlaybackStateChanged()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlaybackStateChanged)(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState* playbackState, void* userData)
```

**Description**

Triggered when the playback state changes.

**Since:** 23

### OH_AVCastControllerCallback_MediaItemChange()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_MediaItemChange)(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avQueueItem, void* userData)
```

**Description**

Triggered when the media item changes.

**Since:** 23

### OH_AVCastControllerCallback_PlayNext()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayNext)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Triggered when the next track is played.

**Since:** 23

### OH_AVCastControllerCallback_PlayPrevious()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayPrevious)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Triggered when the previous track is played.

**Since:** 23

### OH_AVCastControllerCallback_SeekDone()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_SeekDone)(OH_AVCastController* avcastcontroller, int32_t position, void* userData)
```

**Description**

Triggered when the seek is complete.

**Since:** 23

### OH_AVCastControllerCallback_EndOfStream()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_EndOfStream)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Triggered when the playback stream ends.

**Since:** 23

### OH_AVCastControllerCallback_Error()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_Error)(OH_AVCastController* avcastcontroller, void* userData, AVSession_ErrCode error)
```

**Description**

Triggered when a playback error occurs.

**Since:** 23

### OH_AVCastController_Destroy()

```c
AVSession_ErrCode OH_AVCastController_Destroy(OH_AVCastController* avcastcontroller)
```

**Description**

Requests to destroy the playback controller object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avcastcontroller** parameter is **nullptr**.|

### OH_AVCastController_GetPlaybackState()

```c
AVSession_ErrCode OH_AVCastController_GetPlaybackState(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState** playbackState)
```

**Description**

Obtains the playback state of the current player. Do not release the **playbackState** pointer separately. When [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) is called, the playback controller will be destroyed.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)** playbackState | Double pointer to the playback state.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **playbackState** parameter is **nullptr**.|

### OH_AVCastController_RegisterPlaybackStateChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, int32_t filter, OH_AVCastControllerCallback_PlaybackStateChanged callback, void* userData)
```

**Description**

Requests to register a callback for playback state changes.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| int32_t filter | [AVSession_PlaybackFilter](capi-native-avsession-base-h.md#avsession_playbackfilter) used to determine the parameters to be included in the callback.|
| [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.<br>                                         3. The **filter** parameter is invalid.|

### OH_AVCastController_UnregisterPlaybackStateChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlaybackStateChanged callback)
```

**Description**

Requests to unregister a callback for playback state changes.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterMediaItemChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback, void* userData)
```

**Description**

Requests to register a callback for changes to the media item being played.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterMediaItemChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback)
```

**Description**

Requests to unregister a callback for changes to the media item being played.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterPlayNextCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback, void* userData)
```

**Description**

Requests to register a callback for the next track request sent by the remote device or media center.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterPlayNextCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback)
```

**Description**

Requests to unregister a callback for the next track request sent by the remote device or media center.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterPlayPreviousCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback, void* userData)
```

**Description**

Requests to register a callback for the previous track request sent by the remote device or media center.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterPlayPreviousCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback)
```

**Description**

Requests to unregister a callback for the previous track request sent by the remote device or media center.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterSeekDoneCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback, void* userData)
```

**Description**

Requests to register a callback for the seek completion.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterSeekDoneCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback)
```

**Description**

Requests to unregister a callback for the seek completion.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterEndOfStreamCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback, void* userData)
```

**Description**

Requests to register a callback for the end of stream.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterEndOfStreamCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback)
```

**Description**

Requests to unregister a callback for the end of stream.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_RegisterErrorCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback, void* userData)
```

**Description**

Requests to register a callback for the playback error event.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) callback | Callback to register.|
| void* userData | Pointer to the user data passed by the user.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_UnregisterErrorCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback)
```

**Description**

Requests to unregister a callback for the playback error event.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) callback | Callback to unregister.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **callback** parameter is **nullptr**.|

### OH_AVCastController_SendCommonCommand()

```c
AVSession_ErrCode OH_AVCastController_SendCommonCommand(OH_AVCastController* avcastcontroller, AVSession_AVCastControlCommandType* avCastControlcommand)
```

**Description**

Requests to send a common command to the remote device. Only commands such as play, pause, stop, next, and previous are supported.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [AVSession_AVCastControlCommandType](capi-native-avsession-base-h.md#avsession_avcastcontrolcommandtype)* avCastControlcommand | Pointer to the control command.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The **avcastcontroller** parameter is **nullptr**.<br>         **AV_SESSION_ERR_CODE_COMMAND_INVALID**: The **avCastControlcommand** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_SendSeekCommand()

```c
AVSession_ErrCode OH_AVCastController_SendSeekCommand(OH_AVCastController* avcastcontroller, int32_t seekTimeMS)
```

**Description**

Requests to send a search command to the remote device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| int32_t seekTimeMS | Seek time. The unit is milliseconds.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **seekTimeMS** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_SendFastForwardCommand()

```c
AVSession_ErrCode OH_AVCastController_SendFastForwardCommand(OH_AVCastController* avcastcontroller, int32_t forwardTimeS)
```

**Description**

Requests to send a fast-forward command to the remote device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| int32_t forwardTimeS | Fast-forward time. The unit is second.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **forwardTimeS** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_SendRewindCommand()

```c
AVSession_ErrCode OH_AVCastController_SendRewindCommand(OH_AVCastController* avcastcontroller, int32_t rewindTimeS)
```

**Description**

Requests to send a rewind command to the remote device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| int32_t rewindTimeS | Rewind time. The unit is second.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **rewindTimeS** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_SendSetSpeedCommand()

```c
AVSession_ErrCode OH_AVCastController_SendSetSpeedCommand(OH_AVCastController* avcastcontroller, AVSession_PlaybackSpeed speed)
```

**Description**

Requests to send a speed setting command to the remote device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [AVSession_PlaybackSpeed](capi-native-avsession-base-h.md#avsession_playbackspeed) speed | Speed control command.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **speed** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_SendVolumeCommand()

```c
AVSession_ErrCode OH_AVCastController_SendVolumeCommand(OH_AVCastController* avcastcontroller, int32_t volume)
```

**Description**

Requests to send a volume control command to the remote device.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| int32_t volume | Volume control.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **volume** parameter is invalid.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_Prepare()

```c
AVSession_ErrCode OH_AVCastController_Prepare(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)
```

**Description**

Requests to prepare the current playback queue item. This operation is a prerequisite for displaying the output media information.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVSession_AVQueueItem](capi-ohavsession-oh-avsession-avqueueitem.md)* avqueueItem | Pointer to the audio and video queue item.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **avqueueItem** parameter is **nullptr**.<br>         **AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST**: The remote connection is not established.|

### OH_AVCastController_Start()

```c
AVSession_ErrCode OH_AVCastController_Start(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)
```

**Description**

Requests to play the current item.  It should contain media resources; otherwise, playback will fail.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | Pointer to the instance object of the playback controller.|
| [OH_AVSession_AVQueueItem](capi-ohavsession-oh-avsession-avqueueitem.md)* avqueueItem | Pointer to the audio and video queue item.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_SERVICE_EXCEPTION**: Internal server error.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**:<br>                                         1. The **avcastcontroller** parameter is **nullptr**.<br>                                         2. The **avqueueItem** parameter is **nullptr**.|
