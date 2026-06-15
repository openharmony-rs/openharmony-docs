# native_avplaybackstate.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

Defines the playback state.

**File to include:** <multimedia/av_session/native_avplaybackstate.h>

**Library:** libohavsession.so

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md) | AVSession_PlaybackPosition | Defines the playback position.|
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md) | OH_AVSession_AVPlaybackState | Defines the playback state object.|

### Functions

| Name| Description|
| -- | -- |
| [AVSession_ErrCode OH_AVSession_GetPlaybackState(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackState* state)](#oh_avsession_getplaybackstate) | Obtains the playback state.|
| [AVSession_ErrCode OH_AVSession_GetPlaybackPosition(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackPosition* position)](#oh_avsession_getplaybackposition) | Obtains the playback position.|
| [AVSession_ErrCode OH_AVSession_GetPlaybackSpeed(OH_AVSession_AVPlaybackState* playbackState, int32_t* speed)](#oh_avsession_getplaybackspeed) | Obtains the playback speed.|
| [AVSession_ErrCode OH_AVSession_GetPlaybackVolume(OH_AVSession_AVPlaybackState* playbackState, int32_t* volume)](#oh_avsession_getplaybackvolume) | Obtains the playback volume.|

## Function Description

### OH_AVSession_GetPlaybackState()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackState(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackState* state)
```

**Description**

Obtains the playback state.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | Pointer to the playback state instance object.|
| [AVSession_PlaybackState](capi-native-avsession-base-h.md#avsession_playbackstate)* state | Pointer to the playback state value.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The parameter verification fails. The possible causes are as follows:<br>                                                         1. The **playbackState** parameter is **nullptr**.<br>                                                         2. The **state** parameter is **nullptr**.|

### OH_AVSession_GetPlaybackPosition()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackPosition(OH_AVSession_AVPlaybackState* playbackState, AVSession_PlaybackPosition* position)
```

**Description**

Obtains the playback position.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | Pointer to the playback state instance object.|
| [AVSession_PlaybackPosition](capi-ohavsession-avsession-playbackposition.md)* position | Pointer to the playback position value.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The parameter verification fails. The possible causes are as follows:<br>                                                         1. The **playbackState** parameter is **nullptr**.<br>                                                         2. The **position** parameter is **nullptr**.|

### OH_AVSession_GetPlaybackSpeed()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackSpeed(OH_AVSession_AVPlaybackState* playbackState, int32_t* speed)
```

**Description**

Obtains the playback speed.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | Pointer to the playback state instance object.|
| int32_t* speed | Pointer to the playback speed value.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The parameter verification fails. The possible causes are as follows:<br>                                                         1. The **playbackState** parameter is **nullptr**.<br>                                                         2. The **speed** parameter is **nullptr**.|

### OH_AVSession_GetPlaybackVolume()

```c
AVSession_ErrCode OH_AVSession_GetPlaybackVolume(OH_AVSession_AVPlaybackState* playbackState, int32_t* volume)
```

**Description**

Obtains the playback volume.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AVSession_AVPlaybackState](capi-ohavsession-oh-avsession-avplaybackstate.md)* playbackState | Pointer to the playback state instance object.|
| int32_t* volume | Pointer to the playback volume value.|

**Return value**

| Type| Description|
| -- | -- |
| [AVSession_ErrCode](capi-native-avsession-errors-h.md#avsession_errcode) | **AV_SESSION_ERR_SUCCESS**: The function is executed successfully.<br>         **AV_SESSION_ERR_INVALID_PARAMETER**: The parameter verification fails. The possible causes are as follows:<br>                                                         1. The **playbackState** parameter is **nullptr**.<br>                                                         2. The **volume** parameter is **nullptr**.|
