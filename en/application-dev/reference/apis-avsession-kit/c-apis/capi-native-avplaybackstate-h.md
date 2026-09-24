# native_avplaybackstate.h

## Overview

Declare playbackState interfaces.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md) | AVSession_PlaybackPosition | Defines the playback position. |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) | OH_AVSession_AVPlaybackState | AVSession playbackstate object. |

### Function

| Name | Description |
| -- | -- |
| [AVSession_ErrCode OH_AVSession_GetPlaybackState(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackState* state)](#oh_avsession_getplaybackstate) | Get State of PlayBackState. |
| [AVSession_ErrCode OH_AVSession_GetPlaybackPosition(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackPosition* position)](#oh_avsession_getplaybackposition) | Get position of PlaybackState. |
| [AVSession_ErrCode OH_AVSession_GetPlaybackSpeed(OH_AVSession_AVPlaybackState* playbackState, int32_t* speed)](#oh_avsession_getplaybackspeed) | Get speed of PlaybackState. |
| [AVSession_ErrCode OH_AVSession_GetPlaybackVolume(OH_AVSession_AVPlaybackState* playbackState, int32_t* volume)](#oh_avsession_getplaybackvolume) | Get volume of PlaybackState. |

## Function description

### OH_AVSession_GetPlaybackState()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackState(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackState* state)
```

**Description**

Get State of PlayBackState.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | reference returned by [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) |
| AVSession_PlaybackState* state | the pointer [AVSession_PlaybackState](capi-native-avsession-base-h.md#avsession_playbackstate) variable that will be set play state value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.  or [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode) if parameter valiation fails                 1.The param of playbackState is nullptr;                 2.The param of state is nullptr. |

### OH_AVSession_GetPlaybackPosition()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackPosition(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackPosition* position)
```

**Description**

Get position of PlaybackState.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | reference returned by [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) |
| [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md)* position | the pointer [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md) variable that will be set playback position value. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.  or [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode) if parameter valiation fails                 1.The param of playbackState is nullptr;                 2.The param of position is nullptr. |

### OH_AVSession_GetPlaybackSpeed()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackSpeed(OH_AVSession_AVPlaybackState* playbackState, int32_t* speed)
```

**Description**

Get speed of PlaybackState.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | reference returned by [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) |
| int32_t* speed | the pointer variable that will be set the speed. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.  or [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode) if parameter valiation fails                 1.The param of playbackState is nullptr;                 2.The param of speed is nullptr. |

### OH_AVSession_GetPlaybackVolume()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackVolume(OH_AVSession_AVPlaybackState* playbackState, int32_t* volume)
```

**Description**

Get volume of PlaybackState.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | reference returned by [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) |
| int32_t* volume | the pointer variable that will be set the volume. |

**Returns**:

| Type | Description |
| -- | -- |
| AVSession_ErrCode | [AV_SESSION_ERR_SUCCESS](capi-native-avsession-errors-h.md#avsession_errcode) If the execution is successful.  or [AV_SESSION_ERR_INVALID_PARAMETER](capi-native-avsession-errors-h.md#avsession_errcode) if parameter valiation fails                 1.The param of playbackState is nullptr;                 2.The param of volume is nullptr. |


