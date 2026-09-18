# native_avcastcontroller.h

## Overview

Declare avcastcontroller interface.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) | OH_AVCastController | OH_AVCastController object<br> A pointer can be created using the {@link OH_AVSession_CreateAVCastController} method. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlaybackStateChanged)(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState* playbackState, void* userData)](#oh_avcastcontrollercallback_playbackstatechanged) | OH_AVCastControllerCallback_PlaybackStateChanged | Declaring the callback struct for playback state change |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_MediaItemChange)(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avQueueItem, void* userData)](#oh_avcastcontrollercallback_mediaitemchange) | OH_AVCastControllerCallback_MediaItemChange | Declaring the callback struct for media item change |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlayNext)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_playnext) | OH_AVCastControllerCallback_PlayNext | Declaring the callback struct for Play Next |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_PlayPrevious)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_playprevious) | OH_AVCastControllerCallback_PlayPrevious | Declaring the callback struct for Play Previous |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_SeekDone)(OH_AVCastController* avcastcontroller, int32_t position, void* userData)](#oh_avcastcontrollercallback_seekdone) | OH_AVCastControllerCallback_SeekDone | Declaring the callback struct for seekDone |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_EndOfStream)(OH_AVCastController* avcastcontroller, void* userData)](#oh_avcastcontrollercallback_endofstream) | OH_AVCastControllerCallback_EndOfStream | Declaring the callback struct for EndOfStream |
| [typedef AVSessionCallback_Result(\*OH_AVCastControllerCallback_Error)(OH_AVCastController* avcastcontroller, void* userData, AVSession_ErrCode error)](#oh_avcastcontrollercallback_error) | OH_AVCastControllerCallback_Error | Declaring the callback struct for cast play error |
| [AVSession_ErrCode OH_AVCastController_Destroy(OH_AVCastController* avcastcontroller)](#oh_avcastcontroller_destroy) | - | Request to destroy the avcastcontroller. |
| [AVSession_ErrCode OH_AVCastController_GetPlaybackState(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState** playbackState)](#oh_avcastcontroller_getplaybackstate) | - | Get the playback status of the current player. Do not release the playbackState pointer separately. It will be destroyed when [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) is called. |
| [AVSession_ErrCode OH_AVCastController_RegisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, int32_t filter, OH_AVCastControllerCallback_PlaybackStateChanged callback, void* userData)](#oh_avcastcontroller_registerplaybackstatechangedcallback) | - | Request to register playback state changed callback. |
| [AVSession_ErrCode OH_AVCastController_UnregisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlaybackStateChanged callback)](#oh_avcastcontroller_unregisterplaybackstatechangedcallback) | - | Request to unregister playback state changed callback. |
| [AVSession_ErrCode OH_AVCastController_RegisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback, void* userData)](#oh_avcastcontroller_registermediaitemchangedcallback) | - | Request to register current media changed callback. |
| [AVSession_ErrCode OH_AVCastController_UnregisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback)](#oh_avcastcontroller_unregistermediaitemchangedcallback) | - | Request to unregister current media item changed callback. |
| [AVSession_ErrCode OH_AVCastController_RegisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback, void* userData)](#oh_avcastcontroller_registerplaynextcallback) | - | Request to register playnext callback send by remote side or media center. |
| [AVSession_ErrCode OH_AVCastController_UnregisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback)](#oh_avcastcontroller_unregisterplaynextcallback) | - | Request to unregister playnext callback send by remote side or media center. |
| [AVSession_ErrCode OH_AVCastController_RegisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback, void* userData)](#oh_avcastcontroller_registerplaypreviouscallback) | - | Request to register playprevious command callback send by remote side or media center. |
| [AVSession_ErrCode OH_AVCastController_UnregisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback)](#oh_avcastcontroller_unregisterplaypreviouscallback) | - | Request to unregister playprevious command callback send by remote side or media center. |
| [AVSession_ErrCode OH_AVCastController_RegisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback, void* userData)](#oh_avcastcontroller_registerseekdonecallback) | - | Request to register seek done callback. |
| [AVSession_ErrCode OH_AVCastController_UnregisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback)](#oh_avcastcontroller_unregisterseekdonecallback) | - | Request to unregister seek done callback. |
| [AVSession_ErrCode OH_AVCastController_RegisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback, void* userData)](#oh_avcastcontroller_registerendofstreamcallback) | - | Request to register end of stream callback. |
| [AVSession_ErrCode OH_AVCastController_UnregisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback)](#oh_avcastcontroller_unregisterendofstreamcallback) | - | Request to unregister end of stream callback. |
| [AVSession_ErrCode OH_AVCastController_RegisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback, void* userData)](#oh_avcastcontroller_registererrorcallback) | - | Request to register listener for playback error events. |
| [AVSession_ErrCode OH_AVCastController_UnregisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback)](#oh_avcastcontroller_unregistererrorcallback) | - | Request to unregister listener for playback error events. |
| [AVSession_ErrCode OH_AVCastController_SendCommonCommand(OH_AVCastController* avcastcontroller, AVSession_AVCastControlCommandType* avCastControlcommand)](#oh_avcastcontroller_sendcommoncommand) | - | Request to send common command to Remote, only support to send play pause stop playnext playprevious command. |
| [AVSession_ErrCode OH_AVCastController_SendSeekCommand(OH_AVCastController* avcastcontroller, int32_t seekTimeMS)](#oh_avcastcontroller_sendseekcommand) | - | Request to send seek command to Remote. |
| [AVSession_ErrCode OH_AVCastController_SendFastForwardCommand(OH_AVCastController* avcastcontroller, int32_t forwardTimeS)](#oh_avcastcontroller_sendfastforwardcommand) | - | Request to send forward command to Remote. |
| [AVSession_ErrCode OH_AVCastController_SendRewindCommand(OH_AVCastController* avcastcontroller, int32_t rewindTimeS)](#oh_avcastcontroller_sendrewindcommand) | - | Request to send rewind command to Remote. |
| [AVSession_ErrCode OH_AVCastController_SendSetSpeedCommand(OH_AVCastController* avcastcontroller, AVSession_PlaybackSpeed speed)](#oh_avcastcontroller_sendsetspeedcommand) | - | Request to send set speed command to Remote. |
| [AVSession_ErrCode OH_AVCastController_SendVolumeCommand(OH_AVCastController* avcastcontroller, int32_t volume)](#oh_avcastcontroller_sendvolumecommand) | - | Request to send volume command to Remote. |
| [AVSession_ErrCode OH_AVCastController_Prepare(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)](#oh_avcastcontroller_prepare) | - | Request to prepare the current player item, this is needed for sink media information displaying. |
| [AVSession_ErrCode OH_AVCastController_Start(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)](#oh_avcastcontroller_start) | - | Request to Play the current item, should contain media uri otherwise the playback will fail. |

### Variable

| Name | Description |
| -- | -- |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_PlaybackStateChanged)( OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState* playbackState, void* userData) | Declaring the callback struct for playback state change<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_MediaItemChange)(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avQueueItem, void* userData) | Declaring the callback struct for media item change<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayNext)(OH_AVCastController* avcastcontroller, void* userData) | Declaring the callback struct for Play Next<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayPrevious)(OH_AVCastController* avcastcontroller, void* userData) | Declaring the callback struct for Play Previous<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_SeekDone)(OH_AVCastController* avcastcontroller, int32_t position, void* userData) | Declaring the callback struct for seekDone<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_EndOfStream)(OH_AVCastController* avcastcontroller, void* userData) | Declaring the callback struct for EndOfStream<br>**Since**: 23 |
| AVSessionCallback_Result(*OH_AVCastControllerCallback_Error)(OH_AVCastController* avcastcontroller, void* userData, AVSession_ErrCode error) | Declaring the callback struct for cast play error<br>**Since**: 23 |

## Function description

### OH_AVCastControllerCallback_PlaybackStateChanged()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlaybackStateChanged)(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState* playbackState, void* userData)
```

**Description**

Declaring the callback struct for playback state change

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| OH_AVSession_AVPlaybackState\* playbackState | the {@link OH_AVSession_AVPlaybackState} pointer variable which will be set the changed playback state. |
| userdata | userdata which is passed by register. |

### OH_AVCastControllerCallback_MediaItemChange()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_MediaItemChange)(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avQueueItem, void* userData)
```

**Description**

Declaring the callback struct for media item change

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| OH_AVSession_AVQueueItem\* avQueueItem | the {@link OH_AVSession_AVQueueItem} pointer variable which will be set the changed media item info. |
| userdata | userdata which is passed by register |

### OH_AVCastControllerCallback_PlayNext()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayNext)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Declaring the callback struct for Play Next

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| userdata | userdata which is passed by register. |

### OH_AVCastControllerCallback_PlayPrevious()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_PlayPrevious)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Declaring the callback struct for Play Previous

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| userdata | userdata which is passed by register. |

### OH_AVCastControllerCallback_SeekDone()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_SeekDone)(OH_AVCastController* avcastcontroller, int32_t position, void* userData)
```

**Description**

Declaring the callback struct for seekDone

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| int32_t position | position value after seek. |
| userdata | userdata which is passed by register. |

### OH_AVCastControllerCallback_EndOfStream()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_EndOfStream)(OH_AVCastController* avcastcontroller, void* userData)
```

**Description**

Declaring the callback struct for EndOfStream

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| userdata | userdata which is passed by register. |

### OH_AVCastControllerCallback_Error()

```c
typedef AVSessionCallback_Result(*OH_AVCastControllerCallback_Error)(OH_AVCastController* avcastcontroller, void* userData, AVSession_ErrCode error)
```

**Description**

Declaring the callback struct for cast play error

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)\* avcastcontroller | the OH_AVCastController instance pointer. |
| userdata | userdata which is passed by register. |
| AVSession_ErrCode error | cast play error code |

### OH_AVCastController_Destroy()

```c
AVSession_ErrCode OH_AVCastController_Destroy(OH_AVCastController* avcastcontroller)
```

**Description**

Request to destroy the avcastcontroller.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avcastcontroller is nullptr. |

### OH_AVCastController_GetPlaybackState()

```c
AVSession_ErrCode OH_AVCastController_GetPlaybackState(OH_AVCastController* avcastcontroller, OH_AVSession_AVPlaybackState** playbackState)
```

**Description**

Get the playback status of the current player. Do not release the playbackState pointer separately. It will be destroyed when [OH_AVCastController_Destroy](capi-native-avcastcontroller-h.md#oh_avcastcontroller_destroy) is called.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| OH_AVSession_AVPlaybackState** playbackState | The returned playbackState |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of playbackState is nullptr. |

### OH_AVCastController_RegisterPlaybackStateChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, int32_t filter, OH_AVCastControllerCallback_PlaybackStateChanged callback, void* userData)
```

**Description**

Request to register playback state changed callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| int32_t filter | The filter {@link AVSession_PlaybackFilter} of playback state determines which param are included in callback. |
| [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) callback | The callback [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr.                                                  3. filter is invalid |

### OH_AVCastController_UnregisterPlaybackStateChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlaybackStateChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlaybackStateChanged callback)
```

**Description**

Request to unregister playback state changed callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) callback | the [OH_AVCastControllerCallback_PlaybackStateChanged](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playbackstatechanged) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code：          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterMediaItemChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback, void* userData)
```

**Description**

Request to register current media changed callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) callback | the [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterMediaItemChangedCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterMediaItemChangedCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_MediaItemChange callback)
```

**Description**

Request to unregister current media item changed callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) callback | the [OH_AVCastControllerCallback_MediaItemChange](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_mediaitemchange) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterPlayNextCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback, void* userData)
```

**Description**

Request to register playnext callback send by remote side or media center.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) callback | the [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterPlayNextCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlayNextCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayNext callback)
```

**Description**

Request to unregister playnext callback send by remote side or media center.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) callback | the [OH_AVCastControllerCallback_PlayNext](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playnext) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterPlayPreviousCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback, void* userData)
```

**Description**

Request to register playprevious command callback send by remote side or media center.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) callback | the [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterPlayPreviousCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterPlayPreviousCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_PlayPrevious callback)
```

**Description**

Request to unregister playprevious command callback send by remote side or media center.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) callback | the [OH_AVCastControllerCallback_PlayPrevious](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_playprevious) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterSeekDoneCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback, void* userData)
```

**Description**

Request to register seek done callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) callback | the [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterSeekDoneCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterSeekDoneCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_SeekDone callback)
```

**Description**

Request to unregister seek done callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) callback | the [OH_AVCastControllerCallback_SeekDone](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_seekdone) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterEndOfStreamCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback, void* userData)
```

**Description**

Request to register end of stream callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) callback | the [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterEndOfStreamCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterEndOfStreamCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_EndOfStream callback)
```

**Description**

Request to unregister end of stream callback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) callback | the [OH_AVCastControllerCallback_EndOfStream](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_endofstream) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_RegisterErrorCallback()

```c
AVSession_ErrCode OH_AVCastController_RegisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback, void* userData)
```

**Description**

Request to register listener for playback error events.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) callback | the [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) to be registered. |
| void* userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_UnregisterErrorCallback()

```c
AVSession_ErrCode OH_AVCastController_UnregisterErrorCallback(OH_AVCastController* avcastcontroller, OH_AVCastControllerCallback_Error callback)
```

**Description**

Request to unregister listener for playback error events.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) callback | the [OH_AVCastControllerCallback_Error](capi-native-avcastcontroller-h.md#oh_avcastcontrollercallback_error) to be unregistered. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of callback is nullptr. |

### OH_AVCastController_SendCommonCommand()

```c
AVSession_ErrCode OH_AVCastController_SendCommonCommand(OH_AVCastController* avcastcontroller, AVSession_AVCastControlCommandType* avCastControlcommand)
```

**Description**

Request to send common command to Remote, only support to send play pause stop playnext playprevious command.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| AVSession_AVCastControlCommandType* avCastControlcommand | control command {@link AVSession_AVCastControlCommandType}. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER} The param of avcastcontroller is nullptr.<br>        {@link AV_SESSION_ERR_CODE_COMMAND_INVALID} The param of avCastControlcommand is invalid.<br>        {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_SendSeekCommand()

```c
AVSession_ErrCode OH_AVCastController_SendSeekCommand(OH_AVCastController* avcastcontroller, int32_t seekTimeMS)
```

**Description**

Request to send seek command to Remote.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| int32_t seekTimeMS | seek time, the unit of time is milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:         {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>       {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>       {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                              1. The param of avcastcontroller is nullptr.<br>                                              2. seekTimeMS invalid.<br>       {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_SendFastForwardCommand()

```c
AVSession_ErrCode OH_AVCastController_SendFastForwardCommand(OH_AVCastController* avcastcontroller, int32_t forwardTimeS)
```

**Description**

Request to send forward command to Remote.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| int32_t forwardTimeS | forward time, the unit of time is seconds. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:         {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>       {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>       {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                               1. The param of avcastcontroller is nullptr.<br>                                               2. forwardTimeS invalid.<br>       {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_SendRewindCommand()

```c
AVSession_ErrCode OH_AVCastController_SendRewindCommand(OH_AVCastController* avcastcontroller, int32_t rewindTimeS)
```

**Description**

Request to send rewind command to Remote.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| int32_t rewindTimeS | rewind time, the unit of time is seconds. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:         {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>       {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>       {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                               1. The param of avcastcontroller is nullptr.<br>                                               2. rewindTimeS invalid.<br>       {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_SendSetSpeedCommand()

```c
AVSession_ErrCode OH_AVCastController_SendSetSpeedCommand(OH_AVCastController* avcastcontroller, AVSession_PlaybackSpeed speed)
```

**Description**

Request to send set speed command to Remote.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| AVSession_PlaybackSpeed speed | control command {@link AVSession_PlaybackSpeed}. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                                1. The param of avcastcontroller is nullptr.<br>                                                2. speed invalid.<br>        {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_SendVolumeCommand()

```c
AVSession_ErrCode OH_AVCastController_SendVolumeCommand(OH_AVCastController* avcastcontroller, int32_t volume)
```

**Description**

Request to send volume command to Remote.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| int32_t volume | volume. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                                1. The param of avcastcontroller is nullptr.<br>                                                2. volume invalid.<br>        {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_Prepare()

```c
AVSession_ErrCode OH_AVCastController_Prepare(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)
```

**Description**

Request to prepare the current player item, this is needed for sink media information displaying.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| OH_AVSession_AVQueueItem* avqueueItem |  media item info {@link OH_AVSession_AVQueueItem}. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}<br>                                                1. The param of avcastcontroller is nullptr.<br>                                                2. The param of avqueueItem is nullptr.<br>        {@link AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST} The remote connection is not established. |

### OH_AVCastController_Start()

```c
AVSession_ErrCode OH_AVCastController_Start(OH_AVCastController* avcastcontroller, OH_AVSession_AVQueueItem* avqueueItem)
```

**Description**

Request to Play the current item, should contain media uri otherwise the playback will fail.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)* avcastcontroller | The avcastcontroller instance pointer |
| OH_AVSession_AVQueueItem* avqueueItem |  media item info {@link OH_AVSession_AVQueueItem}. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | Function result code:          {@link AV_SESSION_ERR_SUCCESS} If the execution is successful.<br>        {@link AV_SESSION_ERR_SERVICE_EXCEPTION} Internal server error.<br>        {@link AV_SESSION_ERR_INVALID_PARAMETER}                                                  1. The param of avcastcontroller is nullptr.                                                  2. The param of avqueueItem is nullptr. |


