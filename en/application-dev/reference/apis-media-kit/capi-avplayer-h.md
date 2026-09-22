# avplayer.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

AVPlayer is an audio and video playback component that provides comprehensive playback control and advanced features (such as multi-track, subtitles, and DRM). It is suitable for scenarios such as video players, audio players, and live streaming apps. AVPlayer offers high-performance and low-latency media playback capabilities, simplifying development.

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
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) | OH_AVPlayerVideoOutput | Describes the video output of the AVPlayer.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Player_MediaKeySystemInfoCallback)(OH_AVPlayer \*player, DRM_MediaKeySystemInfo\* mediaKeySystemInfo)](#player_mediakeysysteminfocallback) | Player_MediaKeySystemInfoCallback | Called when media key system information of the AVPlayer is updated.|
| [OH_AVPlayer *OH_AVPlayer_Create(void)](#oh_avplayer_create) | - | Creates an **OH_AVPlayer** instance.<br> You are advised to create a maximum of 16 AVPlayer instances for an application.<!--Del--><br> The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd--> |
| [OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_seturlsource) | - | Sets the HTTP URL of a media source to be played by an AVPlayer. The source can be an HTTP or HTTPS URL.|
| [OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_setfdsource) | - | Sets the file descriptor of a media source to be played by an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer \*player, OH_AVDataSourceExt\* datasrc, void* userData)](#oh_avplayer_setdatasource) | - | Sets the media source of the AVPlayer. The data of this media source is provided by the application.|
| [OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)](#oh_avplayer_prepare) | - | Prepares the playback environment and buffers media data.<br> This function must be called after **SetSource**.|
| [OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)](#oh_avplayer_play) | - | Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare](#oh_avplayer_prepare).<br> In other words, you can call this function when the AVPlayer is in the prepared state.|
| [OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)](#oh_avplayer_pause) | - | Pauses playback. This function can be called when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)](#oh_avplayer_stop) | - | Stops playback. This function can be called when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)](#oh_avplayer_reset) | - | Restores the AVPlayer to the initial state.<br> After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](#oh_avplayer_prepare) and [OH_AVPlayer_Play](#oh_avplayer_play) in sequence.|
| [OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)](#oh_avplayer_release) | - | Asynchronously releases an **OH_AVPlayer** instance.<br> The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window.|
| [OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)](#oh_avplayer_releasesync) | - | Synchronously releases an **OH_AVPlayer** instance.<br> The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism.|
| [OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)](#oh_avplayer_setvolume) | - | Sets the volume for an AVPlayer.<br> This function can be used when the AVPlayer is in the playing or paused state. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used. The default volume is 1.|
| [OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)](#oh_avplayer_setloudnessgain) | - | Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. **usage** of the AVPlayer stream must be one of the following enumerated values: [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC, [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, and [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> If the audio is played through the high-resolution pipeline, this operation is not supported.|
| [OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)](#oh_avplayer_seek) | - | Seeks to a playback position.<br> This function can be used when the AVPlayer is in the playing or paused state.|
| [OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)](#oh_avplayer_getcurrenttime) | - | Obtains the current playback time (returned through a parameter), accurate to milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)](#oh_avplayer_getvideowidth) | - | Obtains the video width. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)](#oh_avplayer_getvideoheight) | - | Obtains the video height. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)](#oh_avplayer_setplaybackspeed) | - | Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). The default playback rate is 1.0x (normal speed).|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)](#oh_avplayer_setplaybackrate) | - | Sets the playback rate of an AVPlayer within the valid range.<br> The prepared, playing, paused, and completed states are supported. The default playback rate is 1.0x (normal speed).|
| [OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)](#oh_avplayer_getplaybackspeed) | - | Obtains the playback speed of an AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)](#oh_avplayer_getplaybackrate) | - | Obtains the playback rate of an AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)](#oh_avplayer_setaudiorendererinfo) | - | Sets the audio stream type for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)](#oh_avplayer_setvolumemode) | - | Sets the audio volume mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)](#oh_avplayer_setaudiointerruptmode) | - | Sets the audio interruption mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)](#oh_avplayer_setaudioeffectmode) | - | Sets the audio effect mode for an AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)](#oh_avplayer_selectbitrate) | - | Sets the bit rate used by an HLS player. This function is valid only for HLS network streams. This API can be called only when the AVPlayer is in the prepared, playing, or paused state.<br> By default, the AVPlayer selects a proper bit rate and speed based on the network connection.<br> You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. If the bit rate specified by the user is not in the list, the player selects a bit rate that is closest to the specified bit rate.|
| [OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosurface) | - | Sets a playback window.<br> This function must be called after **SetSource** and before **Prepare**.|
| [OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)](#oh_avplayer_getduration) | - | Obtains the total duration of a media file, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)](#oh_avplayer_getstate) | - | Obtains the AVPlayer state.|
| [bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)](#oh_avplayer_isplaying) | - | Checks whether an AVPlayer is playing. This function can be called when an AVPlayer is in any state. However, the validity of the returned result depends on the current state.|
| [bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)](#oh_avplayer_islooping) | - | Checks whether an AVPlayer is looping. This function can be called when an AVPlayer is in any state.|
| [OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)](#oh_avplayer_setlooping) | - | Enables loop playback. Loop playback is disabled by default.|
| [OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)](#oh_avplayer_setplayercallback) | - | Sets an AVPlayer callback.<br> The callbacks [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set by using this function can transfer limited information. In addition, it is inconvenient for the application to distinguish between multiple AVPlayer instances.<br> Starting from API version 12, [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback) are provided to set the callbacks [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.<br>This API has been deprecated since API version 12.|
| [OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_selecttrack) | - | Selects an audio or subtitle track.<br> By default, the first audio track with data is played, and the subtitle track is not played.<br> After the setting takes effect, the original track becomes invalid. When selecting a subtitle track, ensure that the player is in the prepared, playing, paused, or completed state. When selecting an audio track, ensure that the player is in the prepared state.|
| [OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_deselecttrack) | - | Deselects an audio or subtitle track. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)](#oh_avplayer_getcurrenttrack) | - | Obtains the currently valid track. When this API is called, the AVPlayer must be in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)](#oh_avplayer_setmediakeysysteminfocallback) | - | Sets a callback to return the media key system information for an AVPlayer. This method is applicable to the playback of DRM-encrypted media content, for example, listening for DRM information updates, obtaining keys for encrypted content, and processing copyright-protected content.|
| [OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)](#oh_avplayer_getmediakeysysteminfo) | - | Obtains the media key system information to create a media key session.|
| [OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)](#oh_avplayer_setdecryptionconfig) | - | Sets the decryption information. This method is applicable to scenarios where media content is encrypted using DRM, such as playing encrypted videos, paid content, or media resources protected by copyright.|
| [OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)](#oh_avplayer_setoninfocallback) | - | Sets a callback for the event indicating that the AVPlayer receives a message.|
| [OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)](#oh_avplayer_setonerrorcallback) | - | Sets a callback for the event indicating that an error occurs in the AVPlayer.|
| [OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)](#oh_avplayer_getmediadescription) | - | Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)](#oh_avplayer_gettrackdescription) | - | Obtains the media source track information for the AVPlayer by index. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_addfdsubtitlesource) | - | Adds the subtitle resource of the file descriptor to the player. Currently, the external subtitle must be set after the **fdSrc** of the video resource is set in the AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_addurlsubtitlesource) | - | Adds the subtitle resource of the URL to the player. The external subtitle must be set after the URL is set for the AVPlayer.|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)](#oh_avplayer_setplaybackrange) | - | Sets the start and end positions of the playback. Only the content within the specified range is played. This API can be called when the player is in the initialized, prepared, paused, stopped, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)](#oh_avplayer_setmediamuted) | - | Mutes the media stream. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)](#oh_avplayer_getplaybackposition) | - | Obtains the playback position, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)](#oh_avplayer_isseekcontinuoussupported) | - | Checks whether the media source supports continuous seek. If this API is called when the AVPlayer is in the prepared, playing, paused, or completed state, the actual value is returned. Other, **false** is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) mode, **false** is returned.|
| [OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)](#oh_avplayer_selecttrackwithmode) | - | Selects a track in the specified switching mode when playing a resource that contains multiple audio and video tracks. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)](#oh_avplayer_setamplitudeupdatecallback) | - | Subscribes to the maximum audio amplitude update event, which is reported periodically when audio resources are played. This API is applicable to scenarios where audio visualization or audio intensity detection is required, such as audio waveform display, audio intensity visualization, and audio energy detection.|
| [OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)](#oh_avplayer_setseireceivedcallback) | - | Subscribes to the SEI message reception event. This API applies only to HTTP-FLV live streams and is triggered when an SEI message exists in a video stream. This subscription must be initiated before **prepare** is called.|
| [uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)](#oh_avseimessage_getseicount) | - | Obtains the number of items in the SEI message array.|
| [OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)](#oh_avseimessage_getsei) | - | Obtains an SEI message form the SEI message array by index. You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)](#oh_avplayer_settargetvideowindowsize) | - | Sets the video window size for super resolution. This method can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. The input parameter value must be in the range of 320 × 320 to 1920 × 1080, in pixels. This method is applicable to scenarios where super resolution is used for video display, such as low-resolution video quality enhancement and video enhancement.|
| [OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)](#oh_avplayer_setvideosuperresolutionenable) | - | Dynamically enables or disables super resolution. This method can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. You must enable the super resolution feature in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling **prepare**. This method is applicable to scenarios where video quality enhancement needs to be dynamically controlled, for example, dynamically adjusting the quality based on the device performance or switching the quality based on the network status.|
| [OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)](#oh_avplaybackstrategy_create) | - | Creates a playback strategy instance.|
| [OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)](#oh_avplaybackstrategy_destroy) | - | Releases a playback strategy instance.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)](#oh_avplaybackstrategy_setpreferredwidth) | - | Selects a stream with width close to the specified value.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)](#oh_avplaybackstrategy_setpreferredheight) | - | Selects a stream with height close to the specified value.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)](#oh_avplaybackstrategy_setpreferredbufferduration) | - | Selects the preferred buffer duration that is close to the specified value.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setpreferredhdr) | - | Enables or disables the preferred HDR mode.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredsubtitlelanguage) | - | Sets the preferred subtitle language.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredaudiolanguage) | - | Sets the preferred audio language.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)](#oh_avplaybackstrategy_setmutedmediatype) | - | Sets the media type to be muted during playback.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setshowfirstframeonprepare) | - | Sets whether to display the first frame during the **prepare** state.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setthresholdforautoquickplay) | - | Sets the threshold for automatic quick playback. When the buffered data is insufficient and stuttering may occur during playback, the player automatically increases the playback rate to quickly play the buffered content. This threshold is used to control the condition for triggering this behavior.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setsuperresolutionenable) | - | Sets whether to enable super resolution.|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setpreferredbufferdurationforplaying) | - | Sets the preferred buffer duration during playback (double type, in seconds).|
| [OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setkeepdecodingonmute) | - | Sets whether to continue decoding when the audio is muted.|
| [OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)](#oh_avplayer_setplaybackstrategy) | - | Sets the playback strategy for the AVPlayer. This API can be called only when the AVPlayer is in the initialized state.|
| [OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)](#oh_avplayer_getplaybackinfo) | - | Obtains the statistics of the current AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)](#oh_avplayer_setmediasource) | - | Sets the **OH_AVMediaSource** to the AVPlayer.|
| [uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)](#oh_avplayer_gettrackcount) | - | Obtains the number of tracks of the media source of the AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.|
| [OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)](#oh_avplayer_gettrackformat) | - | Obtains the track information of the AVPlayer by index. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed.|
| [OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)](#oh_avplayer_getplaybackstatisticmetrics) | - | Obtains the statistic metrics of the current AVPlayer. This function can be called when the playback resource has been set and the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> Note that you need to manually release the lifecycle of the [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) pointer object.|
| [OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)](#oh_avplayer_setpcmoutputcallback) | - | Sets the callback for audio PCM data output. This API can be called when the AVPlayer is in the idle or initialized state. This API is applicable to scenarios where raw audio data needs to be obtained, such as audio data analysis, audio recording, audio processing, and audio visualization.|
| [OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosideoutput) | - | Sets the callback for decoded video frame output. This API can be called when the AVPlayer is in the idle or initialized state. This API is applicable to scenarios where decrypted video frames need to be obtained, such as video frame analysis, video filter processing, video snapshot, and video special effect processing.|
| [OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)](#oh_avplayervideooutput_getnewestvideosample) | - | Obtains a decoded video frame. This API can be called when the AVPlayer is in the paused or playing state. This API is applicable to scenarios where the current video frame needs to be obtained, such as video frame capture, video frame analysis, video snapshot, and video frame processing.|
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)](#oh_avplayer_setpcmprocessorcallback) | - | Sets the callback for audio PCM data postprocessing. This API can be called when the AVPlayer is in the idle or initialized state.|
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)](#oh_avplayer_setpcmprocessormaxlen) | - | Sets the maximum amount of data that can be returned at a time by the audio postprocessing callback. Some data can be cached and output together with the PCM data returned next time.<br> This API can be called when the AVPlayer is in the idle or initialized state.|

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md)* mediaKeySystemInfo | DRM media key system information, including the key system ID and session ID. This parameter is used to receive and transfer DRM information when encrypted content is played.|

### OH_AVPlayer_Create()

```c
OH_AVPlayer *OH_AVPlayer_Create(void)
```

**Description**

Creates an **OH_AVPlayer** instance.<br> You are advised to create a maximum of 16 AVPlayer instances for an application.<br> <!--Del-->The actual number of instances that can be created may be different. It depends on the specifications of the device chip in use. For example, in the case of RK3568, you are advised to create a maximum of 6 AVPlayer instances for an application in audio and video playback scenarios.<!--DelEnd-->

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) * | Pointer to the **OH_AVPlayer** instance created if the operation is successful; nullptr otherwise.<br> The possible causes of an operation failure are as follows:<br> 1. The execution of **PlayerFactory::CreatePlayer** fails.<br> 2. The execution of **new PlayerObject** fails.|

### OH_AVPlayer_SetURLSource()

```c
OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)
```

**Description**

Sets the HTTP URL of a media source to be played by an AVPlayer. The source can be an HTTP or HTTPS URL. After the setting is complete, you can call **OH_AVPlayer_AddUrlSubtitleSource** to add external subtitles. It is applicable to scenarios such as network video playback, online audio playback, and livestreaming.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| const char *url | URL of the playback source. Network URLs complying with the HTTP/HTTPS protocol are supported.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The setting is successful.<br>**AV_ERR_INVALID_VAL**: The input **player** is a null pointer, **url** is null or in an incorrect format, or the playback source fails to be set. Check whether the URL format is correct, whether the network is available, and whether the resource exists.|

### OH_AVPlayer_SetFDSource()

```c
OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets the file descriptor of a media source to be played by an AVPlayer. After the setting is complete, you can call **OH_AVPlayer_AddFdSubtitleSource** to add external subtitles. This method applies to scenarios such as playing files in the app sandbox, encrypted media files, and segmented media files.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t fd | File descriptor of the media source.|
| int64_t offset | Offset of the media source in the file descriptor, in bytes.|
| int64_t size | Size of the media source, in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The file descriptor is set successfully.<br>**AV_ERR_INVALID_VAL**: The input **player** is a null pointer, **fd** is invalid, **offset** or **size** is incorrect, or the **SetFdSource** execution fails. Check whether the file descriptor is valid and whether the offset and size are within the file range.|

### OH_AVPlayer_SetDataSource()

```c
OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)
```

**Description**

Sets the media source of the AVPlayer. The data of this media source is provided by the application. This method applies to scenarios where a custom data source is required, such as custom protocol playback, dynamic decryption stream playback, and playback of media data generated within the application.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVDataSourceExt](../apis-avcodec-kit/capi-codecbase-oh-avdatasourceext.md)* datasrc | Pointer to custom media data.|
| void* userData | Pointer to the handle, which is used in the callback. If **userData** is empty, the AVPlayer does not support multi-instance playback.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The setting is successful.<br>         **AV_ERR_INVALID_VAL**: The **player** or **datasrc** parameter is nullptr.|

### OH_AVPlayer_Prepare()

```c
OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)
```

**Description**

Prepares the playback environment and buffers media data.<br> This function must be called after **SetSource**. To subscribe to SEI messages, you must call **OH_AVPlayer_SetSeiReceivedCallback** before calling this function. This function applies to scenarios such as preloading media before playback and buffering network streams in advance.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>**AV_ERR_INVALID_VAL**: The input **player** is a null pointer, or **Prepare** fails to be executed. Check whether a valid playback source has been set, whether the format of the playback source is supported, and whether the memory is sufficient.|

### OH_AVPlayer_Play()

```c
OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)
```

**Description**

Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare](#oh_avplayer_prepare).<br> In other words, you can call this function when the AVPlayer is in the prepared state. It is applicable to scenarios such as tapping the play button, automatically playing a video, and playing audio.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Play** fails.|

### OH_AVPlayer_Pause()

```c
OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)
```

**Description**

Pauses playback. This function can be called when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as tapping the pause button, pausing when the app loses focus, and pausing when a call interrupts.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Pause** fails.|

### OH_AVPlayer_Stop()

```c
OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)
```

**Description**

Stops playback. This function can be called when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as tapping the stop button, switching the playback content, and releasing player resources.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Stop** fails.|

### OH_AVPlayer_Reset()

```c
OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)
```

**Description**

Restores the AVPlayer to the initial state.<br> After the function is called, you can call **SetSource** to set the media source to play, and then call [OH_AVPlayer_Prepare](#oh_avplayer_prepare) and [OH_AVPlayer_Play](#oh_avplayer_play) in sequence. It is applicable to scenarios such as switching the playback source, re-playing, and recovering from a playback error.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Reset** fails.|

### OH_AVPlayer_Release()
```c
OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)
```

**Description**

Asynchronously releases an **OH_AVPlayer** instance.<br> The asynchronous function improves performance, but cannot ensure that the surface buffer of the playback window is released. You must ensure the lifecycle of the playback window. This function is applicable to scenarios where resources need to be quickly released, such as exiting the playback page or destroying the player instance.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Release** fails.|

### OH_AVPlayer_ReleaseSync()

```c
OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)
```

**Description**

Synchronously releases an **OH_AVPlayer** instance.<br> The synchronous function ensures that the display buffer of the playback window is released, with a long time. Therefore, you need to design an asynchronous mechanism. This function is applicable to scenarios where you need to ensure that the playback window is completely released, for example, clearing resources before an app exits or switching to a non-playback page.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player ReleaseSync** fails.|

### OH_AVPlayer_SetVolume()

```c
OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)
```

**Description**

Sets the volume for an AVPlayer.<br> This function can be used when the AVPlayer is in the playing or paused state. The value **0** indicates no sound. The default volume is 1. If this API is not called to set the volume, the default value is used.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance. This function can be used when the AVPlayer is in the playing or paused state.|
| float leftVolume | Target volume of the left channel. The value range is [0.0, 1.0]. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used.|
| float rightVolume | Target volume of the right channel. The value range is [0.0, 1.0]. The value **0** means that the AVPlayer is muted, and **1** means that the original volume is used.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The volume is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SetVolume** fails.|

### OH_AVPlayer_SetLoudnessGain()

```c
OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)
```

**Description**

Sets the loudness of the AVPlayer. This function can be called when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. If this API is not called to set the loudness, the default value is used. **usage** of the AVPlayer stream must be one of the following enumerated values: [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC, [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, and [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> If the audio is played through the high-resolution pipeline, this operation is not supported.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance, which must be used when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.|
| float loudnessGain | Loudness, in the range [-90.0, 24.0], in dB.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The loudness is set successfully.<br>**AV_ERR_INVALID_VAL**: The **player** parameter is nullptr, or the **loudnessGain** parameter is invalid.<br>**AV_ERR_INVALID_STATE**: The function is called in an abnormal state, or the **usage** parameter of **audioRendererInfo** is not one of the following:<br>[OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC,<br>[OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE,<br>and [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOKs.<br>**AV_ERR_SERVICE_DIED**: The system service is terminated unexpectedly. Check the system service status, create a player instance again, and try again. If the issue persists, check the system resources or restart the app.|

### OH_AVPlayer_Seek()

```c
OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)
```

**Description**

Seeks to a playback position.<br> This function can be used when the AVPlayer is in the playing or paused state. It is applicable to scenarios such as dragging the progress bar, fast-forwarding and rewinding the playback, jumping to a chapter, and resuming the playback position.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t mSeconds | Position to seek to, in ms. The value range is [0, **duration**], where **duration** indicates the total duration of the media file. If the value is out of the range, the seek operation may fail.|
| [AVPlayerSeekMode](capi-avplayer-base-h.md#avplayerseekmode) mode | Seek mode. For details about the options and use scenarios, see the definitions in [AVPlayerSeekMode](capi-avplayer-base-h.md#avplayerseekmode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player Seek** fails.|

### OH_AVPlayer_GetCurrentTime()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)
```

**Description**

Obtains the current playback time (returned through a parameter), accurate to milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as progress bar display, playback time statistics, and resumable playback recording.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t *currentTime | Current playback position (output parameter). The unit is ms.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback position is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetCurrentTime** fails.|

### OH_AVPlayer_GetVideoWidth()

```c
OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)
```

**Description**

Obtains the video width. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This method is applicable to scenarios such as video size adaptation, adaptive layout, and image ratio calculation.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t *videoWidth | Video width (output parameter), in px.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The video width is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_GetVideoHeight()

```c
OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)
```

**Description**

Obtains the video height. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This method is applicable to scenarios such as video size adaptation, adaptive layout, and image ratio calculation.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t *videoHeight | Video height (output parameter), in px.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The video height is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_SetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)
```

**Description**

Sets the playback speed of the AVPlayer. For details about the playback speed, see [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). The prepared, playing, paused, and completed states are supported. The default playback rate is 1.0x (normal speed). If this API is not called to set the playback rate, the default value is used.<br> Differences: [OH_AVPlayer_SetPlaybackRate](#oh_avplayer_setplaybackrate) can also be used to set the playback rate, but more flexible rates can be set using the float type. This method uses fixed enumeration levels and is suitable for standard playback scenarios. **SetPlaybackRate** is suitable for scenarios where the playback rate needs to be precisely controlled. It is applicable to scenarios such as variable-speed playback, slow-motion playback, and fast-forward preview.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) speed | Playback speed. For details about the options and use scenarios, see the definitions in [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback speed is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr.|

### OH_AVPlayer_SetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)
```

**Description**

Sets the playback rate of an AVPlayer within the valid range.<br> The prepared, playing, paused, and completed states are supported. The default playback rate is 1.0x (normal speed). If this API is not called to set the playback rate, the default value is used.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 20

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance. The prepared, playing, paused, and completed states are supported.|
| float rate | Playback rate. The value range is [0.125, 8.0] for API version 26.0.0 or later and [0.125, 4.0] for API versions earlier than 26.0.0. A value less than 1.0 (the normal speed) is suitable for slow playback (such as learning and analysis), and a value greater than 1.0 is suitable for fast browsing.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback speed is set successfully.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: This method is called in an unsupported state or during livestreaming.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer, or the configured rate is out of range.|

### OH_AVPlayer_GetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)
```

**Description**

Obtains the playback speed of an AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.<br> **Differences:** [OH_AVPlayer_GetPlaybackRate](#oh_avplayer_getplaybackrate) can also be used to obtain the playback rate, but it returns a value of the float type. This method returns an enumerated value of **AVPlaybackSpeed** and can be used with **SetPlaybackSpeed**. **GetPlaybackRate** returns an accurate value and is suitable for scenarios where accurate rate information is required.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) *speed | Current playback rate of the player (output parameter).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback rate is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetPlaybackSpeed** fails.|

### OH_AVPlayer_GetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)
```

**Description**

Obtains the playback rate of an AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| float *rate | Pointer to the playback rate. A multiple of the playback rate of the current player is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback rate of the current AVPlayer is successfully obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **GetPlaybackRate** fails.|

### OH_AVPlayer_SetAudioRendererInfo()

```c
OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)
```

**Description**

Sets the audio stream type for an AVPlayer. This API can be called only when the AVPlayer is in the idle or initialized state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage) streamUsage | Audio stream type. For details about the options and use scenarios, see the definitions in [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio stream type is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **streamUsage** is invalid.|

### OH_AVPlayer_SetVolumeMode()

```c
OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)
```

**Description**

Sets the audio volume mode for an AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, completed, or stopped state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 19

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AudioStream_VolumeMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_volumemode) volumeMode | Volume mode of the audio stream. For details about the options and use scenarios, see the definitions in [OH_AudioStream_VolumeMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_volumemode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio volume mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **volumeMode** is invalid.<br>         **AV_ERR_INVALID_STATE**: The function is called in an invalid state. It must be in the prepared state.<br>         **AV_ERR_SERVICE_DIED**: The system service is terminated unexpectedly. Check the system service status, create a player instance again, and try again. If the issue persists, check the system resources or restart the app.|

### OH_AVPlayer_SetAudioInterruptMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)
```

**Description**

Sets the audio interruption mode for an AVPlayer. This API can be called only when the AVPlayer is in the idle or initialized state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AudioInterrupt_Mode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_mode) interruptMode | Audio interruption mode. For details about the options and use scenarios, see the definitions in [OH_AudioInterrupt_Mode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_mode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio interruption mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **interruptMode** is invalid.|

### OH_AVPlayer_SetAudioEffectMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Sets the audio effect mode for an AVPlayer. This API can be called only when the AVPlayer is in the idle or initialized state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AudioStream_AudioEffectMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode) effectMode | Audio effect mode. For details about the options and use scenarios, see the definitions in [OH_AudioStream_AudioEffectMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The audio effect mode is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or **effectMode** is invalid.|

### OH_AVPlayer_SelectBitRate()

```c
OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)
```

**Description**

Sets the bit rate used by an HLS player. This function is valid only for HLS network streams. This API can be called only when the AVPlayer is in the prepared, playing, or paused state.<br> By default, the AVPlayer selects a proper bit rate and speed based on the network connection.<br> You can set a bit rate available in the valid bit rates reported in **INFO_TYPE_BITRATE_COLLECT**. If the bit rate specified by the user is not in the list, the player selects a bit rate that is closest to the specified bit rate. It is applicable to scenarios such as manually switching the definition, optimizing the network bandwidth, and saving mobile data.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance. This API can be called only when the AVPlayer is in the prepared, playing, or paused state.|
| uint32_t bitRate | Bit rate, in bit/s. You can select a proper bit rate based on the network bandwidth. A low bit rate can be selected at a low bandwidth, and a high bit rate can be selected at a high bandwidth. By default, the player automatically selects a proper bit rate.|

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance. This function must be called after **SetSource** and before **Prepare**.|
| [OHNativeWindow](../apis-avcodec-kit/capi-codecbase-nativewindow.md) *window | Pointer to the **OHNativeWindow** instance. This parameter must be called after **SetSource** and before **Prepare**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The playback window is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** or **window** is nullptr, or the execution of **player SetVideoSurface** fails.|

### OH_AVPlayer_GetDuration()

```c
OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)
```

**Description**

Obtains the total duration of a media file, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t *duration | Total duration of a media file (output parameter), in ms.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The total duration is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetDuration** fails.|

### OH_AVPlayer_GetState()

```c
OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)
```

**Description**

Obtains the AVPlayer state. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as UI status synchronization, playback process control, state machine management, and error diagnosis.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [AVPlayerState](capi-avplayer-base-h.md#avplayerstate) *state | Output parameter used to obtain the current playback status. The returned state values include **idle**, **initialized**, **prepared**, **playing**, **paused**, **completed**, **stopped**, and **error**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The AVPlayer state is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetState** fails.|

### OH_AVPlayer_IsPlaying()

```c
bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is playing. This function can be called when an AVPlayer is in any state. However, the validity of the returned result depends on the current state. It is applicable to scenarios such as switching the playback button status, updating the UI playback indicator, and detecting the playback state in the background.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Check result for whether the AVPlayer is playing. **true** if yes, **false** if the AVPlayer is not playing or the input parameter **player** is nullptr.|

### OH_AVPlayer_IsLooping()

```c
bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)
```

**Description**

Checks whether an AVPlayer is looping. This function can be called when an AVPlayer is in any state. This function applies to scenarios such as loop mode indicator display, playback mode management, and UI status synchronization.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Check result for whether the AVPlayer is looping. **true** if yes, **false** if the AVPlayer is not looping or the input parameter **player** is nullptr.|

### OH_AVPlayer_SetLooping()

```c
OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)
```

**Description**

Enables loop playback. By default, the playback is not looped. If this API is not called to set loop playback, the default value is used. This API can be called when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as loop playback of background music, learning materials, and short videos.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| bool loop | Whether to enable loop playback. The value **true** indicates that loop playback is enabled (suitable for scenarios where repeated playback is required, such as background music and ad rotation). The value **false** indicates that loop playback is disabled (suitable for scenarios where content is played only once, such as broadcast VOD). The default value is **false**. |

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) callback | Pointer to the callback object, which is used to receive player event callbacks, including callbacks such as **onInfo** and **onError**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The callback is set successfully.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, the input parameter **callback.onInfo** or **onError** is null, or the execution of **player SetPlayerCallback** fails.|

### OH_AVPlayer_SelectTrack()

```c
OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Selects an audio or subtitle track.<br> By default, the first audio track with data is played, and the subtitle track is not played.<br> After the setting takes effect, the original track becomes invalid. When selecting a subtitle track, ensure that the player is in the prepared, playing, paused, or completed state. When selecting an audio track, ensure that the player is in the prepared state.<br> **Differences:** [OH_AVPlayer_SelectTrackWithMode](#oh_avplayer_selecttrackwithmode) can also be used to select a track, but the switching mode can be specified. This method uses the default switching mode. To control the switching behavior (such as smooth switching), use **SelectTrackWithMode**. This method is applicable to scenarios such as switching between multiple languages, controlling subtitle display, and selecting multiple soundtracks.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t index | Index. Index of an audio or subtitle track. The value range is [0, **trackCount** – 1], where **trackCount** can be obtained by calling **OH_AVPlayer_GetTrackCount**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player SelectTrack** fails.|

### OH_AVPlayer_DeselectTrack()

```c
OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Deselects an audio or subtitle track. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This method can be used to disable subtitle display and cancel unnecessary soundtracks.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t index | Index. Index of an audio or subtitle track. The value range is [0, **trackCount** – 1], where **trackCount** can be obtained by calling **OH_AVPlayer_GetTrackCount**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player DeselectTrack** fails.|

### OH_AVPlayer_GetCurrentTrack()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)
```

**Description**

Obtains the currently valid track. When this API is called, the AVPlayer must be in the prepared, playing, paused, or completed state. This method applies to scenarios such as current track information display, playback state query, and multi-track management.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t trackType | Media type. The value **0** means audio and **1** means video.|
| int32_t *index | Index. Output parameter used to obtain the current track index.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The track is obtained.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **player GetCurrentTrack** fails.|

### OH_AVPlayer_SetMediaKeySystemInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)
```

**Description**

Sets a callback to return the media key system information for an AVPlayer. This method is applicable to the playback of DRM-encrypted media content, for example, listening for DRM information updates, obtaining keys for encrypted content, and processing copyright-protected content. This API must be set before **prepare** is called.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [Player_MediaKeySystemInfoCallback](capi-avplayer-h.md#player_mediakeysysteminfocallback) callback | Pointer to the callback for receiving the DRM key system information update event.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input **player** or **callback** is a null pointer, or the execution of **SetDrmSystemInfoCallback** fails.|

### OH_AVPlayer_GetMediaKeySystemInfo()

```c
OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)
```

**Description**

Obtains the media key system information to create a media key session. This API can be called only when the AVPlayer is in the prepared, playing, paused, completed, or stopped state. This API is applicable to scenarios such as initializing decryption sessions and obtaining decryption keys before playing DRM-encrypted content.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) *mediaKeySystemInfo | Output parameter used to receive the media key system information. The information includes DRM-related information such as the key system ID and session ID, which is used to create a media key session.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the memory is insufficient.|

### OH_AVPlayer_SetDecryptionConfig()

```c
OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)
```

**Description**

Sets the decryption information. This method is applicable to scenarios where media content is encrypted using DRM, such as playing encrypted videos, paid content, or media resources protected by copyright. This API must be set before **prepare** is called.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [MediaKeySession](capi-avplayer-mediakeysession.md) *mediaKeySession | Pointer to the media key session with the decryption feature.|
| bool secureVideoPath | Whether a secure decoder is required. The value **true** indicates that a secure decoder is required (a decoder with a hardware security channel, used to process copyright-protected video content). The value **false** indicates that a secure decoder is not required.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr, or the execution of **SetDecryptionConfig** fails.|

### OH_AVPlayer_SetOnInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that the AVPlayer receives a message. Since API version 12, this API is a substitute for **OH_AVPlayer_SetPlayerCallback** and flexibly supports multiple instances. It is applicable to scenarios such as listening for player status changes, receiving playback notifications, and controlling the playback process.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer messages is canceled.|
| void *userData | Pointer to the custom data. The data is returned in the callback and is used to identify different AVPlayer instances or pass context information in the callback. You can pass a null pointer, indicating that the user data does not need to be passed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_NO_MEMORY**: Memory allocation fails. If the memory usage exceeds the threshold, release the memory and try again.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or the function fails to be executed.|

### OH_AVPlayer_SetOnErrorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)
```

**Description**

Sets a callback for the event indicating that an error occurs in the AVPlayer. Since API version 12, this API is a substitute for **OH_AVPlayer_SetPlayerCallback** and flexibly supports multiple instances. This API is applicable to scenarios such as playback error handling, error reporting, user error notification, and abnormal playback recovery.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) callback | Pointer to the callback. If nullptr is passed in, the listening for AVPlayer errors is canceled.|
| void *userData | Pointer to the custom data. The data is returned in the callback and is used to identify different AVPlayer instances or pass context information in the callback. You can pass a null pointer, indicating that the user data does not need to be passed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | **AV_ERR_OK**: The operation is successful.<br>         **AV_ERR_NO_MEMORY**: Memory allocation fails. If the memory usage exceeds the threshold, release the memory and try again.<br>         **AV_ERR_INVALID_VAL**: The input parameter **player** is nullptr or the function fails to be executed.|

### OH_AVPlayer_GetMediaDescription()

```c
OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)
```

**Description**

Obtains the media source information for the AVPlayer. This function can be called when the playback resource is configured and the AVPlayer is in the initialized, prepared, playing, paused, completed, or stopped state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed. This method applies to scenarios such as media information display, playback details query, and media metadata obtaining.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 22

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Media source information obtained. If the operation fails, nullptr is returned.<br> Possible cause:<br>   1. The **player** pointer is invalid.<br>   2. The playback resource is invalid.|

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| uint32_t index | Index of the track. The value range is [0, **trackCount** – 1], where **trackCount** can be obtained by calling **OH_AVPlayer_GetTrackCount**. If an index out of the range is passed, nullptr is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Track information obtained. If the operation fails, nullptr is returned.<br> Possible cause:<br>   1. The **player** pointer is invalid.<br>   2. The playback resource is invalid.<br>   3. The track index is out of the range for the playback source file array.|

### OH_AVPlayer_AddFdSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Adds the subtitle resource of the file descriptor to the player. Currently, the external subtitle must be set after the **fdSrc** of the video resource is set in the AVPlayer. This method applies to scenarios such as playing local subtitle files, supporting subtitles in multiple languages, and displaying external subtitles.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t fd | File descriptor of the subtitle source.|
| int64_t offset | Offset of the media source in the file descriptor.|
| int64_t size | Size of the media source, in bytes. This parameter specifies the length of the media data read from the file descriptor.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.|

### OH_AVPlayer_AddUrlSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)
```

**Description**

Adds the subtitle resource of the URL to the player. The external subtitle must be set after the URL is set for the AVPlayer. This method applies to scenarios such as playing network subtitle files, loading online subtitles, and supporting subtitles in multiple languages.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| const char *url | URL of the subtitle source. The HTTP/HTTPS protocol is supported.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.|

### OH_AVPlayer_SetPlaybackRange()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)
```

**Description**

Sets the start and end positions of the playback. Only the content within the specified range is played. This method can be called only when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. This method applies to scenarios such as video clip preview, chapter playback, clip sharing, and partial content playback.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t mSecondsStart | Start position of playback. The value must be in the range of [0, **duration**). The value **-1** indicates that the start position is not set, and the playback starts from 0. If the value is out of range, the error code **AV_ERR_INVALID_VAL** (parameter error) is returned, or the value is automatically corrected to the boundary value. The unit is ms.|
| int32_t mSecondsEnd | End position of playback. The value must be in the range of (**mSecondsStart**, **duration**). If **mSecondsStart** is set to **-1**, the value must be in the range of (0, **duration**]. The value **-1** indicates that the end position is not set, and the playback ends at the end of the stream. The value of **duration** can be obtained through the **OH_AVPlayer_GetDuration** API. The unit is ms.|
| bool closestRange | Whether to seek to the frame closest to the specified position. If **true** is passed, the playback position is synchronized to the nearest frame, which is suitable for scenarios where the precise playback position is required. If **false** is passed, the playback position is not synchronized to the nearest frame, which is suitable for scenarios where the precise playback position is not required.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. Check whether the current player status meets the API calling requirements or whether an unsupported operation is performed during live streaming.|

### OH_AVPlayer_SetMediaMuted()

```c
OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)
```

**Description**

Mutes the media stream. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as muted playback, independent audio and video mute control, and playback preview.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype) mediaType | Media type. The options are **MEDIA_TYPE_AUD** (audio type, used to mute the audio stream) and **MEDIA_TYPE_VID** (video type, used to mute the camera stream). For details, see [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype).|
| bool muted | Whether to mute the player. The value **true** indicates that the player is muted (suitable for scenarios where the audio needs to be temporarily disabled, such as muted preview and background playback). The value **false** indicates that the player is unmuted (suitable for scenarios where the audio is played normally). The default value is **false**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVPlayer_GetPlaybackPosition()

```c
int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)
```

**Description**

Obtains the playback position, in milliseconds. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. It is applicable to scenarios such as playback progress display, playback time statistics, and resumable playback recording.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Playback position, in milliseconds.<br>         If **player** is a null pointer or invalid, **-1** is returned.|

### OH_AVPlayer_IsSeekContinuousSupported()

```c
bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)
```

**Description**

Checks whether the media source supports continuous seek. If this API is called when the AVPlayer is in the prepared, playing, paused, or completed state, the actual value is returned. Other, **false** is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) mode, **false** is returned. It is applicable to scenarios such as progress bar drag check, function compatibility check, and player capability query.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| bool | **true** indicates that continuous seek is supported.<br>          **false** indicates that continuous seek is not supported or the API is called in an invalid state (idle, initialized, or stopped).|

### OH_AVPlayer_SelectTrackWithMode()

```c
OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)
```

**Description**

Selects a track in the specified switching mode when playing a resource that contains multiple audio and video tracks.<br> When selecting a subtitle track, ensure that the player is in the prepared, playing, paused, or completed state. When selecting an audio track, ensure that the player is in the prepared state. This method applies to scenarios such as seamless switching between multiple languages, smooth switching between audio tracks, and advanced track management and control.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t index | Index of the selected track. The value range is [0, **trackCount** – 1], where **trackCount** can be obtained by calling **OH_AVPlayer_GetTrackCount**.|
| [AVPlayerTrackSwitchMode](capi-avplayer-base-h.md#avplayertrackswitchmode) mode | Switching mode. For details about the options and use scenarios, see the definitions in [AVPlayerTrackSwitchMode](capi-avplayer-base-h.md#avplayertrackswitchmode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVPlayer_SetAmplitudeUpdateCallback()

```c
OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)
```

**Description**

Subscribes to the maximum audio amplitude update event, which is reported periodically when audio resources are played. This API is applicable to scenarios where audio visualization or audio intensity detection is required, such as audio waveform display, audio intensity visualization, and audio energy detection.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVPlayerOnAmplitudeUpdateCallback](capi-avplayer-base-h.md#oh_avplayeronamplitudeupdatecallback) callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered.|
| void *userData | Pointer to user-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.|

### OH_AVPlayer_SetSeiReceivedCallback()

```c
OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)
```

**Description**

Subscribes to the SEI message reception event. This API applies only to HTTP-FLV live streams and is triggered when an SEI message exists in a video stream. This subscription must be initiated before **prepare** is called.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance. This parameter must be called before **prepare**.|
| const int32_t *payloadTypes | Array of payload types for SEI message subscription, which specifies the types of SEI messages to be subscribed to. The array size is specified by the **typeNum** parameter.|
| uint32_t typeNum | Size of the load type array.|
| [OH_AVPlayerOnSeiMessageReceivedCallback](capi-avplayer-base-h.md#oh_avplayeronseimessagereceivedcallback) callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered.|
| void *userData | Pointer to user-defined data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.|

### OH_AVSeiMessage_GetSeiCount()

```c
uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)
```

**Description**

Obtains the number of items in the SEI message array.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) *message | Pointer to the **OH_AVSeiMessageArray** instance.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Number of items in the SEI message array.|

### OH_AVSeiMessage_GetSei()

```c
OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)
```

**Description**

Obtains an SEI message form the SEI message array by index. You must manually release the returned OH_AVFormat pointer object when it is no longer needed.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) *message | Pointer to the **OH_AVSeiMessageArray** instance.|
| uint32_t index | Index of the message item. The value range is [0, **seiCount** – 1], where **seiCount** can be obtained by calling **OH_AVSeiMessage_GetSeiCount**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | SEI of the message item. If **message** is a null pointer or **index** is invalid, a null pointer is returned.|

### OH_AVPlayer_SetTargetVideoWindowSize()

```c
OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)
```

**Description**

Sets the video window size for super resolution. This method can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. The input parameter value must be in the range of 320 × 320 to 1920 × 1080, in pixels. This method is applicable to scenarios where super resolution is used for video display, such as low-resolution video quality enhancement and video enhancement.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t width | Window width, in pixels. The value range is [320, 1920]. If the value is out of range, the error code **AV_ERR_INVALID_VAL** (parameter error) is returned.|
| int32_t height | Window height, in pixels. The value range is [320, 1080]. If the value is out of range, the error code **AV_ERR_INVALID_VAL** (parameter error) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer or the parameter is incorrect.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.<br>         **AV_ERR_SUPER_RESOLUTION_UNSUPPORTED**: The current device does not support the super resolution function. Check the device specifications or use another video processing solution.<br>         **AV_ERR_SUPER_RESOLUTION_NOT_ENABLED**: Super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md).|

### OH_AVPlayer_SetVideoSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)
```

**Description**

Dynamically enables or disables super resolution. This method can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. You must enable the super resolution feature in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling **prepare**. This method is applicable to scenarios where video quality enhancement needs to be dynamically controlled, for example, dynamically adjusting the quality based on the device performance or switching the quality based on the network status.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| bool enabled | **true** means to enable super resolution; **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer or the parameter is incorrect.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.<br>         **AV_ERR_SUPER_RESOLUTION_UNSUPPORTED**: Super resolution is not supported.<br>         **AV_ERR_SUPER_RESOLUTION_NOT_ENABLED**: Super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md).|

### OH_AVPlaybackStrategy_Create()

```c
OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)
```

**Description**

Creates a playback strategy instance.

**Since**: 23

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVPlaybackStrategy *](capi-avplayer-oh-avplaybackstrategy.md) | Playback strategy instance. If the operation fails, a null pointer is returned.|

### OH_AVPlaybackStrategy_Destroy()

```c
OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)
```

**Description**

Releases a playback strategy instance.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the **OH_AVPlaybackStrategy** instance, which is used to specify the playback strategy object to be released.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredWidth()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)
```

**Description**

Selects a stream with width close to the specified value.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the playback strategy configuration object. You need to create the object by calling **OH_AVPlaybackStrategy_Create**, configure parameters such as the width, height, and buffer duration by calling related set APIs, and then set the object to the player to apply the strategy.|
| int32_t width | Preferred width for playback when the AVPlayer is started, in pixels. The recommended value range is [320, 1920]. The player selects the camera stream close to this width for playback. If this parameter is not set or is set to **0**, the default selection policy is used.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredHeight()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)
```

**Description**

Selects a stream with height close to the specified value.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | **OH_AVPlaybackStrategy** used by the AVPlayer.|
| int32_t height | Preferred height for playback when the AVPlayer is started, in pixels. The recommended value range is [320, 1080].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredBufferDuration()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)
```

**Description**

Selects the preferred buffer duration that is close to the specified value.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | **OH_AVPlaybackStrategy** used by the AVPlayer.|
| int32_t ms | Preferred buffer duration for playback when the AVPlayer is started, in milliseconds. The recommended value range is [100, 10000].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredHdr()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Enables or disables the preferred HDR mode.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| bool enabled | The value **true** means to enable the preferred HDR mode, and the value **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred subtitle language.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| const char *lang | Subtitle language code, which complies with the ISO 639-1 or ISO639-2 standard and contains 2 to 3 characters (for example, **zh**, **en**, and **zho**).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredAudioLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred audio language.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| const char *lang | Audio language code, which complies with the ISO 639-1 or ISO639-2 standard and contains 2 to 3 characters (for example, **zh**, **en**, and **zho**).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetMutedMediaType()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)
```

**Description**

Sets the media type to be muted during playback.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype) mediaType | Type of the media to be muted. The options are **MEDIA_TYPE_AUD** (audio type, used to mute the audio stream) and **MEDIA_TYPE_VID** (video type, used to mute the camera stream). For details, see [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to display the first frame during the **prepare** state.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| bool enabled | **true**: The first frame is displayed. **false**: The first frame is not displayed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the threshold for automatic quick playback. When the buffered data is insufficient and stuttering may occur during playback, the player automatically increases the playback rate to quickly play the buffered content. This threshold is used to control the condition for triggering this behavior.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| double seconds | Threshold for automatic quick playback, in seconds. The recommended value range is [0.5, 10.0].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to enable super resolution. Before calling **OH_AVPlayer_Prepare**, you need to set the playback strategy that contains the super resolution function for the player by calling **OH_AVPlayer_SetPlaybackStrategy**.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| bool enabled | The value **true** indicates that super resolution is enabled, and the value **false** indicates that super resolution is disabled.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the preferred buffer duration during playback (double type, in seconds).

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| double seconds | Buffer duration during playback, in seconds. The recommended value range is [0.1, 30.0].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlaybackStrategy_SetKeepDecodingOnMute()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to continue decoding when the audio is muted.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to **OH_AVPlaybackStrategy**.|
| bool enabled | The value **true** means to continue decoding when the audio is muted, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input strategy is a null pointer.|

### OH_AVPlayer_SetPlaybackStrategy()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)
```

**Description**

Sets the playback strategy for the AVPlayer. This API can be called only when the AVPlayer is in the initialized state. This API is applicable to scenarios where playback optimization configurations such as the buffer policy, image quality policy, and super resolution policy need to be set before playback.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance, which must be called in the initialized state.|
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the **OH_AVPlaybackStrategy** instance, which is used to set the playback policy for the player.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed.|

### OH_AVPlayer_GetPlaybackInfo()

```c
OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)
```

**Description**

Obtains the statistics of the current AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, or paused state. You must manually release the returned OH_AVFormat pointer object when it is no longer needed. It is applicable to scenarios such as playback quality monitoring, performance analysis, and playback parameter optimization.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance, which must be called when the AVPlayer is in the prepared, playing, or paused state.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the **OH_AVFormat** instance.<br>         If the **player** is a null pointer or invalid, a null pointer is returned.|

### OH_AVPlayer_SetMediaSource()

```c
OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)
```

**Description**

Sets the **OH_AVMediaSource** to the AVPlayer. This function applies to scenarios where complex media sources, media sources with DRM configurations, and advanced playback configurations need to be set.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Pointer to the **OH_AVMediaSource** instance, including the media URL and DRM configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input **player** or **source** is a null pointer, or the **player** fails to set the URL source.|

### OH_AVPlayer_GetTrackCount()

```c
uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)
```

**Description**

Obtains the number of tracks of the media source of the AVPlayer. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. This method applies to scenarios such as track list display, multi-track management, and track information traversal.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Returns the number of tracks of the media source of the AVPlayer. If **player** is a null pointer or invalid, **0** is returned.|

### OH_AVPlayer_GetTrackFormat()

```c
OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)
```

**Description**

Obtains the track information of the AVPlayer by index. This API can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.<br> You must manually release the returned OH_AVFormat pointer object when it is no longer needed. This method applies to scenarios such as track details display, track information query, and multi-track management.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| uint32_t trackIndex | Index of the track array. The value range is [0, **trackCount** – 1], where **trackCount** can be obtained by calling **OH_AVPlayer_GetTrackCount**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the **OH_AVFormat** instance.<br>         If **player** is a null pointer or invalid, or **trackIndex** is invalid, a null pointer is returned.|

### OH_AVPlayer_GetPlaybackStatisticMetrics()

```c
OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)
```

**Description**

Obtains the statistic metrics of the current AVPlayer. This function can be called when the playback resource has been set and the AVPlayer is in the prepared, playing, paused, completed, or stopped state.<br> Note that you need to manually release the lifecycle of the [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) pointer object.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | If the operation is successful, the statistic metrics of the current AVPlayer are returned. (For details about the key values, see [Variables](../apis-media-kit/capi-avplayer-base-h.md#variables) in **avplayer_base.h**.) Otherwise, **nullptr** is returned.<br> Possible failure cause: The input **player** pointer is invalid.|

### OH_AVPlayer_SetPCMOutputCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)
```

**Description**

Sets the callback for audio PCM data output. This API can be called when the AVPlayer is in the idle or initialized state. This API is applicable to scenarios where raw audio data needs to be obtained, such as audio data analysis, audio recording, audio processing, and audio visualization.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance, which must be called when the AVPlayer is in the idle or initialized state.|
| [OH_AVPlayerPCMOutputCallback](capi-avplayer-base-h.md#oh_avplayerpcmoutputcallback) callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered.|
| void *userData | Pointer to user data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer, or **OH_AVPlayer_SetPCMOutputCallback()** fails.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The function is called in an unsupported state.|

### OH_AVPlayer_SetVideoSideOutput()

```c
OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Sets the callback for decoded video frame output. This API can be called when the AVPlayer is in the idle or initialized state. This API is applicable to scenarios where decrypted video frames need to be obtained, such as video frame analysis, video filter processing, video snapshot, and video special effect processing.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance, which must be called when the AVPlayer is in the idle or initialized state.|
| [OHNativeWindow](../apis-avcodec-kit/capi-codecbase-nativewindow.md) *window | Pointer to the **OHNativeWindow** instance. For details, see **OHNativeWindow**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVPlayerVideoOutput*](capi-avplayer-oh-avplayervideooutput.md) | Pointer to the **OH_AVPlayerVideoOutput** instance. If **nullptr** is returned, the operation fails.<br> Possible cause:<br> 1. The **player** pointer is invalid.<br> 2. The **window** pointer is invalid.|

### OH_AVPlayerVideoOutput_GetNewestVideoSample()

```c
OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)
```

**Description**

Obtains a decoded video frame. This API can be called when the AVPlayer is in the paused or playing state. This API is applicable to scenarios where the current video frame needs to be obtained, such as video frame capture, video frame analysis, video snapshot, and video frame processing.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) *videoOutput | Pointer to the **OH_AVPlayerVideoOutput** instance returned by **OH_AVPlayer_SetVideoSideOutput**.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_VideoOutputResult](capi-avplayer-base-h.md#oh_videooutputresult) | **OH_VIDEO_OUTPUT_OK** (**0**): A decoded video frame is obtained.<br>         **OH_VIDEO_OUTPUT_NO_IMAGE** (**1**): No frame is available for rendering.|

### OH_AVPlayer_SetPCMProcessorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)
```

**Description**

Sets the callback for audio PCM data postprocessing. This API can be called when the AVPlayer is in the idle or initialized state. This method is applicable to scenarios such as audio special effect processing, audio enhancement, and secondary audio data processing.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| [OH_AVPlayerPCMProcessorCallback](capi-avplayer-base-h.md#oh_avplayerpcmprocessorcallback) callback | Pointer to the callback function. **nullptr** indicates that the callback is deregistered.|
| void *userData | Pointer to user data.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer, or **OH_AVPlayer_SetPCMProcessorCallback()** fails.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The function is called in an unsupported state.|

### OH_AVPlayer_SetPCMProcessorMaxLen()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)
```

**Description**

Sets the maximum amount of data that can be returned at a time by the audio postprocessing callback. Some data can be cached and output together with the PCM data returned next time.<br> This API can be called when the AVPlayer is in the idle or initialized state.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the **OH_AVPlayer** instance.|
| int32_t maxProcessedPCMLen | Maximum amount of data that can be returned at a time. The unit is byte and the value range is (0, 5 MB].<br> **OH_AVPlayerPCMProcessorCallback **ensures that the returned AVBuffer capacity is not less than this value.|

**Returns**

| Type| Description|
| -- | -- |
| OH_AVErrCode | Execution result of the function.<br>         **AV_ERR_OK**: The execution is successful.<br>         **AV_ERR_INVALID_VAL**: The input player is a null pointer, or the **maxProcessedPCMLen** parameter is invalid.<br>         **AV_ERR_OPERATE_NOT_PERMIT**: The function is called in an unsupported state.|
