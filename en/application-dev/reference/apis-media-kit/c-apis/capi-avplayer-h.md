# avplayer.h

## Overview

The **avplayer.h** file declares the AVPlayer APIs. You can use the native AVPlayer APIs to play a media asset.

**Library**: libavplayer.so

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [MediaKeySession](capi-avplayer-mediakeysession.md) | MediaKeySession | The MediaKeySession struct describes the media key session. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) | DRM_MediaKeySystemInfo | The DRM_MediaKeySystemInfo struct describes the media key system information. |
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) | OH_AVPlayerVideoOutput | OH_AVPlayerVideoOutput field. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)](#player_mediakeysysteminfocallback) | Player_MediaKeySystemInfoCallback | Called when media key system information of the AVPlayer is updated. |
| [OH_AVPlayer *OH_AVPlayer_Create(void)](#oh_avplayer_create) | - | Creates an OH_AVPlayer instance. You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios. <!--Del-->The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd--> |
| [OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_seturlsource) | - | Sets the HTTP URL of a media source to be played by an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_setfdsource) | - | Sets the file descriptor of a media source to be played by an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)](#oh_avplayer_setdatasource) | - | Sets the media source of the AVPlayer. The data of this media source is provided by the application. |
| [OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)](#oh_avplayer_prepare) | - | Prepares the playback environment and buffers media data. This function must be called after **SetSource**. |
| [OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)](#oh_avplayer_play) | - | Starts playback. This function must be called after [OH_AVPlayer_Prepare](capi-avplayer-h.md#oh_avplayer_prepare). In other words, you can call this function when the AVPlayer is in the prepared state. |
| [OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)](#oh_avplayer_pause) | - | Pauses playback. |
| [OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)](#oh_avplayer_stop) | - | Stops playback. |
| [OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)](#oh_avplayer_reset) | - | Restores the AVPlayer to the initial state. After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](capi-avplayer-h.md#oh_avplayer_prepare) and [OH_AVPlayer_Play](capi-avplayer-h.md#oh_avplayer_play) in sequence. |
| [OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)](#oh_avplayer_release) | - | Asynchronously releases an OH_AVPlayer instance. The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window. |
| [OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)](#oh_avplayer_releasesync) | - | Synchronously releases an OH_AVPlayer instance. The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism. |
| [OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)](#oh_avplayer_getmediadescription) | - | Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed. |
| [OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)](#oh_avplayer_gettrackdescription) | - | Obtains the media source track information for the AVPlayer by index. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed. |
| [OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)](#oh_avplayer_setvolume) | - | Sets the volume for an AVPlayer. This function can be used when the AVPlayer is in the playing or paused state. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used. |
| [OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)](#oh_avplayer_seek) | - | Seeks to a playback position. This function can be used when the AVPlayer is in the playing or paused state. |
| [OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)](#oh_avplayer_getcurrenttime) | - | Obtains the playback position, in milliseconds. |
| [OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)](#oh_avplayer_getvideowidth) | - | Obtains the video width. |
| [OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)](#oh_avplayer_getvideoheight) | - | Obtains the video height. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)](#oh_avplayer_setplaybackspeed) | - | Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). |
| [OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)](#oh_avplayer_getplaybackspeed) | - | Obtains the playback speed of an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)](#oh_avplayer_getplaybackrate) | - | Obtains the playback rate of an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)](#oh_avplayer_setaudiorendererinfo) | - | Sets the audio stream type for an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)](#oh_avplayer_setaudiointerruptmode) | - | Sets the audio interruption mode for an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)](#oh_avplayer_setaudioeffectmode) | - | Sets the audio effect mode for an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)](#oh_avplayer_selectbitrate) | - | Sets the bit rate used by an HLS player. This function is valid only for HLS network streams. By default, the AVPlayer selects a proper bit rate and speed based on the network connection. You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. The AVPlayer selects a bit rate that is lower than and closest to the specified bit rate. When ready, you can query the selected bit rate. |
| [OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosurface) | - | Sets a playback window. This function must be called after **SetSource** and before **Prepare**. |
| [OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)](#oh_avplayer_getduration) | - | Obtains the total duration of a media file, in milliseconds. |
| [OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)](#oh_avplayer_getstate) | - | Obtains the AVPlayer state. |
| [bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)](#oh_avplayer_isplaying) | - | Checks whether an AVPlayer is playing. |
| [bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)](#oh_avplayer_islooping) | - | Checks whether an AVPlayer is looping. |
| [OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)](#oh_avplayer_setlooping) | - | Enables loop playback. |
| [OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)](#oh_avplayer_setplayercallback) | - | Sets an AVPlayer callback. The callbacks [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set by using this function can transfer limited information. In addition, it is inconvenient for the application to distinguish between multiple AVPlayer instances. Starting from API version 12, [OH_AVPlayer_SetOnInfoCallback](capi-avplayer-h.md#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](capi-avplayer-h.md#oh_avplayer_setonerrorcallback) are provided to set the callbacks [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.(Deprecated in API12) |
| [OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_selecttrack) | - | Selects an audio or subtitle track. By default, the first audio track with data is played, and the subtitle track is not played. After the setting takes effect, the original track becomes invalid. Set the subtitle track to the prepared, playing, paused, or completed state, and set the audio track to the prepared state. |
| [OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_deselecttrack) | - | Deselects an audio or subtitle track. |
| [OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)](#oh_avplayer_getcurrenttrack) | - | Obtains the currently valid track. You can set the track to the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)](#oh_avplayer_setmediakeysysteminfocallback) | - | Sets a callback to return the media key system information for an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)](#oh_avplayer_getmediakeysysteminfo) | - | Obtains the media key system information to create a media key session. |
| [OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)](#oh_avplayer_setdecryptionconfig) | - | Sets the decryption information. |
| [OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)](#oh_avplayer_setoninfocallback) | - | Sets a callback for the event indicating that the AVPlayer receives a message. |
| [OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)](#oh_avplayer_setonerrorcallback) | - | Sets a callback for the event indicating that an error occurs in the AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)](#oh_avplayer_setvolumemode) | - | Sets the audio volume mode for an AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)](#oh_avplayer_setplaybackrate) | - | Sets the playback rate of an AVPlayer within the valid range. The supported states are prepared, playing, paused, and completed. |
| [OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)](#oh_avplayer_setloudnessgain) | - | Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state. The default loudness gain is 0.0 dB. The **usage** parameter of the AVPlayer stream must be {@link OH_AudioStream_Usage}.<br>AUDIOSTREAM_USAGE_MUSIC,<br>{@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_MOVIE, or {@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_AUDIOBOOK.<br>The latency mode of the audio renderer must be {@link OH_AudioStream_LatencyMode}.AUDIOSTREAM_LATENCY_MODE_NORMAL. If the audio is played through the high-resolution pipeline, this operation is not supported. |
| [OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)](#oh_avplayer_getplaybackstatisticmetrics) | - | Obtains the statistic metrics of the current AVPlayer. This API can be called when the playback resource is set and the AVPlayer is in the prepared, playing, paused, completed, or stopped state. Note that you need to manually release the lifecycle of the [OH_AVFormat](capi-core-oh-avformat.md) pointer object. |
| [OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_addfdsubtitlesource) | - | Adds the subtitle resource represented by the file descriptor to the player. Currently, the external subtitle must be set after the **fdSrc** of the video resource is set in the AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_addurlsubtitlesource) | - | Adds the subtitle resource represented by the URL to the player. The external subtitle must be set after the URL is set for the AVPlayer. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)](#oh_avplayer_setplaybackrange) | - | Sets the start and end positions of the playback. After the setting, only the content within the specified range of the audio and video file is played. This API can be called when the player is in the initialized, prepared, paused, stopped, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)](#oh_avplayer_setmediamuted) | - |  |
| [int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)](#oh_avplayer_getplaybackposition) | - | Obtains the playback position, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. |
| [bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)](#oh_avplayer_isseekcontinuoussupported) | - | Checks whether the media source supports continuous seek. If this API is called when the AVPlayer is in the prepared, playing, paused, or completed state, the actual value is returned. Other, **false** is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) mode, **false** is returned. |
| [OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)](#oh_avplayer_selecttrackwithmode) | - | Selects a track in the specified switching mode when playing a resource that contains multiple audio and video tracks. |
| [OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)](#oh_avplayer_setamplitudeupdatecallback) | - | Subscribes to the maximum audio amplitude update event, which is reported periodically when audio resources are played. |
| [OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)](#oh_avplayer_setseireceivedcallback) | - | Subscribes to the SEI message reception event. This API applies only to HTTP-FLV live streams and is triggered when an SEI message exists in a video stream. This subscription must be initiated before **prepare** is called. |
| [uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)](#oh_avseimessage_getseicount) | - | Obtains the number of items in the SEI message array. |
| [OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)](#oh_avseimessage_getsei) | - | Obtains an SEI message form the SEI message array by index. |
| [OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)](#oh_avplayer_settargetvideowindowsize) | - | Sets the video window size for super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. The input parameter value must be in the range of 320 × 320 to 1920 × 1080 (pixels). |
| [OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)](#oh_avplayer_setvideosuperresolutionenable) | - | Dynamically enables or disables super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must enable the super resolution feature in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling **prepare**. |
| [OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)](#oh_avplaybackstrategy_create) | - | Creates a playback strategy instance. |
| [OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)](#oh_avplaybackstrategy_destroy) | - | Releases a playback strategy instance. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)](#oh_avplaybackstrategy_setpreferredwidth) | - | Selects a stream with width close to the specified value. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)](#oh_avplaybackstrategy_setpreferredheight) | - | Selects a stream with height close to the specified value. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)](#oh_avplaybackstrategy_setpreferredbufferduration) | - | Selects the preferred buffer duration that is close to the specified value. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setpreferredhdr) | - | Enables or disables the preferred HDR mode. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredsubtitlelanguage) | - | Sets the preferred subtitle language. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredaudiolanguage) | - | Sets the preferred audio language. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)](#oh_avplaybackstrategy_setmutedmediatype) | - | Sets the media type to be muted during playback. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setshowfirstframeonprepare) | - | Sets whether to display the first frame during the **prepare** state. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setthresholdforautoquickplay) | - | Sets the threshold for automatic quick playback. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setsuperresolutionenable) | - | Sets whether to enable super resolution. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setpreferredbufferdurationforplaying) | - | Sets the preferred buffer duration during playback (double type, in seconds). |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setkeepdecodingonmute) | - | Sets whether to continue decoding when the audio is muted. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)](#oh_avplayer_setplaybackstrategy) | - | Sets the playback strategy for the AVPlayer. This API can be called only when the AVPlayer is in the initialized state. |
| [OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)](#oh_avplayer_getplaybackinfo) | - | Obtains the statistics of the current AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. |
| [OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)](#oh_avplayer_setmediasource) | - | Sets the **OH_AVMediaSource** to the AVPlayer. |
| [uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)](#oh_avplayer_gettrackcount) | - | Obtains the number of tracks of the media source of the AVPlayer. |
| [OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)](#oh_avplayer_gettrackformat) | - | Obtains the track information of the AVPlayer by index. |
| [OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)](#oh_avplayer_setpcmoutputcallback) | - | Method to set audio pcm data callback. This API can be called only when the avplayer is in the idle or initialized state. |
| [OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosideoutput) | - | Method to set video decoded frame output callback. This API can be called only when the avplayer is in the idle or initalized state. |
| [OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)](#oh_avplayervideooutput_getnewestvideosample) | - | Method to get one video decoded frame. This API can be called only when the avplayer is in the paused or playing state. |
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)](#oh_avplayer_setpcmprocessorcallback) | - | Method to set audio pcm data process callback. This API can be called only when the avplayer is in the idle or initialized state. |
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)](#oh_avplayer_setpcmprocessormaxlen) | - | Sets the maximum amount of data that can be returned at a time during audio post-processing. Allows some PCM data to be cached and returned with the next PCM data. This API can be called only when the avplayer is in the idle or initialized state. |

### Variable

| Name | Description |
| -- | -- |
| void (*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo) | Called when media key system information of the AVPlayer is updated.<br>**Since**: 12 |

## Function description

### Player_MediaKeySystemInfoCallback()

```c
typedef void (*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)
```

**Description**

Called when media key system information of the AVPlayer is updated.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to the OH_AVPlayer instance. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md)\* mediaKeySystemInfo | Pointer to the media key system information. |

### OH_AVPlayer_Create()

```c
OH_AVPlayer *OH_AVPlayer_Create(void)
```

**Description**

Creates an OH_AVPlayer instance. You are advised to create a maximum of 16 AVPlayer instances for an application in both audio and video playback scenarios. <!--Del-->The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd-->

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVPlayer * | Pointer to the OH_AVPlayer instance created if the operation is successful; nullptr otherwise.  The possible causes of an operation failure are as follows:  1. The execution of PlayerFactory::CreatePlayer fails.  2. The execution of new PlayerObject fails. |

### OH_AVPlayer_SetURLSource()

```c
OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)
```

**Description**

Sets the HTTP URL of a media source to be played by an AVPlayer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| const char *url | URL of the media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The setting is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, the input parameter url is null, or the  execution of player SetUrlSource fails. |

### OH_AVPlayer_SetFDSource()

```c
OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets the file descriptor of a media source to be played by an AVPlayer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t fd | File descriptor of the media source. |
| int64_t offset | Offset of the media source in the file descriptor. |
| int64_t size | Size of the media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The file descriptor is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player SetFdSource fails. |

### OH_AVPlayer_SetDataSource()

```c
OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)
```

**Description**

Sets the media source of the AVPlayer. The data of this media source is provided by the application.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance |
| OH_AVDataSourceExt* datasrc | Pointer to an OH_AVDataSourceExt instance |
| void* userData | The handle passed in by the user is used to pass in the callback |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The setting is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The player or datasrc parameter is nullptr. |

### OH_AVPlayer_Prepare()

```c
OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)
```

**Description**

Prepares the playback environment and buffers media data. This function must be called after **SetSource**.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Prepare fails. |

### OH_AVPlayer_Play()

```c
OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)
```

**Description**

Starts playback. This function must be called after [OH_AVPlayer_Prepare](capi-avplayer-h.md#oh_avplayer_prepare). In other words, you can call this function when the AVPlayer is in the prepared state.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Play fails. |

### OH_AVPlayer_Pause()

```c
OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)
```

**Description**

Pauses playback.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Pause fails. |

### OH_AVPlayer_Stop()

```c
OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)
```

**Description**

Stops playback.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Stop fails. |

### OH_AVPlayer_Reset()

```c
OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)
```

**Description**

Restores the AVPlayer to the initial state. After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](capi-avplayer-h.md#oh_avplayer_prepare) and [OH_AVPlayer_Play](capi-avplayer-h.md#oh_avplayer_play) in sequence.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Reset fails. |

### OH_AVPlayer_Release()

```c
OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)
```

**Description**

Asynchronously releases an OH_AVPlayer instance. The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Release fails. |

### OH_AVPlayer_ReleaseSync()

```c
OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)
```

**Description**

Synchronously releases an OH_AVPlayer instance. The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player ReleaseSync fails. |

### OH_AVPlayer_GetMediaDescription()

```c
OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)
```

**Description**

Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Media source information obtained. If the operation fails, nullptr is returned.  Possible cause:  1. The player pointer is invalid.  2. The playback resource is invalid. |

### OH_AVPlayer_GetTrackDescription()

```c
OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)
```

**Description**

Obtains the media source track information for the AVPlayer by index. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| uint32_t index | Index of the track. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Track information obtained. If the operation fails, nullptr is returned.  Possible cause:  1. The player pointer is invalid.  2. The playback resource is invalid.  3. The track index is out of the range for the playback source file array. |

### OH_AVPlayer_SetVolume()

```c
OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)
```

**Description**

Sets the volume for an AVPlayer. This function can be used when the AVPlayer is in the playing or paused state. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| float leftVolume | Target volume of the left channel. |
| float rightVolume | Target volume of the right channel. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The volume is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player SetVolume fails. |

### OH_AVPlayer_Seek()

```c
OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)
```

**Description**

Seeks to a playback position. This function can be used when the AVPlayer is in the playing or paused state.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t mSeconds | Position to seek to, in ms. |
| AVPlayerSeekMode mode | Seek mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player Seek fails. |

### OH_AVPlayer_GetCurrentTime()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)
```

**Description**

Obtains the playback position, in milliseconds.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t *currentTime | Pointer to the playback position. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The playback position is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player GetCurrentTime  fails. |

### OH_AVPlayer_GetVideoWidth()

```c
OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)
```

**Description**

Obtains the video width.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t *videoWidth | Pointer to the video width. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The video width is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr. |

### OH_AVPlayer_GetVideoHeight()

```c
OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)
```

**Description**

Obtains the video height.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t *videoHeight | Pointer to the video height. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The video height is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr. |

### OH_AVPlayer_SetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)
```

**Description**

Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| AVPlaybackSpeed speed | Playback speed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The playback speed is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr. |

### OH_AVPlayer_GetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)
```

**Description**

Obtains the playback speed of an AVPlayer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| AVPlaybackSpeed *speed | Pointer to the playback speed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The playback rate is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player GetPlaybackSpeed  fails. |

### OH_AVPlayer_GetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)
```

**Description**

Obtains the playback rate of an AVPlayer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| float *rate | Pointer to the playback rate that can be obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if the playback rate of the AVPlayer is successfully obtained.  Otherwise, an error code defined in {@link native_averrors.h} is returned. |

### OH_AVPlayer_SetAudioRendererInfo()

```c
OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)
```

**Description**

Sets the audio stream type for an AVPlayer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AudioStream_Usage streamUsage | Audio stream type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The audio stream type is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or streamUsage is invalid. |

### OH_AVPlayer_SetAudioInterruptMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)
```

**Description**

Sets the audio interruption mode for an AVPlayer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AudioInterrupt_Mode interruptMode | Audio interruption mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The audio interruption mode is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or interruptMode is invalid. |

### OH_AVPlayer_SetAudioEffectMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Sets the audio effect mode for an AVPlayer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AudioStream_AudioEffectMode effectMode | Audio effect mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The audio effect mode is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or effectMode is invalid. |

### OH_AVPlayer_SelectBitRate()

```c
OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)
```

**Description**

Sets the bit rate used by an HLS player. This function is valid only for HLS network streams. By default, the AVPlayer selects a proper bit rate and speed based on the network connection. You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. The AVPlayer selects a bit rate that is lower than and closest to the specified bit rate. When ready, you can query the selected bit rate.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| uint32_t bitRate | Bit rate, in kbit/s. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The bit rate is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player SelectBitRate  fails. |

### OH_AVPlayer_SetVideoSurface()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Sets a playback window. This function must be called after **SetSource** and before **Prepare**.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OHNativeWindow *window | Pointer to the OHNativeWindow instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The playback window is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player or window is nullptr, or the execution of player  SetVideoSurface fails. |

### OH_AVPlayer_GetDuration()

```c
OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)
```

**Description**

Obtains the total duration of a media file, in milliseconds.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t *duration | Pointer to the total duration. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The total duration is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player GetDuration fails. |

### OH_AVPlayer_GetState()

```c
OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)
```

**Description**

Obtains the AVPlayer state.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| AVPlayerState *state | Pointer to the state of the AVPlayer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The AVPlayer state is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player GetState fails. |

### OH_AVPlayer_IsPlaying()

```c
bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is playing.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Check result for whether the AVPlayer is playing. true if yes, false if the AVPlayer is not playing  or the input parameter player is nullptr. |

### OH_AVPlayer_IsLooping()

```c
bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is looping.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Check result for whether the AVPlayer is looping. true if yes, false if the AVPlayer is not looping  or the input parameter player is nullptr. |

### OH_AVPlayer_SetLooping()

```c
OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)
```

**Description**

Enables loop playback.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| bool loop | Whether to enable loop playback. **true** to play in a loop, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): Loop playback is enabled.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player SetLooping fails. |

### OH_AVPlayer_SetPlayerCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)
```

**Description**

Sets an AVPlayer callback. The callbacks [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set by using this function can transfer limited information. In addition, it is inconvenient for the application to distinguish between multiple AVPlayer instances. Starting from API version 12, [OH_AVPlayer_SetOnInfoCallback](capi-avplayer-h.md#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](capi-avplayer-h.md#oh_avplayer_setonerrorcallback) are provided to set the callbacks [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.

**Since**: 11

**Deprecated**: 12

**Replaced by**: [OH_AVPlayer_SetOnInfoCallback](capi-avplayer-h.md#oh_avplayer_setoninfocallback) [OH_AVPlayer_SetOnErrorCallback](capi-avplayer-h.md#oh_avplayer_setonerrorcallback)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| AVPlayerCallback callback | Callback used to return the result. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The callback is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, the input parameter callback.onInfo or   onError is null, or the execution of player SetPlayerCallback fails. |

### OH_AVPlayer_SelectTrack()

```c
OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Selects an audio or subtitle track. By default, the first audio track with data is played, and the subtitle track is not played. After the setting takes effect, the original track becomes invalid. Set the subtitle track to the prepared, playing, paused, or completed state, and set the audio track to the prepared state.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t index | Index of the track. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player SelectTrack fails. |

### OH_AVPlayer_DeselectTrack()

```c
OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Deselects an audio or subtitle track.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t index | Index of the track. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player DeselectTrack  fails. |

### OH_AVPlayer_GetCurrentTrack()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)
```

**Description**

Obtains the currently valid track. You can set the track to the prepared, playing, paused, or completed state.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t trackType | Media type. The value **0** means audio and **1** means video. |
| int32_t *index | Pointer to the index of the track. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The track is obtained.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of player GetCurrentTrack  fails. |

### OH_AVPlayer_SetMediaKeySystemInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)
```

**Description**

Sets a callback to return the media key system information for an AVPlayer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| [Player_MediaKeySystemInfoCallback](capi-avplayer-h.md#player_mediakeysysteminfocallback) callback | Callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player or callback is a null pointer, or the execution of   player SetDrmSystemInfoCallback  SetDrmSystemInfoCallback or SetDrmSystemInfoCallback fails. |

### OH_AVPlayer_GetMediaKeySystemInfo()

```c
OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)
```

**Description**

Obtains the media key system information to create a media key session.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) *mediaKeySystemInfo | Pointer to the media key system information. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the memory is insufficient. |

### OH_AVPlayer_SetDecryptionConfig()

```c
OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)
```

**Description**

Sets the decryption information.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| [MediaKeySession](capi-avplayer-mediakeysession.md) *mediaKeySession | Pointer to the media key session with the decryption feature. |
| bool secureVideoPath | Whether a secure decoder is required. **true** if required, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or the execution of SetDecryptionConfig fails. |

### OH_AVPlayer_SetOnInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that the AVPlayer receives a message.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AVPlayerOnInfoCallback callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer messages is canceled. |
| void *userData | Pointer to the instance set by the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  AV_ERR_NO_MEMORY: Memory allocation fails.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or the function fails to be executed. |

### OH_AVPlayer_SetOnErrorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that an error occurs in the AVPlayer.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AVPlayerOnErrorCallback callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer errors is canceled. |
| void *userData | Pointer to the instance set by the caller. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is successful.  AV_ERR_NO_MEMORY: Memory allocation fails.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or the function fails to be executed. |

### OH_AVPlayer_SetVolumeMode()

```c
OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)
```

**Description**

Sets the audio volume mode for an AVPlayer.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AudioStream_VolumeMode volumeMode | Volume mode of the audio stream. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The audio volume mode is set successfully.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr or volumeMode is invalid.  AV_ERR_INVALID_STATE: The function is called in an invalid state. It must be in the prepared state.  [AV_ERR_SERVICE_DIED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): A system error occurs. |

### OH_AVPlayer_SetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)
```

**Description**

Sets the playback rate of an AVPlayer within the valid range. The supported states are prepared, playing, paused, and completed.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| float rate | Playback rate. The value ranges is [0.125, 8.0], on API 24 and below, the range is [0.125, 4.0]. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The playback speed is set successfully.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The function is called when the AVPlayer is not in the allowed state, or it is called  during live streaming.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter player is nullptr, or rate is out of range. |

### OH_AVPlayer_SetLoudnessGain()

```c
OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)
```

**Description**

Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state. The default loudness gain is 0.0 dB. The **usage** parameter of the AVPlayer stream must be {@link OH_AudioStream_Usage}.<br>AUDIOSTREAM_USAGE_MUSIC,<br>{@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_MOVIE, or {@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_AUDIOBOOK.<br>The latency mode of the audio renderer must be {@link OH_AudioStream_LatencyMode}.AUDIOSTREAM_LATENCY_MODE_NORMAL. If the audio is played through the high-resolution pipeline, this operation is not supported.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| float loudnessGain | Loudness, in the range [-90.0, 24.0], in dB. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The loudness is set successfully.<br>[AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The player parameter is nullptr, or the loudnessGain parameter is invalid.<br>AV_ERR_INVALID_STATE: The function is called in an abnormal state, or the usage parameter of <br>audioRendererInfo is not one of the following:<br>{@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_MUSIC,<br>{@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_MOVIE,<br>and {@link OH_AudioStream_Usage}.AUDIOSTREAM_USAGE_AUDIOBOOKs.<br>[AV_ERR_SERVICE_DIED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): A system error occurs. |

### OH_AVPlayer_GetPlaybackStatisticMetrics()

```c
OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)
```

**Description**

Obtains the statistic metrics of the current AVPlayer. This API can be called when the playback resource is set and the AVPlayer is in the prepared, playing, paused, completed, or stopped state. Note that you need to manually release the lifecycle of the [OH_AVFormat](capi-core-oh-avformat.md) pointer object.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | If the operation is successful, the statistic metric information of the AVPlayer is returned. (For details  about the key values, see {@link statistic metric information}). Otherwise, nullptr is returned.  Possible failure cause: The input player pointer is invalid. |

### OH_AVPlayer_AddFdSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Adds the subtitle resource represented by the file descriptor to the player. Currently, the external subtitle must be set after the **fdSrc** of the video resource is set in the AVPlayer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance |
| int32_t fd | Indicates the file descriptor of subtitle source. |
| int64_t offset | Indicates the offset of media source in file descriptor. |
| int64_t size | Indicates the size of media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer. |

### OH_AVPlayer_AddUrlSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)
```

**Description**

Adds the subtitle resource represented by the URL to the player. The external subtitle must be set after the URL is set for the AVPlayer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| const char *url | URL of the subtitle source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer. |

### OH_AVPlayer_SetPlaybackRange()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)
```

**Description**

Sets the start and end positions of the playback. After the setting, only the content within the specified range of the audio and video file is played. This API can be called when the player is in the initialized, prepared, paused, stopped, or completed state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t mSecondsStart | Start position of playback. The value must be in the range of [0, **duration**). The value **-1*<br> indicates that the start position is not set, and the playback starts from 0. |
| int32_t mSecondsEnd | End position of playback. The value must be in the range of (**startTimeMs**, **duration**]. The value **-1** indicates that the end position is not set, and the playback ends at the end of the stream. |
| bool closestRange | Whether to seek to the frame closest to the specified position. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed. |

### OH_AVPlayer_SetMediaMuted()

```c
OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)
```

**Description**

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_MediaType mediaType | Media type. For details, see [OH_MediaType](../../apis-avcodec-kit/c-apis/capi-native-avcodec-base-h.md#oh_mediatype) in {@link native_avcodec_base.h}. |
| bool muted | **true** indicates that the audio is muted, and **false** indicates that the audio is unmuted. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed. |

### OH_AVPlayer_GetPlaybackPosition()

```c
int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)
```

**Description**

Obtains the playback position, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Playback position, in milliseconds.  If player is a null pointer or invalid, -1 is returned. |

### OH_AVPlayer_IsSeekContinuousSupported()

```c
bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)
```

**Description**

Checks whether the media source supports continuous seek. If this API is called when the AVPlayer is in the prepared, playing, paused, or completed state, the actual value is returned. Other, **false** is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) mode, **false** is returned.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | @returns true indicates that continuous seek is supported.  false indicates that continuous seek is not supported or is uncertain. |

### OH_AVPlayer_SelectTrackWithMode()

```c
OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)
```

**Description**

Selects a track in the specified switching mode when playing a resource that contains multiple audio and video tracks.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t index | Index of the selected track. |
| AVPlayerTrackSwitchMode mode | Switching mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input parameter is invalid.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed. |

### OH_AVPlayer_SetAmplitudeUpdateCallback()

```c
OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)
```

**Description**

Subscribes to the maximum audio amplitude update event, which is reported periodically when audio resources are played.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AVPlayerOnAmplitudeUpdateCallback callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer. |

### OH_AVPlayer_SetSeiReceivedCallback()

```c
OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)
```

**Description**

Subscribes to the SEI message reception event. This API applies only to HTTP-FLV live streams and is triggered when an SEI message exists in a video stream. This subscription must be initiated before **prepare** is called.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| const int32_t *payloadTypes | Load type array. |
| uint32_t typeNum | Size of the load type array. |
| OH_AVPlayerOnSeiMessageReceivedCallback callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered. |
| void *userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer. |

### OH_AVSeiMessage_GetSeiCount()

```c
uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)
```

**Description**

Obtains the number of items in the SEI message array.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVSeiMessageArray *message | Pointer to the **OH_AVSeiMessageArray** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Number of items in the SEI message array. |

### OH_AVSeiMessage_GetSei()

```c
OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)
```

**Description**

Obtains an SEI message form the SEI message array by index.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVSeiMessageArray *message | Pointer to the **OH_AVSeiMessageArray** instance. |
| uint32_t index | Index of the message item. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | SEI of the message item. |

### OH_AVPlayer_SetTargetVideoWindowSize()

```c
OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)
```

**Description**

Sets the video window size for super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. The input parameter value must be in the range of 320 × 320 to 1920 × 1080 (pixels).

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| int32_t width | Window width, in pixels. The value range is [320, 1920]. |
| int32_t height | Window height, in pixels. The value range is [320, 1080]. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer or the parameter is incorrect.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed.  [AV_ERR_SUPER_RESOLUTION_UNSUPPORTED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): Super resolution is not supported.  [AV_ERR_SUPER_RESOLUTION_NOT_ENABLED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): Super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md). |

### OH_AVPlayer_SetVideoSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)
```

**Description**

Dynamically enables or disables super resolution. This API can be called when the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state. You must enable the super resolution feature in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling **prepare**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| bool enabled | **true** means to enable super resolution; **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer or the parameter is incorrect.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed.  [AV_ERR_SUPER_RESOLUTION_UNSUPPORTED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): Super resolution is not supported.  [AV_ERR_SUPER_RESOLUTION_NOT_ENABLED](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): Super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md). |

### OH_AVPlaybackStrategy_Create()

```c
OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)
```

**Description**

Creates a playback strategy instance.

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVPlaybackStrategy * | Playback strategy instance. If the operation fails, a null pointer is returned. |

### OH_AVPlaybackStrategy_Destroy()

```c
OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)
```

**Description**

Releases a playback strategy instance.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | **OH_AVPlaybackStrategy** instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredWidth()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)
```

**Description**

Selects a stream with width close to the specified value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | **OH_AVPlaybackStrategy** used by the AVPlayer. |
| int32_t width | Preferred width for playback when the AVPlayer is started. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredHeight()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)
```

**Description**

Selects a stream with height close to the specified value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | **OH_AVPlaybackStrategy** used by the AVPlayer. |
| int32_t height | Preferred height for playback when the AVPlayer is started. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredBufferDuration()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)
```

**Description**

Selects the preferred buffer duration that is close to the specified value.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | **OH_AVPlaybackStrategy** used by the AVPlayer. |
| int32_t ms | Preferred buffer duration for playback when the AVPlayer is started. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredHdr()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Enables or disables the preferred HDR mode.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| bool enabled | The value **true** means to enable the preferred HDR mode, and the value **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred subtitle language.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| const char *lang | Pointer to subtitle language code (for example, **zh**). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredAudioLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred audio language.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| const char *lang | Pointer to audio language code (for example, **en**). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetMutedMediaType()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)
```

**Description**

Sets the media type to be muted during playback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| OH_MediaType mediaType | Type of the media to be muted. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to display the first frame during the **prepare** state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| bool enabled | **true** to display, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the threshold for automatic quick playback.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| double seconds | Threshold for automatic quick playback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to enable super resolution.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| bool enabled | **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the preferred buffer duration during playback (double type, in seconds).

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| double seconds | Buffer duration, in seconds. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetKeepDecodingOnMute()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to continue decoding when the audio is muted.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlaybackStrategy *strategy | Pointer to **OH_AVPlaybackStrategy**. |
| bool enabled | The value **true** means to continue decoding when the audio is muted, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input strategy is a null pointer. |

### OH_AVPlayer_SetPlaybackStrategy()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)
```

**Description**

Sets the playback strategy for the AVPlayer. This API can be called only when the AVPlayer is in the initialized state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AVPlaybackStrategy *strategy | Playback strategy instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player is a null pointer.  [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The operation is not allowed. |

### OH_AVPlayer_GetPlaybackInfo()

```c
OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)
```

**Description**

Obtains the statistics of the current AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, or paused state.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat* | Pointer to the OH_AVFormat instance.  If the player is a null pointer or invalid, a null pointer is returned. |

### OH_AVPlayer_SetMediaSource()

```c
OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)
```

**Description**

Sets the **OH_AVMediaSource** to the AVPlayer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| OH_AVMediaSource *source | Media source. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Execution result of the function.  [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The execution is successful.  [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode): The input player or source is a null pointer, or the player fails to set the URL  source. |

### OH_AVPlayer_GetTrackCount()

```c
uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)
```

**Description**

Obtains the number of tracks of the media source of the AVPlayer.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Number of tracks. |

### OH_AVPlayer_GetTrackFormat()

```c
OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)
```

**Description**

Obtains the track information of the AVPlayer by index.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to the OH_AVPlayer instance. |
| uint32_t trackIndex | Index of the track array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | Pointer to the OH_AVFormat instance.  If player is a null pointer or invalid, or trackIndex is invalid, a null pointer is returned. |

### OH_AVPlayer_SetPCMOutputCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)
```

**Description**

Method to set audio pcm data callback. This API can be called only when the avplayer is in the idle or initialized state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance. |
| OH_AVPlayerPCMOutputCallback callback | Pointer to callback function, nullptr indicates unregister callback. |
| void *userData | Pointer to user specific data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.          [AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if the execution is successful.          [AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if input player is null or player SetPCMOutputCallback failed.          [AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if called in unsupported state. |

### OH_AVPlayer_SetVideoSideOutput()

```c
OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Method to set video decoded frame output callback. This API can be called only when the avplayer is in the idle or initalized state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance. |
| OHNativeWindow *window | A pointer to a OHNativeWindow instance, see [OHNativeWindow](../../apis-avcodec-kit/c-apis/capi-codecbase-nativewindow.md) |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVPlayerVideoOutput*](capi-avplayer-oh-avplayervideooutput.md) | Returns a pointer to an OH_AVPlayerVideoOutput instance, released by system when avplayer was      reset or release. nullptr means failed. |

### OH_AVPlayerVideoOutput_GetNewestVideoSample()

```c
OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)
```

**Description**

Method to get one video decoded frame. This API can be called only when the avplayer is in the paused or playing state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) *videoOutput | Pointer to an OH_AVPlayerVideoOutput instance returned by OH_AVPlayer_SetVideoSideOutput. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_VideoOutputResult | Returns OH_VIDEO_OUTPUT_OK when got a frame.          Returns OH_VIDEO_OUTPUT_NO_IMAGE when there is no frame ready to render. |

### OH_AVPlayer_SetPCMProcessorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)
```

**Description**

Method to set audio pcm data process callback. This API can be called only when the avplayer is in the idle or initialized state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance. |
| OH_AVPlayerPCMProcessorCallback callback | Pointer to callback function, nullptr indicates unregister callback. |
| void *userData | Pointer to user specific data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.          <br>[AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if the execution is successful.          <br>[AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if input player is null or player SetPCMProcessorCallback failed.          <br>[AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if called in unsupported state. |

### OH_AVPlayer_SetPCMProcessorMaxLen()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)
```

**Description**

Sets the maximum amount of data that can be returned at a time during audio post-processing. Allows some PCM data to be cached and returned with the next PCM data. This API can be called only when the avplayer is in the idle or initialized state.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer *player | Pointer to an OH_AVPlayer instance. |
| int32_t maxProcessedPCMLen | the maximum amount of PCM data returned at one time, in the range (0, 5MB]. OH_AVPlayerPCMProcessorCallback ensures that the returned pcmBuffer's Capacity is not less than this value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | Function result code.          <br>[AV_ERR_OK](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if the execution is successful.          <br>[AV_ERR_INVALID_VAL](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if input player is null or maxProcessedPCMLen is error.          <br>[AV_ERR_OPERATE_NOT_PERMIT](../../apis-avcodec-kit/c-apis/capi-native-averrors-h.md#oh_averrcode) if called in unsupported state. |


