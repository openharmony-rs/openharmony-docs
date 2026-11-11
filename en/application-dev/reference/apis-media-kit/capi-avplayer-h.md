# avplayer.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1a0e73408ae45dae1d89551f7b1632524bee30d7 translatedAt=2026-11-10T08:41:23.109Z pushedAt=2026-11-10T10:45:18.943Z nl=1 -->

## Overview

AVPlayer is an audio/video playback component that provides complete playback control and advanced features (multiple tracks, subtitles, DRM, and so on). It is applicable to scenarios such as video players, audio players, and live streaming applications, providing developers with high-performance, low-latency media playback capabilities and reducing development complexity.

**File to include:** <multimedia/player_framework/avplayer.h>

**Library:** libavplayer.so

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

**Sample:** [AVPlayerNDKVideo](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVPlayer/AVPlayerNDK)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [MediaKeySession](capi-avplayer-mediakeysession.md) | MediaKeySession | MediaKeySession type. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) | DRM_MediaKeySystemInfo | DRM_MediaKeySystemInfo type. |
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) | OH_AVPlayerVideoOutput | OH_AVPlayerVideoOutput fields. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)](#player_mediakeysysteminfocallback) | Player_MediaKeySystemInfoCallback | Called when the player's DRM information is updated. |
| [OH_AVPlayer *OH_AVPlayer_Create(void)](#oh_avplayer_create) | - | Creates a player.<br> It is recommended that a single application create no more than 16 audio/video player instances in total. <!--Del--><br> The number of audio/video player instances that can be created depends on the support of the device chip. If the chip supports fewer instances than the number above, the chip specification prevails. For example, RK3568 recommends that a single application create no more than 6 audio/video player instances. <!--DelEnd--> |
| [OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_seturlsource) | - | Sets the playback source of the player. The source can be an HTTP URL or an HTTPS URL. |
| [OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_setfdsource) | - | Sets the media file descriptor source of the player. |
| [OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer \*player, OH_AVDataSourceExt\* datasrc, void* userData)](#oh_avplayer_setdatasource) | - | Sets the media source of the player. The data of this media source is provided by the application. |
| [OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)](#oh_avplayer_prepare) | - | Prepares the playback environment and asynchronously caches media data.<br> This function must be called after SetSource. |
| [OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)](#oh_avplayer_play) | - | Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare()](#oh_avplayer_prepare).<br> If the player state is \<Prepared>, call this function to start playback. |
| [OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)](#oh_avplayer_pause) | - | Pauses playback. Call this function when the player is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)](#oh_avplayer_stop) | - | Stops playback. Call this function when the player is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)](#oh_avplayer_reset) | - | Restores the player to the initial state.<br> After this function is called, call SetSource to add a playback source. After calling [OH_AVPlayer_Prepare()](#oh_avplayer_prepare), call [OH_AVPlayer_Play()](#oh_avplayer_play) to restart playback. |
| [OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)](#oh_avplayer_release) | - | Asynchronously releases player resources.<br> Asynchronous release improves performance but does not ensure that the SurfaceBuffer of the playback frame has been released. The caller must ensure the lifecycle safety of the playback frame window. |
| [OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)](#oh_avplayer_releasesync) | - | Synchronously releases player resources.<br> The synchronous process ensures that the SurfaceBuffer of the playback frame is released, but it takes a long time. It is recommended that the caller design an asynchronous mechanism. |
| [OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)](#oh_avplayer_setvolume) | - | Sets the volume of the player.<br> It can be used during playback or pause. 0 indicates silence, and 1 is the original value. The default volume is 1. |
| [OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)](#oh_avplayer_setloudnessgain) | - | Sets the loudness of the player. This interface can be called when the player is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. The usage parameter of the player stream must be one of the following enum values: [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC, [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, and [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> This operation is not supported if playback is performed through a high-resolution pipeline. |
| [OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)](#oh_avplayer_seek) | - | Changes the playback position.<br> This function can be used during playback or pause. |
| [OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)](#oh_avplayer_getcurrenttime) | - | Obtains the current playback time (returned through the parameter), accurate to milliseconds. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)](#oh_avplayer_getvideowidth) | - | Obtains the video width. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)](#oh_avplayer_getvideoheight) | - | Obtains the video height. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)](#oh_avplayer_setplaybackspeed) | - | Sets the playback rate of the player based on the specified [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). The default playback rate is 1.0x (normal speed). |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)](#oh_avplayer_setplaybackrate) | - | Sets the playback rate of the player within the valid range.<br> The supported states include prepared, playing, paused, and completed. The default playback rate is 1.0x (normal speed). |
| [OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)](#oh_avplayer_getplaybackspeed) | - | Obtains the current playback rate of the player. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)](#oh_avplayer_getplaybackrate) | - | Obtains the current playback rate of the player. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)](#oh_avplayer_setaudiorendererinfo) | - | Sets the audio stream type of the player. |
| [OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)](#oh_avplayer_setvolumemode) | - | Sets the audio stream volume mode of the player. |
| [OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)](#oh_avplayer_setaudiointerruptmode) | - | Sets the interruption mode of the player's audio stream. |
| [OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)](#oh_avplayer_setaudioeffectmode) | - | Sets the sound effect mode of the player's audio stream. |
| [OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)](#oh_avplayer_selectbitrate) | - | Sets the bit rate used by the HLS player. It is valid only for HLS protocol network streams. This interface can be called only when AVPlayer is in the prepared, playing, or paused state.<br> By default, the player selects an appropriate bit rate and speed based on the network connection.<br> The valid bit rate list is reported through INFO_TYPE_BITRATE_COLLECT. If the bit rate specified by the user is not in this list, the player selects the closest bit rate from the available bit rate list. |
| [OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosurface) | - | Sets the playback frame window.<br> This function must be called after SetSource and before Prepare. |
| [OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)](#oh_avplayer_getduration) | - | Obtains the total duration of the media file, accurate to milliseconds. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)](#oh_avplayer_getstate) | - | Obtains the current playback state. |
| [bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)](#oh_avplayer_isplaying) | - | Checks whether the player is playing. This interface can be called when AVPlayer is in any state, but the validity of the returned result depends on the current state. |
| [bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)](#oh_avplayer_islooping) | - | Checks whether loop playback is enabled. This interface can be called when AVPlayer is in any state. |
| [OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)](#oh_avplayer_setlooping) | - | Sets loop playback. Loop playback is disabled by default. |
| [OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)](#oh_avplayer_setplayercallback) | - | Sets the player callback function.<br> Because the information listening callback function [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and the error listening callback function [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set through this method can pass limited information, it is also inconvenient for applications to distinguish multiple player instances.<br> Since API version 12, use [OH_AVPlayer_SetOnInfoCallback()](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback()](#oh_avplayer_setonerrorcallback) to set the information listening callback function [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and the error listening callback function [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) respectively.<br>Deprecated since API version 12. |
| [OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_selecttrack) | - | Selects an audio or subtitle track.<br> By default, the first audio track with data is played, and no subtitle track is played.<br> After the setting takes effect, the original audio track becomes invalid. When selecting a subtitle track, the player must be in the prepared, playing, paused, or completed state; when selecting an audio track, the player must be in the prepared state. |
| [OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)](#oh_avplayer_deselecttrack) | - | Deselects the current audio or subtitle track. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)](#oh_avplayer_getcurrenttrack) | - | Obtains the index of the currently valid track. When calling this interface, the player must be in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)](#oh_avplayer_setmediakeysysteminfocallback) | - | Sets the method for the player's media key system information callback. It is applicable to scenarios of playing DRM-encrypted media content, such as listening for DRM information updates, obtaining encrypted content keys, and processing copyright-protected content. |
| [OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)](#oh_avplayer_getmediakeysysteminfo) | - | Obtains the media key system information to create a media key session. |
| [OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)](#oh_avplayer_setdecryptionconfig) | - | Sets the decryption information. It is applicable to scenarios of DRM-encrypted media content, such as playing encrypted videos, playing paid content, and playing copyright-protected media resources. |
| [OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)](#oh_avplayer_setoninfocallback) | - | Sets the player message callback listening function. |
| [OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)](#oh_avplayer_setonerrorcallback) | - | Sets the player error callback listening function. |
| [OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)](#oh_avplayer_getmediadescription) | - | Obtains the media source information of the player. This interface can be called after the playback resource is set and the player is in the initialized/prepared/playing/paused/completed/stopped state.<br> Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user. |
| [OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)](#oh_avplayer_gettrackdescription) | - | Obtains the media source track information of the player by index. This interface can be called after the playback resource is set and the player is in the initialized/prepared/playing/paused/completed/stopped state.<br> Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user. |
| [OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)](#oh_avplayer_addfdsubtitlesource) | - | Adds a file descriptor subtitle resource to the player. Currently, external subtitles must be set after AVPlayer has set the fdSrc of the video resource. |
| [OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)](#oh_avplayer_addurlsubtitlesource) | - | Adds a URL subtitle resource to the player. External subtitles must be set after AVPlayer has set the URL. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)](#oh_avplayer_setplaybackrange) | - | Sets the playback start position and end position. Only the content within the specified range is played. It can be called in the initialized, prepared, paused, stopped, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)](#oh_avplayer_setmediamuted) | - | Mutes a media stream. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)](#oh_avplayer_getplaybackposition) | - | Obtains the playback position, accurate to milliseconds. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)](#oh_avplayer_isseekcontinuoussupported) | - | Checks whether the media source supports continuous seeking. When called in the prepared, playing, paused, or completed state, the actual value is returned; when called in other states, false is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) seek mode, false is returned. |
| [OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)](#oh_avplayer_selecttrackwithmode) | - | Selects a track using the specified switch mode when playing a resource that contains multiple audio/video tracks. This interface can be called only when AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)](#oh_avplayer_setamplitudeupdatecallback) | - | Subscribes to the update event of the maximum audio level value, which is reported periodically when playing audio resources. It is applicable to scenarios that require audio visualization or audio intensity detection, such as audio waveform display, audio intensity visualization, and audio energy detection. |
| [OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)](#oh_avplayer_setseireceivedcallback) | - | Subscribes to the event of receiving Supplemental Enhancement Information (SEI) messages. It is applicable only to HTTP-FLV live streams and is triggered when SEI messages exist in the video stream. The subscription must be initiated before calling prepare. |
| [uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)](#oh_avseimessage_getseicount) | - | Obtains the number of message items in the SEI message array. |
| [OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)](#oh_avseimessage_getsei) | - | Obtains an SEI (Supplemental Enhancement Information) item in the SEI message array by index. Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user. |
| [OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)](#oh_avplayer_settargetvideowindowsize) | - | Sets the video window size for super resolution. This interface can be called when AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. The input parameter values must be within the range of 320x320 to 1920x1080. The unit is pixel (px). It is applicable to scenarios of super-resolution video display, such as quality enhancement of low-resolution videos and enhanced video display. |
| [OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)](#oh_avplayer_setvideosuperresolutionenable) | - | Dynamically enables or disables super resolution. This interface can be called when AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. Super resolution must be enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling prepare. It is applicable to scenarios that require dynamic control of video quality enhancement, such as dynamic adjustment based on device performance and switching quality based on network status. |
| [OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)](#oh_avplaybackstrategy_create) | - | Creates a playback strategy instance. |
| [OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)](#oh_avplaybackstrategy_destroy) | - | Releases a playback strategy instance. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)](#oh_avplaybackstrategy_setpreferredwidth) | - | Selects a stream close to the specified width. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)](#oh_avplaybackstrategy_setpreferredheight) | - | Selects a stream close to the specified height. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)](#oh_avplaybackstrategy_setpreferredbufferduration) | - | Selects a preferred buffer duration close to the specified value. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setpreferredhdr) | - | Enables or disables the preferred HDR mode. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredsubtitlelanguage) | - | Sets the preferred subtitle language. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)](#oh_avplaybackstrategy_setpreferredaudiolanguage) | - | Sets the preferred audio language. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)](#oh_avplaybackstrategy_setmutedmediatype) | - | Sets the media type to be muted during playback. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setshowfirstframeonprepare) | - | Sets whether to display the first frame during prepare. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setthresholdforautoquickplay) | - | Sets the threshold for automatic quick playback. When insufficient buffered data may cause playback stuttering, the player automatically increases the playback rate to quickly play the cached content. This threshold is the condition that controls the triggering of this behavior. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setsuperresolutionenable) | - | Enables or disables super resolution. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)](#oh_avplaybackstrategy_setpreferredbufferdurationforplaying) | - | Sets the preferred buffer duration (in seconds, double type) for playback. |
| [OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)](#oh_avplaybackstrategy_setkeepdecodingonmute) | - | Sets whether to keep decoding when muted. |
| [OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)](#oh_avplayer_setplaybackstrategy) | - | Sets the playback strategy for the AVPlayer. This interface can be called only when the AVPlayer is in the initialized state. |
| [OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)](#oh_avplayer_getplaybackinfo) | - | Obtains the statistics of the current player. This interface can be called only when the AVPlayer is in the prepared, playing, or paused state. Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user. |
| [OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)](#oh_avplayer_setmediasource) | - | Sets the OH_AVMediaSource for the player. |
| [uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)](#oh_avplayer_gettrackcount) | - | Obtains the number of tracks in the player's media source. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state. |
| [OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)](#oh_avplayer_gettrackformat) | - | Obtains the track information of the player by index. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.<br> Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user. |
| [OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)](#oh_avplayer_getplaybackstatisticmetrics) | - | Obtains the statistical metrics of the current player. After the playback resource is set and when the player is in the prepared, playing, paused, completed, or stopped state, this interface can be called.<br> Note that the lifecycle of the returned [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) pointer object must be released manually by the user. |
| [OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)](#oh_avplayer_setpcmoutputcallback) | - | Sets the audio PCM data output callback. This interface can be called when the player is in the idle or initialized state. It is applicable to scenarios that require obtaining raw audio data, such as audio data analysis, audio recording, audio processing, and audio visualization. |
| [OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)](#oh_avplayer_setvideosideoutput) | - | Sets the video decoded frame output callback. This interface can be called when the player is in the idle or initialized state. It is applicable to scenarios that require obtaining video decoded frames, such as video frame analysis, video filter processing, video screenshot, and video effect processing. |
| [OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)](#oh_avplayervideooutput_getnewestvideosample) | - | Obtains a video decoded frame. This interface can be called when the player is in the paused or playing state. It is applicable to scenarios that require obtaining the current video frame, such as video frame capture, video frame analysis, video screenshot, and video frame processing. |
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)](#oh_avplayer_setpcmprocessorcallback) | - | Sets the audio PCM data post-processing callback. This interface can be called when the player is in the idle or initialized state. |
| [OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)](#oh_avplayer_setpcmprocessormaxlen) | - | Sets the maximum amount of data that the audio post-processing callback function can return at a time. It allows caching part of the data and outputting it together with the PCM data returned next time.<br> This interface can be called when the player is in the idle or initialized state. |

## Function Description

### Player_MediaKeySystemInfoCallback()

```c
typedef void (*Player_MediaKeySystemInfoCallback)(OH_AVPlayer *player, DRM_MediaKeySystemInfo* mediaKeySystemInfo)
```

**Description**

Called when the player's DRM information is updated.

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md)* mediaKeySystemInfo | DRM media key system information, including the key system ID, session ID, and other DRM-related data. It is used to receive and pass DRM information when playing encrypted content. |

### OH_AVPlayer_Create()

```c
OH_AVPlayer *OH_AVPlayer_Create(void)
```

**Description**

Creates a player.<br> It is recommended that a single application create no more than 16 audio/video player instances in total.<br> <!--Del-->The number of audio/video player instances that can be created depends on the device chip support. If the chip supports fewer instances than the number above, the chip specification prevails. For example, RK3568 recommends that a single application create no more than 6 audio/video player instances.<!--DelEnd-->

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Return**

| Type | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) * | Pointer to the OH_AVPlayer instance if the player is created successfully; otherwise, a null pointer.<br> Possible failure causes:<br> 1. PlayerFactory::CreatePlayer fails to execute.<br> 2. new PlayerObject fails to execute. |

### OH_AVPlayer_SetURLSource()

```c
OH_AVErrCode OH_AVPlayer_SetURLSource(OH_AVPlayer *player, const char *url)
```

**Description**

Sets the playback source of the player. The source can be an HTTP URL or an HTTPS URL.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| const char *url | URL address of the playback source, which supports network URLs over the HTTP/HTTPS protocol. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the source is set successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, url is null, or SetUrlSource of the player fails to execute. |

### OH_AVPlayer_SetFDSource()

```c
OH_AVErrCode OH_AVPlayer_SetFDSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Sets the media file descriptor source of the player.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t fd | File descriptor of the media source. |
| int64_t offset | Offset of the media source in the file descriptor. |
| int64_t size | Size of the media source. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: fd set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or SetFdSource fails to be executed on the player. |

### OH_AVPlayer_SetDataSource()

```c
OH_AVErrCode OH_AVPlayer_SetDataSource(OH_AVPlayer *player, OH_AVDataSourceExt* datasrc, void* userData)
```

**Description**

Sets the media source of the player. The data of this media source is provided by the application.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AVDataSourceExt](../apis-avcodec-kit/capi-codecbase-oh-avdatasourceext.md)* datasrc | Pointer to the custom media data. |
| void* userData | Handle passed in by the user, used to be passed in the callback. If userData is null, multi-instance playback of AVPlayer is not supported. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the setting is successful.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or the input datasrc is a null pointer. |

### OH_AVPlayer_Prepare()

```c
OH_AVErrCode OH_AVPlayer_Prepare(OH_AVPlayer *player)
```

**Description**

Prepares the playback environment and asynchronously caches media data.<br> This function must be called after SetSource.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer, or if Prepare fails to execute on player. |

### OH_AVPlayer_Play()

```c
OH_AVErrCode OH_AVPlayer_Play(OH_AVPlayer *player)
```

**Description**

Starts playback.<br> This function must be called after [OH_AVPlayer_Prepare](#oh_avplayer_prepare).<br> If the player is in the \<Prepared> state, calling this function starts playback.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player Play fails. |

### OH_AVPlayer_Pause()

```c
OH_AVErrCode OH_AVPlayer_Pause(OH_AVPlayer *player)
```

**Description**

Pauses playback. Call this function when the player is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if the player Pause operation fails. |

### OH_AVPlayer_Stop()

```c
OH_AVErrCode OH_AVPlayer_Stop(OH_AVPlayer *player)
```

**Description**

Stops playback. Called when the player is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player Stop fails to execute. |

### OH_AVPlayer_Reset()

```c
OH_AVErrCode OH_AVPlayer_Reset(OH_AVPlayer *player)
```

**Description**

Restores the player to the initial state.<br> After this function is called, call SetSource to add a playback source. After calling [OH_AVPlayer_Prepare](#oh_avplayer_prepare), call [OH_AVPlayer_Play](#oh_avplayer_play) to start playback again.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or the player Reset fails. |

### OH_AVPlayer_Release()

```c
OH_AVErrCode OH_AVPlayer_Release(OH_AVPlayer *player)
```

**Description**

Asynchronously releases player resources.<br> Asynchronous release improves performance but does not ensure that the SurfaceBuffer of the playback frame has been released. The caller must ensure the lifecycle safety of the playback frame window.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br> Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player Release fails. |

### OH_AVPlayer_ReleaseSync()

```c
OH_AVErrCode OH_AVPlayer_ReleaseSync(OH_AVPlayer *player)
```

**Description**

Synchronously releases player resources.<br> The synchronous process ensures that the SurfaceBuffer of the playback frame is released, but this process is time-consuming. It is recommended that the caller design an asynchronous mechanism.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player ReleaseSync fails. |

### OH_AVPlayer_SetVolume()

```c
OH_AVErrCode OH_AVPlayer_SetVolume(OH_AVPlayer *player, float leftVolume, float rightVolume)
```

**Description**

Sets the volume of the player.<br> This API can be used during playback or pause. 0 indicates silence, and 1 indicates the original value. The default volume is 1.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| float leftVolume | Target volume of the left channel to set, ranging from 0.0 to 1.0. 0 indicates silence, and 1 indicates the original volume. |
| float rightVolume | Target volume of the right channel to set, ranging from 0.0 to 1.0. 0 indicates silence, and 1 indicates the original volume. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK: the volume is set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or player SetVolume fails to be executed. |

### OH_AVPlayer_SetLoudnessGain()

```c
OH_AVErrCode OH_AVPlayer_SetLoudnessGain(OH_AVPlayer *player, float loudnessGain)
```

**Description**

Sets the loudness of the player. This interface can be called when the player is in the prepared, playing, paused, completed, or stopped state.<br> The default loudness gain is 0.0 dB. The usage parameter of the player stream must be one of the following enum values: [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC, [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, and [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br> The latency mode of the audio renderer must be [OH_AudioStream_LatencyMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_latencymode).AUDIOSTREAM_LATENCY_MODE_NORMAL.<br> This operation is not supported if playback is performed through a high-resolution pipeline.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 21

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance, which must be used in the prepared/playing/paused/completed/stopped state. |
| float loudnessGain | Loudness value to set for the player, in dB. The loudness range is [-90.0, 24.0]. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>Returns AV_ERR_OK if the loudness is set successfully.<br>Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or the input loudnessGain is an invalid parameter.<br>Returns AV_ERR_INVALID_STATE if the function is called in an abnormal state, or the usage parameter of audioRendererInfo is not one of<br>[OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MUSIC,<br>[OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_MOVIE, and<br>[OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage).AUDIOSTREAM_USAGE_AUDIOBOOK.<br>Returns AV_ERR_SERVICE_DIED if a system error occurs. |

### OH_AVPlayer_Seek()

```c
OH_AVErrCode OH_AVPlayer_Seek(OH_AVPlayer *player, int32_t mSeconds, AVPlayerSeekMode mode)
```

**Description**

Changes the playback position.<br> This function can be used during playback or pause.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |
| int32_t mSeconds | Target playback position, accurate to milliseconds. |
| [AVPlayerSeekMode](capi-avplayer-base-h.md#avplayerseekmode) mode | Seek mode of the player. For the available values and applicable scenarios, see [AVPlayerSeekMode](capi-avplayer-base-h.md#avplayerseekmode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer or the seek operation fails. |

### OH_AVPlayer_GetCurrentTime()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTime(OH_AVPlayer *player, int32_t *currentTime)
```

**Description**

Gets the current playback time (returned through a parameter), accurate to milliseconds. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t *currentTime | Used to obtain the current playback position (output parameter), accurate to milliseconds. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK: the current playback position is obtained successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or GetCurrentTime fails to be executed on the player. |

### OH_AVPlayer_GetVideoWidth()

```c
OH_AVErrCode OH_AVPlayer_GetVideoWidth(OH_AVPlayer *player, int32_t *videoWidth)
```

**Description**

Gets the video width. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t *videoWidth | Output parameter used to obtain the video width, in pixels (px). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the video width is obtained successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_GetVideoHeight()

```c
OH_AVErrCode OH_AVPlayer_GetVideoHeight(OH_AVPlayer *player, int32_t *videoHeight)
```

**Description**

Obtains the video height. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |
| int32_t *videoHeight | Output parameter for obtaining the video height, in pixels (px). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK: the video height is obtained successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_SetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed speed)
```

**Description**

Sets the playback rate of the player based on the specified [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). The default playback rate is 1.0x (normal speed).

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) speed | Playback speed mode. For the available values and applicable scenarios, see the definition of [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the playback rate is set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_SetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRate(OH_AVPlayer *player, float rate)
```

**Description**

Sets the playback rate of the player within the valid range.<br> Supported states include prepared, playing, paused, and completed. The default playback rate is 1.0x (normal speed).

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 20

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| float rate | Playback rate. The value range is [0.125, 8.0] for API version 26.0.0 and later, and [0.125, 4.0] for API versions earlier than 26.0.0. A value less than 1.0 is suitable for slow playback (for example, learning and analysis), 1.0 is the normal speed, and a value greater than 1.0 is suitable for fast browsing. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the playback rate is set successfully.<br>         Returns AV_ERR_OPERATE_NOT_PERMIT if this method is called in an unsupported state or during live streaming.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or the set rate is out of range. |

### OH_AVPlayer_GetPlaybackSpeed()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackSpeed(OH_AVPlayer *player, AVPlaybackSpeed *speed)
```

**Description**

Gets the current playback speed of the player. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed) *speed | Speed mode. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the playback speed is obtained successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player GetPlaybackSpeed fails to execute. |

### OH_AVPlayer_GetPlaybackRate()

```c
OH_AVErrCode OH_AVPlayer_GetPlaybackRate(OH_AVPlayer *player, float *rate)
```

**Description**

Gets the current playback rate of the player. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| float *rate | Pointer to the variable that receives the playback rate, which returns the current playback rate multiple of the player. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the current playback rate of the player is obtained successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or GetPlaybackRate fails to execute. |

### OH_AVPlayer_SetAudioRendererInfo()

```c
OH_AVErrCode OH_AVPlayer_SetAudioRendererInfo(OH_AVPlayer *player, OH_AudioStream_Usage streamUsage)
```

**Description**

Sets the audio stream type of the player.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage) streamUsage | Type of the audio stream set for the player. For the available values and applicable scenarios, see the definition of [OH_AudioStream_Usage](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_usage). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the audio stream type is set successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or the streamUsage value is invalid. |

### OH_AVPlayer_SetVolumeMode()

```c
OH_AVErrCode OH_AVPlayer_SetVolumeMode(OH_AVPlayer *player, OH_AudioStream_VolumeMode volumeMode)
```

**Description**

Sets the volume mode of the player's audio stream.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 19

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AudioStream_VolumeMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_volumemode) volumeMode | Specifies the volume mode of the audio stream. For the available values and applicable scenarios, see the definition of [OH_AudioStream_VolumeMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_volumemode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the volume mode of the audio stream is set successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or the volumeMode value is invalid.<br>         Returns AV_ERR_INVALID_STATE if the function is called in an invalid state. The player must be in the prepared state first.<br>         Returns AV_ERR_SERVICE_DIED if a system error occurs. |

### OH_AVPlayer_SetAudioInterruptMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioInterruptMode(OH_AVPlayer *player, OH_AudioInterrupt_Mode interruptMode)
```

**Description**

Sets the interruption mode of the player's audio stream.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AudioInterrupt_Mode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_mode) interruptMode | Interruption mode used by the player's audio stream. For the available values and applicable scenarios, see [OH_AudioInterrupt_Mode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_mode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the interruption mode of the audio stream is set successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or the interruptMode value is invalid. |

### OH_AVPlayer_SetAudioEffectMode()

```c
OH_AVErrCode OH_AVPlayer_SetAudioEffectMode(OH_AVPlayer *player, OH_AudioStream_AudioEffectMode effectMode)
```

**Description**

Sets the sound effect mode of the player's audio stream.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AudioStream_AudioEffectMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode) effectMode | Sound effect mode used by the player's audio stream. For the available values and applicable scenarios, see [OH_AudioStream_AudioEffectMode](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_audioeffectmode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the sound effect mode of the audio stream is set successfully.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer or effectMode is invalid. |

### OH_AVPlayer_SelectBitRate()

```c
OH_AVErrCode OH_AVPlayer_SelectBitRate(OH_AVPlayer *player, uint32_t bitRate)
```

**Description**

Sets the bit rate used by the HLS player. This interface is valid only for HLS network streams. It can be called only when the AVPlayer is in the prepared, playing, or paused state.<br> By default, the player selects an appropriate bit rate and speed based on the network connection.<br> The valid bit rate list is reported through INFO_TYPE_BITRATE_COLLECT. If the bit rate specified by the user is not in this list, the player selects the closest bit rate from the available bit rate list.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| uint32_t bitRate | Bit rate, in bits per second (bps). Select an appropriate bit rate based on the network bandwidth. In a low-bandwidth environment, select a lower bit rate; in a high-bandwidth environment, select a higher bit rate. By default, the player automatically selects an appropriate bit rate. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br> AV_ERR_OK: the bit rate is set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or SelectBitRate fails to be executed on the player. |

### OH_AVPlayer_SetVideoSurface()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSurface(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Sets the video surface window.<br> This function must be called after SetSource and before Prepare.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OHNativeWindow](../apis-avcodec-kit/capi-codecbase-nativewindow.md) *window | Pointer to an OHNativeWindow instance. This parameter must be set after SetSource and before Prepare. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the video surface window is set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, the input window is a null pointer, or SetVideoSurface fails to be executed on the player. |

### OH_AVPlayer_GetDuration()

```c
OH_AVErrCode OH_AVPlayer_GetDuration(OH_AVPlayer *player, int32_t *duration)
```

**Description**

Obtains the total duration of the media file, accurate to milliseconds. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t *duration | Output parameter used to obtain the total duration of the media file, accurate to milliseconds. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: the media file duration is obtained successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or the player fails to execute GetDuration. |

### OH_AVPlayer_GetState()

```c
OH_AVErrCode OH_AVPlayer_GetState(OH_AVPlayer *player, AVPlayerState *state)
```

**Description**

Gets the current playback state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [AVPlayerState](capi-avplayer-base-h.md#avplayerstate) *state | Pointer to the current playback state. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the current playback state is obtained successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer, or if player GetState fails to execute. |

### OH_AVPlayer_IsPlaying()

```c
bool OH_AVPlayer_IsPlaying(OH_AVPlayer *player)
```

**Description**

Checks whether the player is playing. This interface can be called when the AVPlayer is in any state, but the validity of the returned result depends on the current state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | Returns true if the player is playing; returns false if the player is not playing or the input player is a null pointer. |

### OH_AVPlayer_IsLooping()

```c
bool OH_AVPlayer_IsLooping(OH_AVPlayer *player)
```

**Description**

Checks whether loop playback is enabled. This interface can be called when the AVPlayer is in any state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if loop playback is enabled; false if loop playback is not enabled or the input player is a null pointer. |

### OH_AVPlayer_SetLooping()

```c
OH_AVErrCode OH_AVPlayer_SetLooping(OH_AVPlayer *player, bool loop)
```

**Description**

Sets loop playback. Loop playback is disabled by default.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| bool loop | Whether to enable loop playback. The value true means to enable loop playback, and false means to disable loop playback.  |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | AV_ERR_OK: loop playback is set successfully.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or SetLooping fails to be executed on player. |

### OH_AVPlayer_SetPlayerCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPlayerCallback(OH_AVPlayer *player, AVPlayerCallback callback)
```

**Description**

Sets the player callback function.<br> The information listening callback function [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and the error listening callback function [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) set through this method can convey only limited information, and it is inconvenient for applications to distinguish between multiple player instances.<br> Since API version 12, use [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback) and [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback) to set the information listening callback function [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) and the error listening callback function [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback), respectively.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Deprecated version**: 12

**Alternative APIs:** [OH_AVPlayer_SetOnInfoCallback](#oh_avplayer_setoninfocallback), [OH_AVPlayer_SetOnErrorCallback](#oh_avplayer_setonerrorcallback)

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) callback | Pointer to the callback object used to receive player event callbacks. It contains callback functions such as onInfo and onError. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the player callback is set successfully.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer, callback.onInfo or onError is null, or player SetPlayerCallback fails to execute. |

### OH_AVPlayer_SelectTrack()

```c
OH_AVErrCode OH_AVPlayer_SelectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Selects an audio or subtitle track.<br> By default, the first audio track that contains data is played, and no subtitle track is played.<br> After the setting takes effect, the original audio track becomes invalid. When selecting a subtitle track, the player must be in the prepared, playing, paused, or completed state. When selecting an audio track, the player must be in the prepared state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t index | Index of the audio or subtitle track. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br> Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer, or if SelectTrack fails to execute on player. |

### OH_AVPlayer_DeselectTrack()

```c
OH_AVErrCode OH_AVPlayer_DeselectTrack(OH_AVPlayer *player, int32_t index)
```

**Description**

Deselects the current audio or subtitle track. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t index | Index of the audio or subtitle track. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer or the player DeselectTrack operation fails. |

### OH_AVPlayer_GetCurrentTrack()

```c
OH_AVErrCode OH_AVPlayer_GetCurrentTrack(OH_AVPlayer *player, int32_t trackType, int32_t *index)
```

**Description**

Obtains the current valid track index. When this API is called, the player must be in the prepared, playing, paused, or completed state.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t trackType | Media type. 0: audio, 1: video. |
| int32_t *index | Index. Used to obtain the current track index (output parameter). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the track index is obtained successfully.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or if player GetCurrentTrack fails to execute. |

### OH_AVPlayer_SetMediaKeySystemInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetMediaKeySystemInfoCallback(OH_AVPlayer *player, Player_MediaKeySystemInfoCallback callback)
```

**Description**

Sets the media key system information callback of the player. This API applies to scenarios of playing DRM-encrypted media content, such as listening for DRM information updates, obtaining encryption content keys, and processing copyright-protected content.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [Player_MediaKeySystemInfoCallback](capi-avplayer-h.md#player_mediakeysysteminfocallback) callback | Pointer to the DRM information update callback, used to receive update events of the player's DRM key system information. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if player/callback is a null pointer, or if SetDrmSystemInfoCallback fails. |

### OH_AVPlayer_GetMediaKeySystemInfo()

```c
OH_AVErrCode OH_AVPlayer_GetMediaKeySystemInfo(OH_AVPlayer *player, DRM_MediaKeySystemInfo *mediaKeySystemInfo)
```

**Description**

Obtains the media key system information to create a media key session.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance. |
| [DRM_MediaKeySystemInfo](capi-avplayer-drm-mediakeysysteminfo.md) *mediaKeySystemInfo | Media key system information. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns **AV_ERR_OK** if the operation is successful.<br>         Returns **AV_ERR_INVALID_VAL** if the input parameter **player** is nullptr or the memory is insufficient. |

### OH_AVPlayer_SetDecryptionConfig()

```c
OH_AVErrCode OH_AVPlayer_SetDecryptionConfig(OH_AVPlayer *player, MediaKeySession *mediaKeySession, bool secureVideoPath)
```

**Description**

Sets the decryption information. This API applies to scenarios involving DRM-encrypted media content, such as playing encrypted videos, playing paid content, and playing copyright-protected media resources.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [MediaKeySession](capi-avplayer-mediakeysession.md) *mediaKeySession | Media key session instance with decryption capability. |
| bool secureVideoPath | Whether a secure decoder is required. **true** if required, **false** otherwise. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>Returns AV_ERR_OK if the operation is successful.<br>Returns AV_ERR_INVALID_VAL if **player** is a null pointer or if SetDecryptionConfig fails to execute on **player**. |

### OH_AVPlayer_SetOnInfoCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnInfoCallback(OH_AVPlayer *player, OH_AVPlayerOnInfoCallback callback, void *userData)
```

**Description**

Sets the callback function for listening to player messages.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) callback | Pointer to the callback function to be invoked. A null pointer indicates that the player message callback listener is unset. |
| void *userData | Pointer to the instance set by the application caller. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_NO_MEMORY if memory allocation fails. Release the memory and try again.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer or the function fails to execute. |

### OH_AVPlayer_SetOnErrorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetOnErrorCallback(OH_AVPlayer *player, OH_AVPlayerOnErrorCallback callback, void *userData)
```

**Description**

Sets the error callback listener of the player.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) callback | Pointer to the callback listener to be executed. A null pointer indicates that the player error callback listener is unset. |
| void *userData | Pointer to the instance set by the application caller. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_NO_MEMORY if memory allocation fails. Retry after releasing memory.<br>         Returns AV_ERR_INVALID_VAL if player is a null pointer or the function execution fails. |

### OH_AVPlayer_GetMediaDescription()

```c
OH_AVFormat *OH_AVPlayer_GetMediaDescription(OH_AVPlayer *player)
```

**Description**

Obtains the media source information of the player. This interface can be called after the playback resource is set and the player is in the initialized/prepared/playing/paused/completed/stopped state.<br> Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 22

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the media information of the player if the operation succeeds; nullptr otherwise.<br> Possible causes of failure:<br>   1. The input player pointer is invalid.<br>   2. The set playback resource is invalid. |

### OH_AVPlayer_GetTrackDescription()

```c
OH_AVFormat *OH_AVPlayer_GetTrackDescription(OH_AVPlayer *player, uint32_t index)
```

**Description**

Gets the track information of the player's media source by index. This interface can be called after the playback resource is set and the player is in the initialized/prepared/playing/paused/completed/stopped state.<br> Note that the lifecycle of the returned **OH_AVFormat** pointer object must be released manually by the user.

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 22

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| uint32_t index | Track index. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Returns the track information by index if the operation is successful; returns nullptr otherwise.<br> Possible causes of failure:<br>   1. The player pointer passed in is invalid.<br>   2. The playback resource set is invalid.<br>   3. The track index is out of the bounds of the playback source file array. |

### OH_AVPlayer_AddFdSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddFdSubtitleSource(OH_AVPlayer *player, int32_t fd, int64_t offset, int64_t size)
```

**Description**

Adds a file descriptor subtitle source to the player. Currently, external subtitles must be set after the fdSrc of the video source is set for the AVPlayer.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t fd | File descriptor of the subtitle source. |
| int64_t offset | Offset of the media source in the file descriptor. |
| int64_t size | Size of the media source, in bytes, used to specify the length of media data to read from the file descriptor. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_AddUrlSubtitleSource()

```c
OH_AVErrCode OH_AVPlayer_AddUrlSubtitleSource(OH_AVPlayer *player, const char *url)
```

**Description**

Adds a URL subtitle source to the player. The external subtitle must be set after the URL is set for the AVPlayer.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| const char *url | URL of the subtitle source, which supports the HTTP/HTTPS protocol. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_SetPlaybackRange()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackRange(OH_AVPlayer *player, int32_t mSecondsStart, int32_t mSecondsEnd, bool closestRange)
```

**Description**

Sets the playback start and end positions. Only the content within the specified range is played. This API can be called in the initialized, prepared, paused, stopped, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t mSecondsStart | Playback start position, which must be within [0, duration). The value -1 indicates that no start position is set, and playback starts from 0. If the value is out of range, the error code AV_ERR_INVALID_VAL (invalid parameter) is returned, or the value is automatically corrected to the boundary value. |
| int32_t mSecondsEnd | Playback end position, which must be within (mSecondsStart, duration]. The value -1 indicates that no end position is set, and playback ends at the end of the stream. |
| bool closestRange | Whether to synchronize to the frame closest to the specified time point. The value true synchronizes to the closest frame (suitable for scenarios that require a precise playback position), and false does not synchronize to the closest frame (suitable for scenarios that do not require a precise playback position). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer.<br>         AV_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. |

### OH_AVPlayer_SetMediaMuted()

```c
OH_AVErrCode OH_AVPlayer_SetMediaMuted(OH_AVPlayer *player, OH_MediaType mediaType, bool muted)
```

**Description**

Mutes the media stream. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype) mediaType | Specified media type. Available values: MEDIA_TYPE_AUD (audio type, used to mute the audio stream) and MEDIA_TYPE_VID (video type, used to mute the video stream). For details, see [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype). |
| bool muted | Whether to mute. The value true means to mute, and false means to unmute. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: invalid input parameter.<br>         AV_ERR_OPERATE_NOT_PERMIT: operation not permitted. |

### OH_AVPlayer_GetPlaybackPosition()

```c
int32_t OH_AVPlayer_GetPlaybackPosition(OH_AVPlayer *player)
```

**Description**

Gets the current playback position, accurate to milliseconds. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Playback position in milliseconds.<br>         Returns -1 if player is a null pointer or invalid. |

### OH_AVPlayer_IsSeekContinuousSupported()

```c
bool OH_AVPlayer_IsSeekContinuousSupported(OH_AVPlayer *player)
```

**Description**

Checks whether the media source supports continuous seeking. When called in the prepared, playing, paused, or completed state, the actual value is returned; when called in other states, false is returned. For devices that do not support the [AV_SEEK_CONTINUOUS](capi-avplayer-base-h.md#avplayerseekmode) seek operation, false is returned.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| bool | true if continuous seeking is supported.<br>          false if continuous seeking is not supported or the support state is uncertain. |

### OH_AVPlayer_SelectTrackWithMode()

```c
OH_AVErrCode OH_AVPlayer_SelectTrackWithMode(OH_AVPlayer *player, int32_t index, AVPlayerTrackSwitchMode mode)
```

**Description**

Selects a track using the specified switch mode when playing a resource that contains multiple audio or video tracks. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t index | Index of the track to select. |
| [AVPlayerTrackSwitchMode](capi-avplayer-base-h.md#avplayertrackswitchmode) mode | Switch mode. For the available values and applicable scenarios, see [AVPlayerTrackSwitchMode](capi-avplayer-base-h.md#avplayertrackswitchmode). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: invalid input parameter.<br>         AV_ERR_OPERATE_NOT_PERMIT: operation not permitted. |

### OH_AVPlayer_SetAmplitudeUpdateCallback()

```c
OH_AVErrCode OH_AVPlayer_SetAmplitudeUpdateCallback(OH_AVPlayer *player, OH_AVPlayerOnAmplitudeUpdateCallback callback, void *userData)
```

**Description**

Subscribes to the update event of the maximum audio level, which is reported periodically when an audio resource is being played. This is applicable to scenarios that require audio visualization or audio intensity detection, such as audio waveform display, audio intensity visualization, and audio energy detection.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AVPlayerOnAmplitudeUpdateCallback](capi-avplayer-base-h.md#oh_avplayeronamplitudeupdatecallback) callback | Callback invoked to return the maximum audio level. nullptr indicates that the callback is unregistered. |
| void *userData | Pointer to user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVPlayer_SetSeiReceivedCallback()

```c
OH_AVErrCode OH_AVPlayer_SetSeiReceivedCallback(OH_AVPlayer *player, const int32_t *payloadTypes, uint32_t typeNum, OH_AVPlayerOnSeiMessageReceivedCallback callback, void *userData)
```

**Description**

Subscribes to the event of receiving supplementary enhancement information (SEI) messages. This applies only to HTTP-FLV live streams and is triggered when SEI messages exist in the video stream. The subscription must be initiated before calling prepare.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. It must be called before prepare. |
| const int32_t *payloadTypes | Array of SEI message payload types, used to specify the SEI message types to subscribe to. The array size is specified by the typeNum parameter. |
| uint32_t typeNum | Size of the payload type array. |
| [OH_AVPlayerOnSeiMessageReceivedCallback](capi-avplayer-base-h.md#oh_avplayeronseimessagereceivedcallback) callback | Callback function pointer. nullptr indicates unregistering the callback. |
| void *userData | Pointer to user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer. |

### OH_AVSeiMessage_GetSeiCount()

```c
uint32_t OH_AVSeiMessage_GetSeiCount(OH_AVSeiMessageArray *message)
```

**Description**

Obtains the number of message items in the SEI message array.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) *message | Pointer to an OH_AVSeiMessageArray instance. |

**Return**

| Type | Description |
| -- | -- |
| uint32_t | Number of message items in the SEI message array. |

### OH_AVSeiMessage_GetSei()

```c
OH_AVFormat *OH_AVSeiMessage_GetSei(OH_AVSeiMessageArray *message, uint32_t index)
```

**Description**

Obtains the SEI of an item in the SEI (Supplemental Enhancement Information) message array by index. Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) *message | Pointer to an OH_AVSeiMessageArray instance. |
| uint32_t index | Index of the message item. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | SEI of the message item. A null pointer is returned if message is a null pointer or index is invalid. |

### OH_AVPlayer_SetTargetVideoWindowSize()

```c
OH_AVErrCode OH_AVPlayer_SetTargetVideoWindowSize(OH_AVPlayer *player, int32_t width, int32_t height)
```

**Description**

Sets the video window size for super resolution. This interface can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. The input parameter values must be within the range from 320x320 to 1920x1080. The unit is pixel (px). It applies to scenarios of super-resolution video display, such as quality enhancement of low-resolution videos and enhanced video display.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t width | Window width, in the range [320-1920], in pixels (px). If the value is out of range, the error code AV_ERR_INVALID_VAL (invalid parameter) is returned. |
| int32_t height | Window height, in the range [320-1080], in pixels (px). If the value is out of range, the error code AV_ERR_INVALID_VAL (invalid parameter) is returned. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer or the parameter is invalid.<br>         AV_ERR_OPERATE_NOT_PERMIT: the operation is not permitted.<br>         AV_ERR_SUPER_RESOLUTION_UNSUPPORTED: super resolution is not supported.<br>         AV_ERR_SUPER_RESOLUTION_NOT_ENABLED: super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md). |

### OH_AVPlayer_SetVideoSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlayer_SetVideoSuperResolutionEnable(OH_AVPlayer *player, bool enabled)
```

**Description**

Dynamically enables or disables super resolution. This interface can be called when the AVPlayer is in the idle, prepared, playing, paused, completed, or stopped state. Super resolution must be enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) before calling prepare. It applies to scenarios that require dynamic control of video quality enhancement, such as dynamically adjusting based on device performance or switching quality based on network status.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| bool enabled | Whether to enable super resolution. The value true means to enable super resolution, and false means to disable it. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer or the parameter is invalid.<br>         AV_ERR_OPERATE_NOT_PERMIT: the operation is not permitted.<br>         AV_ERR_SUPER_RESOLUTION_UNSUPPORTED: super resolution is not supported.<br>         AV_ERR_SUPER_RESOLUTION_NOT_ENABLED: super resolution is not enabled in [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md). |

### OH_AVPlaybackStrategy_Create()

```c
OH_AVPlaybackStrategy *OH_AVPlaybackStrategy_Create(void)
```

**Description**

Creates a playback strategy instance.

**Since**: 23

**Return**

| Type | Description |
| -- | -- |
| [OH_AVPlaybackStrategy *](capi-avplayer-oh-avplaybackstrategy.md) | Pointer to a playback strategy instance, or a null pointer on failure. |

### OH_AVPlaybackStrategy_Destroy()

```c
OH_AVErrCode OH_AVPlaybackStrategy_Destroy(OH_AVPlaybackStrategy *strategy)
```

**Description**

Destroys a playback strategy instance.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the OH_AVPlaybackStrategy playback strategy instance to be destroyed. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredWidth()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredWidth(OH_AVPlaybackStrategy *strategy, int32_t width)
```

**Description**

Selects a stream whose width is close to the specified width.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the OH_AVPlaybackStrategy used by the AVPlayer. |
| int32_t width | Preferred width, in pixels (px), of the stream selected when the AVPlayer starts. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredHeight()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHeight(OH_AVPlaybackStrategy *strategy, int32_t height)
```

**Description**

Selects a stream close to the specified height.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | OH_AVPlaybackStrategy used by the AVPlayer. |
| int32_t height | Preferred height, in pixels, of the stream selected when the AVPlayer starts. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredBufferDuration()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDuration(OH_AVPlaybackStrategy *strategy, int32_t ms)
```

**Description**

Selects a preferred buffer duration close to the specified value.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the OH_AVPlaybackStrategy used by the AVPlayer. |
| int32_t ms | Preferred buffer duration selected when the AVPlayer starts playback, in milliseconds (ms). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredHdr()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredHdr(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Enables or disables the preferred HDR mode.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| bool enabled | Whether to enable HDR. The value true means to enable HDR, and false means to disable it. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredSubtitleLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred subtitle language.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| const char *lang | Subtitle language code, which complies with the ISO639-1 standard and is 2 to 3 characters long (for example, "zh" or "en"). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredAudioLanguage()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredAudioLanguage(OH_AVPlaybackStrategy *strategy, const char *lang)
```

**Description**

Sets the preferred audio language.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| const char *lang | Audio language code in ISO639-1 format, with a length of 2 to 3 characters (for example, "zh" or "en"). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetMutedMediaType()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetMutedMediaType(OH_AVPlaybackStrategy *strategy, OH_MediaType mediaType)
```

**Description**

Sets the media type to be muted during playback.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype) mediaType | Media type to be muted. Available values: MEDIA_TYPE_AUD (audio type, used to mute the audio stream) and MEDIA_TYPE_VID (video type, used to mute the video stream). For details, see [OH_MediaType](../apis-avcodec-kit/capi-native-avcodec-base-h.md#oh_mediatype). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetShowFirstFrameOnPrepare(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to display the first frame during prepare.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| bool enabled | Whether to display the first frame. The value true means to display it, and false means not to display it. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetThresholdForAutoQuickPlay(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the threshold for automatic quick playback. When insufficient buffered data may cause playback stuttering, the player automatically increases the playback rate to quickly play the cached content. This threshold controls the condition that triggers this behavior.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| double seconds | Threshold for automatic quick playback, in seconds (s). |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetSuperResolutionEnable()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetSuperResolutionEnable(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Enables or disables super resolution.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| bool enabled | Whether to enable super resolution. The value **true** means to enable it, and **false** means to disable it. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetPreferredBufferDurationForPlaying(OH_AVPlaybackStrategy *strategy, double seconds)
```

**Description**

Sets the preferred buffer duration (in seconds, of the double type) for playback.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| double seconds | Buffer duration, in seconds. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlaybackStrategy_SetKeepDecodingOnMute()

```c
OH_AVErrCode OH_AVPlaybackStrategy_SetKeepDecodingOnMute(OH_AVPlaybackStrategy *strategy, bool enabled)
```

**Description**

Sets whether to continue decoding when muted.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to an OH_AVPlaybackStrategy instance. |
| bool enabled | Whether to continue decoding. The value **true** means to continue decoding, and **false** means to pause decoding when muted. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input strategy is a null pointer. |

### OH_AVPlayer_SetPlaybackStrategy()

```c
OH_AVErrCode OH_AVPlayer_SetPlaybackStrategy(OH_AVPlayer *player, OH_AVPlaybackStrategy *strategy)
```

**Description**

Sets the playback strategy for the AVPlayer. This interface can be called only when the AVPlayer is in the initialized state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. It must be called in the initialized state. |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) *strategy | Pointer to the OH_AVPlaybackStrategy playback strategy instance, used to set the playback strategy configuration for the player. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer.<br>         AV_ERR_OPERATE_NOT_PERMIT: the operation is not permitted. |

### OH_AVPlayer_GetPlaybackInfo()

```c
OH_AVFormat* OH_AVPlayer_GetPlaybackInfo(OH_AVPlayer *player)
```

**Description**

Obtains the statistics of the current player. This interface can only be called when the AVPlayer is in the prepared, playing, or paused state. Note that the lifecycle of the returned OH_AVFormat pointer must be released manually by the user.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. This parameter can be called only when the player is in the prepared, playing, or paused state. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to the OH_AVFormat instance.<br>         A null pointer is returned if player is a null pointer or invalid. |

### OH_AVPlayer_SetMediaSource()

```c
OH_AVErrCode OH_AVPlayer_SetMediaSource(OH_AVPlayer *player, OH_AVMediaSource *source)
```

**Description**

Sets an OH_AVMediaSource for the player.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| [OH_AVMediaSource](capi-avmedia-source-oh-avmediasource.md) *source | Pointer to an OH_AVMediaSource media source instance, which contains information such as the media URL and DRM configuration. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player or source is a null pointer, or the player fails to set the URL source. |

### OH_AVPlayer_GetTrackCount()

```c
uint32_t OH_AVPlayer_GetTrackCount(OH_AVPlayer *player)
```

**Description**

Obtains the number of tracks in the media source of the player. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| uint32_t | Number of tracks in the media source of the player. Returns 0 if player is a null pointer or invalid. |

### OH_AVPlayer_GetTrackFormat()

```c
OH_AVFormat *OH_AVPlayer_GetTrackFormat(OH_AVPlayer *player, uint32_t trackIndex)
```

**Description**

Obtains the track information of the player by index. This interface can be called only when the AVPlayer is in the prepared, playing, paused, or completed state.<br> Note that the lifecycle of the returned OH_AVFormat pointer object must be released manually by the user.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| uint32_t trackIndex | Index of the track array, in the range [0, trackCount-1], where trackCount can be obtained through OH_AVPlayer_GetTrackCount. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Pointer to an OH_AVFormat instance.<br>         A null pointer is returned if player is a null pointer or invalid, or if trackIndex is invalid. |

### OH_AVPlayer_GetPlaybackStatisticMetrics()

```c
OH_AVFormat *OH_AVPlayer_GetPlaybackStatisticMetrics(OH_AVPlayer *player)
```

**Description**

Gets the current player's statistical metric information. After the playback resource is set, and when the player is in the prepared, playing, paused, completed, or stopped state, this interface can be called.<br> Note that the lifecycle of the returned [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md) pointer object must be released manually by the user.

**Since**: 23

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVFormat *](../apis-avcodec-kit/capi-core-oh-avformat.md) | Statistical metric information of the player if the operation is successful (for key-value details, see [Variables](../apis-media-kit/capi-avplayer-base-h.md#variables) in avplayer_base.h); nullptr otherwise.<br> Possible failure cause: the passed player pointer is invalid. |

### OH_AVPlayer_SetPCMOutputCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMOutputCallback(OH_AVPlayer *player, OH_AVPlayerPCMOutputCallback callback, void *userData)
```

**Description**

Sets the callback for audio PCM data output. This interface can be called when the player is in the idle or initialized state. It applies to scenarios where raw audio data is required, such as audio data analysis, audio recording, audio processing, and audio visualization.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. This interface must be called when the player is in the idle or initialized state. |
| [OH_AVPlayerPCMOutputCallback](capi-avplayer-base-h.md#oh_avplayerpcmoutputcallback) callback | Callback function pointer. nullptr indicates unregistering the callback. |
| void *userData | Pointer to the user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVErrCode](../apis-avcodec-kit/capi-native-averrors-h.md#oh_averrcode) | Result code.<br>         Returns AV_ERR_OK if the operation is successful.<br>         Returns AV_ERR_INVALID_VAL if the input player is a null pointer or the player fails to set the PCM output callback.<br>         Returns AV_ERR_OPERATE_NOT_PERMIT if the API is called in an unsupported state. |

### OH_AVPlayer_SetVideoSideOutput()

```c
OH_AVPlayerVideoOutput* OH_AVPlayer_SetVideoSideOutput(OH_AVPlayer *player, OHNativeWindow *window)
```

**Description**

Sets the callback for outputting decoded video frames. This API can be called when the player is in the idle or initialized state. It applies to scenarios where decoded video frames need to be obtained, such as video frame analysis, video filter processing, video screenshot, and video effect processing.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. This API must be called when the player is in the idle or initialized state. |
| [OHNativeWindow](../apis-avcodec-kit/capi-codecbase-nativewindow.md) *window | Pointer to an OHNativeWindow instance. For details, see OHNativeWindow. |

**Return**

| Type | Description |
| -- | -- |
| [OH_AVPlayerVideoOutput*](capi-avplayer-oh-avplayervideooutput.md) | Pointer to an OH_AVPlayerVideoOutput instance. nullptr indicates a failure.<br> Possible causes of failure:<br> 1. The player pointer passed in is invalid.<br> 2. The window pointer passed in is invalid. |

### OH_AVPlayerVideoOutput_GetNewestVideoSample()

```c
OH_VideoOutputResult OH_AVPlayerVideoOutput_GetNewestVideoSample(OH_AVPlayerVideoOutput *videoOutput)
```

**Description**

Obtains a decoded video frame. This interface can be called when the player is in the paused or playing state. It applies to scenarios where the current video frame needs to be obtained, such as video frame capture, video frame analysis, video screenshot, and video frame processing.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayerVideoOutput](capi-avplayer-oh-avplayervideooutput.md) *videoOutput | Pointer to the OH_AVPlayerVideoOutput instance returned by OH_AVPlayer_SetVideoSideOutput. |

**Return**

| Type | Description |
| -- | -- |
| [OH_VideoOutputResult](capi-avplayer-base-h.md#oh_videooutputresult) | OH_VIDEO_OUTPUT_OK (corresponding value): a decoded video frame is obtained.<br>         OH_VIDEO_OUTPUT_NO_IMAGE (corresponding value): no renderable frame is available. |

### OH_AVPlayer_SetPCMProcessorCallback()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorCallback(OH_AVPlayer *player, OH_AVPlayerPCMProcessorCallback callback, void *userData)
```

**Description**

Sets the audio PCM data post-processing callback. When the player is in the idle or initialized state, this interface can be called.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to the OH_AVPlayer instance. |
| [OH_AVPlayerPCMProcessorCallback](capi-avplayer-base-h.md#oh_avplayerpcmprocessorcallback) callback | Callback function pointer. nullptr indicates that the callback is unregistered. |
| void *userData | Pointer to the user-defined data. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVErrCode | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or the player fails to set the PCM processor callback.<br>         AV_ERR_OPERATE_NOT_PERMIT: called in an unsupported state. |

### OH_AVPlayer_SetPCMProcessorMaxLen()

```c
OH_AVErrCode OH_AVPlayer_SetPCMProcessorMaxLen(OH_AVPlayer *player, int32_t maxProcessedPCMLen)
```

**Description**

Sets the maximum amount of data that the audio post-processing callback can return at a time. Partial data can be buffered and output together with the PCM data returned next time.<br> This interface can be called when the player is in the idle or initialized state.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance. |
| int32_t maxProcessedPCMLen | Maximum amount of data that can be returned at a time. The unit is byte, and the value range is (0, 5 MB].<br> OH_AVPlayerPCMProcessorCallback guarantees that the capacity of the returned AVBuffer is not less than this value. |

**Return**

| Type | Description |
| -- | -- |
| OH_AVErrCode | Result code.<br>         AV_ERR_OK: success.<br>         AV_ERR_INVALID_VAL: the input player is a null pointer, or the maxProcessedPCMLen parameter is invalid.<br>         AV_ERR_OPERATE_NOT_PERMIT: called in an unsupported state. |


