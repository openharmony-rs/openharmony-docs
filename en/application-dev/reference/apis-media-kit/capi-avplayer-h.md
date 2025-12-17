# avplayer.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xushubo; @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the AVPlayer APIs. You can use the native AVPlayer APIs to play a media asset.

**File to include**: <multimedia/player_framework/avplayer.h>

**Library**: libavplayer.so

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [MediaKeySession](capi-avplayer-mediakeysession.md) | MediaKeySession | Describes the media key session.|
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) | DRM_MediaKeySystemInfo | Describes the media key system information.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)](#player_mediakeysysteminfocallback) | Player_MediaKeySystemInfoCallback | Called when media key system information of the AVPlayer is updated.|
| [OH_AVPlayer *OH_AVPlayer_Create(void)](#oh_avplayer_create) | - | Creates an OH_AVPlayer instance.<br> You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios.<!--Del--><br> The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd--> |
| [OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_seturlsource) | - | Sets the HTTP URL of a media source to be played by an AVPlayer.  |
| [OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_setfdsource) | - | Sets the file descriptor of a media source to be played by an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)](#oh_avplayer_setdatasource) | - | Sets the media source of the AVPlayer. The data of this media source is provided by the application.|
| [OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)](#oh_avplayer_prepare) | - | Prepares the playback environment and buffers media data.<br> This function must be called after **SetSource**.|
| [OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)](#oh_avplayer_play) | - | Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare](#oh_avplayer_prepare).<br> In other words, you can call this function when the AVPlayer is in the prepared state.|
| [OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)](#oh_avplayer_pause) | - | Pauses playback.|
| [OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)](#oh_avplayer_stop) | - | Stops playback.|
| [OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)](#oh_avplayer_reset) | - | Restores the AVPlayer to the initial state.<br> After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](#oh_avplayer_prepare) and [OH_AVPlayer_Play](#oh_avplayer_play) in sequence.|
| [OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)](#oh_avplayer_release) | - | Asynchronously releases an OH_AVPlayer instance.<br> The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window.|
| [OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)](#oh_avplayer_releasesync) | - | Synchronously releases an OH_AVPlayer instance.<br> The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism.|
| [OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)](#oh_avplayer_setvolume) | - | Sets the volume for an AVPlayer.<br> This function can be used when the AVPlayer is in the playing or paused state. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used.|
| [OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)](#oh_avplayer_setloudnessgain) | - | Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. The **usage** parameter of the AVPlayer stream must be [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC,<br> [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, or [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> If the audio is played through the high-resolution pipeline, this operation is not supported.|
| [OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)](#oh_avplayer_seek) | - | Seeks to a playback position.<br> This function can be used when the AVPlayer is in the playing or paused state.|
| [OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)](#oh_avplayer_getcurrenttime) | - | Obtains the playback position, in milliseconds.|
| [OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)](#oh_avplayer_getvideowidth) | - | Obtains the video width.|
| [OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)](#oh_avplayer_getvideoheight) | - | Obtains the video height.|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)](#oh_avplayer_setplaybackspeed) | - | Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)](#oh_avplayer_setplaybackrate) | - | Sets the playback rate of an AVPlayer within the valid range.<br> The supported states are prepared, playing, paused, and completed.|
| [OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)](#oh_avplayer_getplaybackspeed) | - | Obtains the playback speed of an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)](#oh_avplayer_setaudiorendererinfo) | - | Sets the audio stream type for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)](#oh_avplayer_setvolumemode) | - | Sets the audio volume mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)](#oh_avplayer_setaudiointerruptmode) | - | Sets the audio interruption mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)](#oh_avplayer_setaudioeffectmode) | - | Sets the audio effect mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)](#oh_avplayer_selectbitrate) | - | Sets the bit rate used by an HLS player. This function is valid only for HLS network streams.<br> By default, the AVPlayer selects a proper bit rate and speed based on the network connection.<br> You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. The AVPlayer selects a bit rate that is lower than and closest to the specified bit rate. When ready, you can query the selected bit rate.|
| [OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosurface) | - | Sets a playback window.<br> This function must be called after **SetSource** and before **Prepare**.|
| [OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)](#oh_avplayer_getduration) | - | Obtains the total duration of a media file, in milliseconds.|
| [OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)](#oh_avplayer_getstate) | - | Obtains the AVPlayer state.|
| [bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)](#oh_avplayer_isplaying) | - | Checks whether an AVPlayer is playing.|
| [bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)](#oh_avplayer_islooping) | - | Checks whether an AVPlayer is looping.|
| [OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)](#oh_avplayer_setlooping) | - | Enables loop playback.|
| [OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)](#oh_avplayer_setplayercallback) | - | Sets an AVPlayer callback.<br> The callbacks [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set by using this function can transfer limited information. In addition, it is inconvenient for the application to distinguish between multiple AVPlayer instances.<br> Starting from API version 12, [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback) are provided to set the callbacks [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.|
| [OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_selecttrack) | - | Selects an audio or subtitle track.<br> By default, the first audio track with data is played, and the subtitle track is not played.<br> After the setting takes effect, the original track becomes invalid. Set the subtitle track to the prepared, playing, paused, or completed state, and set the audio track to the prepared state.|
| [OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_deselecttrack) | - | Deselects an audio or subtitle track.|
| [OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)](#oh_avplayer_getcurrenttrack) | - | Obtains the currently valid track. You can set the track to the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)](#oh_avplayer_setmediakeysysteminfocallback) | - | Sets a callback to return the media key system information for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)](#oh_avplayer_getmediakeysysteminfo) | - | Obtains the media key system information to create a media key session.|
| [OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)](#oh_avplayer_setdecryptionconfig) | - | Sets the decryption information.|
| [OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)](#oh_avplayer_setoninfocallback) | - | Sets a callback for the event indicating that the AVPlayer receives a message.|
| [OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)](#oh_avplayer_setonerrorcallback) | - | Sets a callback for the event indicating that an error occurs in the AVPlayer.|
| [OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)](#oh_avplayer_getmediadescription) | - | Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)](#oh_avplayer_gettrackdescription) | - | Obtains the media source track information for the AVPlayer by index. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|

## Function Description

### Player_MediaKeySystemInfoCallback()

```c
typedef void (*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)
```

**Description**

Called when media key system information of the AVPlayer is updated.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md)* mediaKeySystemInfo | Pointer to the media key system information.|

### OH_AVPlayer_Create()

```c
OH_AVPlayer *OH_AVPlayer_Create(void)
```

**Description**

Creates an OH_AVPlayer instance.

You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios.

<!--Del-->The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd-->

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) * | Pointer to the OH_AVPlayer instance created if the operation is successful; nullptr otherwise.<br> The possible causes of an operation failure are as follows:<br> 1. The execution of **PlayerFactory::CreatePlayer** fails.<br> 2. The execution of **new PlayerObject** fails.|

### OH_AVPlayer_SetURLSource()

```c
OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)
```

**Description**

Sets the HTTP URL of a media source to be played by an AVPlayer.  

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| const char *url | URL of the media source.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The setting is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, the input parameter **url** is null, or the execution of **player SetUrlSource** fails.|

### OH_AVPlayer_SetFDSource()

```c
OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets the file descriptor of a media source to be played by an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t fd | File descriptor of the media source.|
| int64_t offset | Offset of the media source in the file descriptor.|
| int64_t size | Size of the media source.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The file descriptor is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SetFdSource** fails.|

### OH_AVPlayer_SetDataSource()

```c
OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)
```

**Description**

Sets the media source of the AVPlayer. The data of this media source is provided by the application.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| OH_AVDataSourceExt* datasrc | Pointer to custom media data.|
| void* userData | Pointer to the handle, which is used in the callback. If **userData** is empty, the AVPlayer does not support multi-instance playback.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | **AV_ERR_OK**: The setting is successful.<br>         **AV_ERR_INVALID_VAL**: The **player** or **datasrc** parameter is nullptr.|

### OH_AVPlayer_Prepare()

```c
OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)
```

**Description**

Prepares the playback environment and buffers media data.<br> This function must be called after **SetSource**.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Prepare** fails.|

### OH_AVPlayer_Play()

```c
OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)
```

**Description**

Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare](#oh_avplayer_prepare).<br> In other words, you can call this function when the AVPlayer is in the prepared state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Play** fails.|

### OH_AVPlayer_Pause()

```c
OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)
```

**Description**

Pauses playback.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Pause** fails.|

### OH_AVPlayer_Stop()

```c
OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)
```

**Description**

Stops playback.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Stop** fails.|

### OH_AVPlayer_Reset()

```c
OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)
```

**Description**

Restores the AVPlayer to the initial state.<br> After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](#oh_avplayer_prepare) and [OH_AVPlayer_Play](#oh_avplayer_play) in sequence.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Reset** fails.|

### OH_AVPlayer_Release()

```c
OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)
```

**Description**

Asynchronously releases an OH_AVPlayer instance.<br> The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Release** fails.|

### OH_AVPlayer_ReleaseSync()

```c
OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)
```

**Description**

Synchronously releases an OH_AVPlayer instance.<br> The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player ReleaseSync** fails.|

### OH_AVPlayer_SetVolume()

```c
OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)
```

**Description**

Sets the volume for an AVPlayer.<br> This function can be used when the AVPlayer is in the playing or paused state. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| float leftVolume | Target volume of the left channel.|
| float rightVolume | Target volume of the right channel.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The volume is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SetVolume** fails.|

### OH_AVPlayer_SetLoudnessGain()

```c
OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)
```

**Description**

Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. The **usage** parameter of the AVPlayer stream must be [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC,<br> [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, or [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> If the audio is played through the high-resolution pipeline, this operation is not supported.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| float loudnessGain | Loudness, in the range [-90.0, 24.0], in dB.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The loudness is set successfully.<br>         **AV_ERR_INVALID_VAL**: The **player** parameter is nullptr, or the **loudnessGain** parameter is invalid.<br>         **AV_ERR_INVALID_STATE**: The function is called in an abnormal state, or the **usage** parameter in **audioRendererInfo** is not [StreamUsage](../apis-audio-kit/arkts-apis-audio-e.md#streamusage).STREAM_USAGE_MUSIC,<br>              [StreamUsage](../apis-audio-kit/arkts-apis-audio-e.md#streamusage).STREAM_USAGE_MOVIE, or [StreamUsage](../apis-audio-kit/arkts-apis-audio-e.md#streamusage).STREAM_USAGE_AUDIOBOOK.<br>         **AV_ERR_SERVICE_DIED**: A system error occurs.|

### OH_AVPlayer_Seek()

```c
OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)
```

**Description**

Seeks to a playback position.<br> This function can be used when the AVPlayer is in the playing or paused state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t mSeconds | Position to seek to, in ms.|
| [AVPlayerSeekMode](capi-avplayer-base-h.md#avplayerseekmode) mode | Seek mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Seek** fails.|

### OH_AVPlayer_GetCurrentTime()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)
```

**Description**

Obtains the playback position, in milliseconds.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t *currentTime | Pointer to the playback position.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback position is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetCurrentTime** fails.|

### OH_AVPlayer_GetVideoWidth()

```c
OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)
```

**Description**

Obtains the video width.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t *videoWidth | Pointer to the video width.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The video width is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_GetVideoHeight()

```c
OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)
```

**Description**

Obtains the video height.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t *videoHeight | Pointer to the video height.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The video height is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_SetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)
```

**Description**

Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) speed | Playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback speed is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_SetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)
```

**Description**

Sets the playback rate of an AVPlayer within the valid range.<br> The supported states are prepared, playing, paused, and completed.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| float rate | Playback rate. The value ranges from 0.125 to 4.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback speed is set successfully.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The function is called when the AVPlayer is not in the allowed state, or it is called during live streaming.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or **rate** is out of range.|

### OH_AVPlayer_GetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)
```

**Description**

Obtains the playback speed of an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) *speed | Pointer to the playback speed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback rate is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetPlaybackSpeed** fails.|

### OH_AVPlayer_SetAudioRendererInfo()

```c
OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)
```

**Description**

Sets the audio stream type for an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage) streamUsage | Audio stream type.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio stream type is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **streamUsage** is invalid.|

### OH_AVPlayer_SetVolumeMode()

```c
OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)
```

**Description**

Sets the audio volume mode for an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 18

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AudioStream_VolumeMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_volumemode) volumeMode | Volume mode of the audio stream.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio volume mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **volumeMode** is invalid.<br>         **AV_ERR_INVALID_STATE**: The function is called in an invalid state. It must be in the prepared state.<br>         **AV_ERR_SERVICE_DIED**: A system error occurs.|

### OH_AVPlayer_SetAudioInterruptMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)
```

**Description**

Sets the audio interruption mode for an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AudioInterrupt_Mode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_mode) interruptMode | Audio interruption mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio interruption mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **interruptMode** is invalid.|

### OH_AVPlayer_SetAudioEffectMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Sets the audio effect mode for an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AudioStream_AudioEffectMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode) effectMode | Audio effect mode.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio effect mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **effectMode** is invalid.|

### OH_AVPlayer_SelectBitRate()

```c
OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)
```

**Description**

Sets the bit rate used by an HLS player. This function is valid only for HLS network streams.<br> By default, the AVPlayer selects a proper bit rate and speed based on the network connection.<br> You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. The AVPlayer selects a bit rate that is lower than and closest to the specified bit rate. When ready, you can query the selected bit rate.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| uint32_t bitRate | Bit rate, in kbit/s.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The bit rate is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SelectBitRate** fails.|

### OH_AVPlayer_SetVideoSurface()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Sets a playback window.<br> This function must be called after **SetSource** and before **Prepare**.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| OHNativeWindow *window | Pointer to the OHNativeWindow instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback window is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** or **window** is nullptr, or the execution of **player SetVideoSurface** fails.|

### OH_AVPlayer_GetDuration()

```c
OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)
```

**Description**

Obtains the total duration of a media file, in milliseconds.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t *duration | Pointer to the total duration.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The total duration is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetDuration** fails.|

### OH_AVPlayer_GetState()

```c
OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)
```

**Description**

Obtains the AVPlayer state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [AVPlayerState](capi-avplayer-base-h.md#avplayerstate) *state | Pointer to the state of the AVPlayer.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The AVPlayer state is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetState** fails.|

### OH_AVPlayer_IsPlaying()

```c
bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is playing.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Check result for whether the AVPlayer is playing. **true** if yes, **false** if the AVPlayer is not playing or the input parameter **player** is nullptr.|

### OH_AVPlayer_IsLooping()

```c
bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is looping.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Check result for whether the AVPlayer is looping. **true** if yes, **false** if the AVPlayer is not looping or the input parameter **player** is nullptr.|

### OH_AVPlayer_SetLooping()

```c
OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)
```

**Description**

Enables loop playback.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| bool loop | Whether to enable loop playback. **true** to play in a loop, **false** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: Loop playback is enabled.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SetLooping** fails.|

### OH_AVPlayer_SetPlayerCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)
```

**Description**

Sets an AVPlayer callback.<br> The callbacks [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set by using this function can transfer limited information. In addition, it is inconvenient for the application to distinguish between multiple AVPlayer instances.<br> Starting from API version 12, [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback) are provided to set the callbacks [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Deprecated from**: 12

**Substitute**: [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback)

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) callback | Callback used to return the result.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The callback is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, the input parameter **callback.onInfo** or **onError** is null, or the execution of **player SetPlayerCallback** fails.|

### OH_AVPlayer_SelectTrack()

```c
OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Selects an audio or subtitle track.<br> By default, the first audio track with data is played, and the subtitle track is not played.<br> After the setting takes effect, the original track becomes invalid. Set the subtitle track to the prepared, playing, paused, or completed state, and set the audio track to the prepared state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t index | Index of the track.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SelectTrack** fails.|

### OH_AVPlayer_DeselectTrack()

```c
OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Deselects an audio or subtitle track.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t index | Index of the track.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player DeselectTrack** fails.|

### OH_AVPlayer_GetCurrentTrack()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)
```

**Description**

Obtains the currently valid track. You can set the track to the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| int32_t trackType | Media type. The value **0** means audio and **1** means video.|
| int32_t *index | Pointer to the index of the track.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The track is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetCurrentTrack** fails.|

### OH_AVPlayer_SetMediaKeySystemInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)
```

**Description**

Sets a callback to return the media key system information for an AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [Player_MediaKeySystemInfoCallback](#player_mediakeysysteminfocallback) callback | Callback.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** or **callback** is a null pointer, or the execution of **player SetDrmSystemInfoCallback**<br> **SetDrmSystemInfoCallback** or **SetDrmSystemInfoCallback** fails.|

### OH_AVPlayer_GetMediaKeySystemInfo()

```c
OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)
```

**Description**

Obtains the media key system information to create a media key session.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) *mediaKeySystemInfo | Pointer to the media key system information.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the memory is insufficient.|

### OH_AVPlayer_SetDecryptionConfig()

```c
OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)
```

**Description**

Sets the decryption information.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [MediaKeySession](capi-avplayer-mediakeysession.md) *mediaKeySession | Pointer to the media key session with the decryption feature.|
| bool secureVideoPath | Whether a secure decoder is required. **true** if required, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **SetDecryptionConfig** fails.|

### OH_AVPlayer_SetOnInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that the AVPlayer receives a message.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer messages is canceled.|
| void *userData | Pointer to the instance set by the caller.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_NO_MEMORY**: Memory allocation fails.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or the function fails to be executed.|

### OH_AVPlayer_SetOnErrorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that an error occurs in the AVPlayer.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer errors is canceled.|
| void *userData | Pointer to the instance set by the caller.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_NO_MEMORY**: Memory allocation fails.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or the function fails to be executed.|

### OH_AVPlayer_GetMediaDescription()

```c
OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)
```

**Description**

Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat](capi-videoprocessing-oh-avformat.md) * | Media source information obtained. If the operation fails, nullptr is returned.<br> Possible cause:<br>   1. The **player** pointer is invalid.<br>   2. The playback resource is invalid.|

### OH_AVPlayer_GetTrackDescription()

```c
OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)
```

**Description**

Obtains the media source track information for the AVPlayer by index. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance.|
| uint32_t index | Index of the track.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat](capi-videoprocessing-oh-avformat.md) * | Track information obtained. If the operation fails, nullptr is returned.<br> Possible cause:<br>   1. The **player** pointer is invalid.<br>   2. The playback resource is invalid.<br>   3. The track index is out of the range for the playback source file array.|
