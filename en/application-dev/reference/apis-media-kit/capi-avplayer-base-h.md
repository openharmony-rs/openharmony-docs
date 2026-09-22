# avplayer_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @dongyu_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the structs and enums of the AVPlayer.

**File to include**: <multimedia/player_framework/avplayer_base.h>

**Library**: libavplayer.so

**System capability**: SystemCapability.Multimedia.Media.AVPlayer

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

## Summary

### Structs

| Name| typedef Keyword| Description| 
| -- | -- | -- | 
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) | AVPlayerCallback | Defines a set of pointers to the [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) callbacks.<br>To ensure the normal running of AVPlayer, you must register this struct with the OH_AVPlayer instance using **OH_AVPlayer_SetPlayerCallback** and process the information reported by the callbacks.|
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) | OH_AVPlayer | Describes an initialized AVPlayer.| 
| [OH_AVSeiMessageArray](./capi-avplayer-oh-avseimessagearray.md) | OH_AVSeiMessageArray | Defines the SEI message array.| 
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) | OH_AVPlaybackStrategy | Defines the audio and video playback strategy.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVPlayerState](#avplayerstate) | AVPlayerState | Enumerates the AVPlayer states.|
| [AVPlayerSeekMode](#avplayerseekmode) | AVPlayerSeekMode | Enumerates the seek modes.|
| [AVPlaybackSpeed](#avplaybackspeed) | AVPlaybackSpeed | Enumerates the playback speeds of the AVPlayer.|
| [AVPlayerOnInfoType](#avplayeroninfotype) | AVPlayerOnInfoType | Enumerates the **OnInfo** types, which can be used to indicate the type of information received by the AVPlayer.<br>It can be used in **OH_AVPlayerOnInfoCallback** and **OH_AVPlayerOnInfo** (deprecated).<br>Since API version 12, you are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback). Different information (**infoBody**) can be obtained for different **OnInfo** types. **infoBody** contains the key-value pairs. For details, see the following enumerated value table.<br>If you are using API version 11 for development, use **OH_AVPlayerOnInfo (deprecated)**. For details about how to use the deprecated API **OH_AVPlayerOnInfo**, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).|
| [AVPlayerBufferingType](#avplayerbufferingtype) | AVPlayerBufferingType | Enumerates the types of buffer messages of the AVPlayer.|
| [AVPlayerTrackSwitchMode](#avplayertrackswitchmode) | AVPlayerTrackSwitchMode | Enumerates the track switching modes.|
| [OH_VideoOutputResult](#oh_videooutputresult) | OH_VideoOutputResult | Enumerates the video output results.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)](#oh_avplayeroninfo) | OH_AVPlayerOnInfo | This API is supported since API version 11 and deprecated since API version 12. You are advised to use [OH_AVPlayerOnInfoCallback](#oh_avplayeroninfocallback) instead.|
| [typedef void (\*OH_AVPlayerOnInfoCallback)(OH_AVPlayer \*player, AVPlayerOnInfoType type, OH_AVFormat\* infoBody, void \*userData)](#oh_avplayeroninfocallback) | OH_AVPlayerOnInfoCallback | Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo** function will not be invoked.|
| [typedef void (\*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)](#oh_avplayeronerror) | OH_AVPlayerOnError | This API is supported since API version 11 and deprecated since API version 12. You are advised to use [OH_AVPlayerOnErrorCallback](#oh_avplayeronerrorcallback) instead.|
| [typedef void (\*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avplayeronerrorcallback) | OH_AVPlayerOnErrorCallback | Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError** function will not be invoked.|
| [typedef void (\*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)](#oh_avplayeronamplitudeupdatecallback) | OH_AVPlayerOnAmplitudeUpdateCallback | Called when the maximum audio amplitude is calculated.|
| [typedef void (\*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)](#oh_avplayeronseimessagereceivedcallback) | OH_AVPlayerOnSeiMessageReceivedCallback | Called for obtaining supplemental enhancement information (SEI) messages. This function is used to subscribe to SEI message events and returns detailed SEI information.|
| [typedef void (\*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmoutputcallback) | OH_AVPlayerPCMOutputCallback | Called for obtaining the output of audio pulse code modulation (PCM) data. This function applies to scenarios such as audio data analysis and visualization.|
| [typedef void (\*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmprocessorcallback) | OH_AVPlayerPCMProcessorCallback | Called for obtaining the audio PCM data to be post-processed. AVPlayer needs to use the processed data for audio playback, and the processing must be completed before the callback is returned. Otherwise, the playback will be blocked. This function is applicable to scenarios such as real-time audio processing and special effect addition.<br> Do not change the sampling rate, number of audio channels, or sampling format when using this method to avoid failure to obtain data.|

### Variables

| Name| Description|
| -- | -- |
| const char * OH_PLAYER_STATE | Pointer to the key for obtaining the AVPlayer state. The value is of the int32_t type.<br>**Since**: 12|
| const char * OH_PLAYER_STATE_CHANGE_REASON | Pointer to the key for obtaining the AVPlayer state change reason. The value is of the int32_t type.<br> 1. It can be triggered by user operations, for example, when an app calls the **play**, **pause**, or **stop** API. 2. It can be triggered by system changes, for example, when an app is switched to the background, the playback state automatically pauses.<br>**Since**: 12|
| const char * OH_PLAYER_VOLUME | Pointer to the key for obtaining the volume. The value type is float. The value range is [0.0, 1.0].<br>**Since**: 12|
| const char * OH_PLAYER_BITRATE_ARRAY | Pointer to the key for obtaining the bit rate array, in bit/s. The value is of the uint8_t byte array type. When this key is used to obtain information, you need to:<br> Use a pointer variable of the uint8_t type to store the bit rate list and use a variable of the size_t type to store the byte array length.<br> Then it allocates several storage spaces of the uint32_t type to receive the bit rate integer of the uint32_t type, which is converted from the uint8_t byte array.<br>**Since**: 12|
| const char * OH_PLAYER_AUDIO_INTERRUPT_TYPE | Pointer to the key for obtaining the audio interruption type. The value is of the int32_t type. The value **1** means that the audio interruption event starts, and **2** means that the interruption event ends.<br>**Since**: 12|
| const char * OH_PLAYER_AUDIO_INTERRUPT_FORCE | Pointer to the key for obtaining the FORCE type of audio interruption. The value is of the int32_t type. The value **0** means forcible interruption (the system changes the audio playback status), and **1** means sharing interruption (the application changes the audio playback status).<br>**Since**: 12|
| const char * OH_PLAYER_AUDIO_INTERRUPT_HINT | Pointer to the key for obtaining the HINT type of audio interruption. The value is of the int32_t type. The value **0** (NONE) means no hint; **1** (RESUME) means that the audio playback is resumed; **2** (PAUSE) means that the audio playback is paused and loses focus; **3** (STOP) means that the audio playback is stopped; **4** (DUCK) means that the audio volume is reduced; **5** (UNDUCK) means that the audio volume is restored.<br>**Since**: 12|
| const char * OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON | Pointer to the key for obtaining the audio device change reason. The value is of the int32_t type. For details, see **OH_AudioStream_DeviceChangeReason**.<br>**Since**: 12|
| const char * OH_PLAYER_BUFFERING_TYPE | Pointer to the key for obtaining the type of the buffer update message. The value type is [AVPlayerBufferingType](#avplayerbufferingtype).<br> When this key is used to obtain information, you must use a variable of the int32_t type to save the result and then convert the result to a value of **AVPlayerBufferingType**.<br>**Since**: 12|
| const char * OH_PLAYER_BUFFERING_VALUE | Pointer to the key for obtaining the value of the buffer update message. The value is of the int32_t type. For details, see [AVPlayerBufferingType](#avplayerbufferingtype).<br> This parameter is valid only when the buffer update message type is **AVPLAYER_BUFFERING_PERCENT** or **AVPLAYER_BUFFERING_CACHED_DURATION**.<br>**Since**: 12|
| const char * OH_PLAYER_SEEK_POSITION | Pointer to the key for obtaining the playback progress after the seek operation, in milliseconds (ms). The value is of the int32_t type.<br>**Since**: 12|
| const char * OH_PLAYER_PLAYBACK_SPEED | Pointer to the key for obtaining the playback speed. The value type is [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).<br> When this key is used to obtain information, you must use a variable of the int32_t type to save the result and then convert the result to a value of AVPlaybackSpeed.<br>**Since**: 12|
| const char * OH_PLAYER_PLAYBACK_RATE | Pointer to the key for obtaining the playback rate. The value is a floating-point number.<br>**Since**: 20|
| const char * OH_PLAYER_BITRATE | Pointer to the key for obtaining the bit rate, in bit/s. The value is of the uint32_t type.<br>**Since**: 12|
| const char * OH_PLAYER_CURRENT_POSITION | Pointer to the key for obtaining the playback progress information, in ms. The value is of the int32_t type.<br>**Since**: 12|
| const char * OH_PLAYER_DURATION | Pointer to the key for obtaining the duration of the media asset, in ms. The value type is int64_t.<br>**Since**: 12|
| const char * OH_PLAYER_VIDEO_WIDTH | Pointer to the key for obtaining the video weight, in px. The value type is int32_t.<br>**Since**: 12|
| const char * OH_PLAYER_VIDEO_HEIGHT | Pointer to the key for obtaining the video height, in px. The value type is int32_t.<br>**Since**: 12|
| const char * OH_PLAYER_MESSAGE_TYPE | Pointer to the key for obtaining the type of message received by the AVPlayer. The value is of the int32_t type.<br> The value **1** means that the video frame starts to be rendered.<br>**Since**: 12|
| const char * OH_PLAYER_IS_LIVE_STREAM | Pointer to the key for checking whether a media asset is live streaming. The value is of the int32_t type. The value **0** means a non-live stream, and **1** means a live stream.<br>**Since**: 12|
| const char * OH_PLAYER_MD_KEY_HAS_VIDEO | Pointer to the key for obtaining whether the media resource contains video tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains video tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_HAS_AUDIO | Pointer to the key for obtaining whether the media resource contains audio tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains audio tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_HAS_SUBTITLE | Pointer to the key for obtaining whether the media resource contains subtitle tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains subtitle tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_TRACK_INDEX | Pointer to the key for obtaining the track index information of a media resource. The value is of the int32_t type.<br>**Since**: 22|
| const char * OH_PLAYER_SEI_PAYLOAD_TYPE | Pointer to the key for indicating the payload type in an SEI message.<br>**Since**: 23|
| const char * OH_PLAYER_SEI_PAYLOAD_CONTENT | Pointer to the key for indicating the payload content in an SEI message.<br>**Since**: 23|
| const char * OH_PLAYER_SUPER_RESOLUTION_ENABLE_STATE | Pointer to the key for indicating the enable state of the super resolution feature. The value type is int32_t. The value **1** indicates that the feature is enabled, and **0** indicates the opposite. It is used for information callback when the super resolution state changes.<br>**Since**: 23|
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX | Pointer to the key for indicating the track index in the track change information. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED | Pointer to the key for indicating whether the track is selected in the track change information. The value type is int32_t. The value **1** means that the track is selected, and **0** means the opposite.<br>**Since**: 23|
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION | Pointer to the key for indicating the duration in the subtitle update information, in ms. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME | Pointer to the key for indicating the start time in the subtitle update information, in ms. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT | Pointer to the key for indicating the subtitle text content in the subtitle update information. The value type is string.<br>**Since**: 23|
| const char * OH_PLAYER_SERVER_IP_ADDRESS | Pointer to the key for indicating the server IP address in the playback information. The value is a string.<br>**Since**: 23|
| const char * OH_PLAYER_IS_DOWNLOADING | Pointer to the key for indicating whether the download is in progress in the playback information. The value type is int32_t. The value **1** indicates that the download is in progress, and the value **0** indicates that the download is not in progress.<br>**Since**: 23|
| const char * OH_PLAYER_BUFFER_DURATION | Pointer to the key for indicating the buffer duration in the playback information, in ms. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_DOWNLOAD_RATE | Pointer to the key for indicating the current download rate in the playback information, in bit/s. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_AVG_DOWNLOAD_RATE | Pointer to the key for indicating the average download rate in the playback information, in bit/s. The value type is int32_t.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_PREPARE_DURATION | Pointer to the key for obtaining the preparation duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_RESOURCE_CONNECTION_DURATION | Pointer to the key for obtaining the resource connection duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_FIRST_FRAME_DECAPSULATION_DURATION | Pointer to the key for obtaining the first-frame decapsulation duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_TOTAL_PLAYING_TIME | Pointer to the key for obtaining the total playback duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_REQUEST_COUNT | Pointer to the key for obtaining the total number of media resource loading requests in the statistic metric information. The value type is uint32_t.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_TIME | Pointer to the key for obtaining the total media resource loading duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_SIZE | Pointer to the key for obtaining the total size of loaded media resources in the statistic metric information. The value type is int64_t.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_STALLING_COUNT | Pointer to the key for obtaining the total number of stalling times in the statistic metric information. The value type is uint32_t.<br>**Since**: 23|
| const char * OH_MEDIA_EVENT_INFO_TOTAL_STALLING_TIME | Pointer to the key for obtaining the total stalling duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23|

## Enum Description

### AVPlayerState

```c
enum AVPlayerState
```

**Description**

Enumerates the AVPlayer states.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| AV_IDLE = 0 | Idle.|
| AV_INITIALIZED = 1 | Initialized.|
| AV_PREPARED = 2 | Ready.|
| AV_PLAYING = 3 | Playing.|
| AV_PAUSED = 4 | Paused.|
| AV_STOPPED = 5 | Stopped.|
| AV_COMPLETED = 6 | Completed.|
| AV_RELEASED = 7 | Released.|
| AV_ERROR = 8 | Error.|

### AVPlayerSeekMode

```c
enum AVPlayerSeekMode
```

**Description**

Enumerates the seek modes.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| AV_SEEK_NEXT_SYNC = 0 | Seeks to the next key frame at the specified position.|
| AV_SEEK_PREVIOUS_SYNC | Seeks to the previous key frame at the specified position.| 
| AV_SEEK_CLOSEST = 2 | Seeks to the frame closest to the specified position.<br>**Since**: 12|
| AV_SEEK_CONTINUOUS = 3 | Seeks in continuous drag mode. This mode provides a smoother drag experience, but the device must support continuous seeking for the current stream. Before using this mode, check whether continuous seeking is supported. For details, see [OH_AVPlayer_IsSeekContinuousSupported](capi-avplayer-h.md#oh_avplayer_isseekcontinuoussupported).<br>**Since**: 23|


### AVPlaybackSpeed

```c
enum AVPlaybackSpeed
```

**Description**

Enumerates the playback speeds of the AVPlayer.

**Since**: 11

| Enum Item| Description|
| -- | -- |
| AV_SPEED_FORWARD_0_75_X | Plays the video at 0.75 times the normal speed.|
| AV_SPEED_FORWARD_1_00_X | Plays the video at the normal speed.|
| AV_SPEED_FORWARD_1_25_X | Plays the video at 1.25 times the normal speed.|
| AV_SPEED_FORWARD_1_75_X | Plays the video at 1.75 times the normal speed.|
| AV_SPEED_FORWARD_2_00_X | Plays the video at 2.0 times the normal speed.|
| AV_SPEED_FORWARD_0_50_X | Plays the video at 0.5 times the normal speed.<br>**Since**: 12|
| AV_SPEED_FORWARD_1_50_X | Plays the video at 1.5 times the normal speed.<br>**Since**: 12|
| AV_SPEED_FORWARD_3_00_X | Plays the video at 3.0 times the normal speed.<br>**Since**: 13|
| AV_SPEED_FORWARD_0_25_X | Plays the video at 0.25 times the normal speed.<br>**Since**: 13|
| AV_SPEED_FORWARD_0_125_X | Plays the video at 0.125 times the normal speed.<br>**Since**: 13|

### AVPlayerOnInfoType

```c
enum AVPlayerOnInfoType
```

**Description**

Enumerates the **OnInfo** types, which can be used to indicate the type of information received by the AVPlayer.<br>It can be used in **OH_AVPlayerOnInfoCallback** and **OH_AVPlayerOnInfo** (deprecated).<br>Since API version 12, you are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback). Different information (**infoBody**) can be obtained for different **OnInfo** types. **infoBody** contains the key-value pairs. For details, see the following enumerated value table.<br>If you are using API version 11 for development, use **OH_AVPlayerOnInfo (deprecated)**. For details about how to use the deprecated API **OH_AVPlayerOnInfo**, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).

**Since**: 11

| Enum Item| Description|
| -- | -- |
| AV_INFO_TYPE_SEEKDONE = 0 | Message returned when seeking to a playback position is complete.<br> If **key** is set to **OH_PLAYER_SEEK_POSITION**, the value is of the int32_t type, in ms. The value ranges from 0 to the media duration. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_SPEEDDONE = 1 | Message returned when the playback speed setting is complete.<br> If **key** is set to **OH_PLAYER_PLAYBACK_SPEED**, the value is an enumerated value of [AVPlaybackSpeed](#avplaybackspeed). The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value and forcibly converts the value to an enumerated value of [AVPlaybackSpeed](#avplaybackspeed).|
| AV_INFO_TYPE_BITRATEDONE = 2 | Message returned when the bit rate setting is complete.<br> If **key** is set to **OH_PLAYER_BITRATE**, the value type is uint32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value and forcibly converts the value to the uint32_t type.|
| AV_INFO_TYPE_EOS = 3 | Message returned when the playback is complete.|
| AV_INFO_TYPE_STATE_CHANGE = 4 | Message returned when the AVPlayer state changes.<br> If **key** is set to **OH_PLAYER_STATE**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value and forcibly converts the value to an enumerated value of [AVPlayerState](#avplayerstate).<br> If **key** is set to **OH_PLAYER_STATE_CHANGE_REASON**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. The value **1** means that the change is triggered by user operations, and **2** means that the change is triggered by the system.|
| AV_INFO_TYPE_POSITION_UPDATE = 5 | Message returned when the playback position changes.<br> If **key** is set to **OH_PLAYER_CURRENT_POSITION**, the value is of the int32_t type, in ms. The value ranges from 0 to the media duration. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_MESSAGE = 6 | Message returned when video rendering starts.<br> If **key** is set to **OH_PLAYER_MESSAGE_TYPE**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. The value **1** means that video rendering starts.|
| AV_INFO_TYPE_VOLUME_CHANGE = 7 | Message returned when the playback volume changes.<br> If **key** is set to **OH_PLAYER_VOLUME**, the value type is float. The system uses float to transfer the value, and the application uses float to obtain the value. The value range is [0.0, 1.0].|
| AV_INFO_TYPE_RESOLUTION_CHANGE = 8 | Message returned when the video size is obtained for the first time or the video size is updated.<br> If **key** is set to **OH_PLAYER_VIDEO_WIDTH** or **OH_PLAYER_VIDEO_HEIGHT**, the value type is int32_t, in px. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_BUFFERING_UPDATE = 9 | Message returned when multi-queue buffering changes.<br>If **key** is set to **OH_PLAYER_BUFFERING_TYPE**, the value is an enumerated value of [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype). The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value and forcibly converts the value to an enumerated value of [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype).<br>If **key** is set to **OH_PLAYER_BUFFERING_VALUE**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.<br>This value is valid when the buffer update message type is **AVPLAYER_BUFFERING_PERCENT** or **AVPLAYER_BUFFERING_CACHED_DURATION**, which indicate the percentage of the buffer progress and the duration that the cached data can play, respectively. The unit is ms.|
| AV_INFO_TYPE_BITRATE_COLLECT = 10 | Message returned to report the HTTP Live Streaming (HLS) video bit rates.<br>If **key** is set to **OH_PLAYER_BITRATE_ARRAY**, the value type is uint8_t.<br>The app uses a pointer variable of the uint8_t type to store the bit rate list and uses a variable of the size_t type to store the byte array length. Then, the app allocates several storage spaces of the uint32_t type and converts the uint8_t byte array into the bit rate integer value of the uint32_t type.|
| AV_INFO_TYPE_INTERRUPT_EVENT = 11 | Message returned when the audio focus changes.<br> The value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.<br> **key** can be set to any of the following values:<br> **OH_PLAYER_AUDIO_INTERRUPT_TYPE**: The value **1** means that the audio interruption event starts, and **2** means that the event ends.<br> **OH_PLAYER_AUDIO_INTERRUPT_FORCE**: The value **0** means forcible interruption (the system changes the audio playback status), and **1** means sharing interruption (the application changes the audio playback status).<br> **OH_PLAYER_AUDIO_INTERRUPT_HINT**: The value **0** (NONE) means no hint; **1** (RESUME) means that the audio playback is resumed; **2** (PAUSE) means that the audio playback is paused and loses focus; **3** (STOP) means that the audio playback is stopped; **4** (DUCK) means that the audio volume is reduced; **5** (UNDUCK) means that the audio volume is restored.|
| AV_INFO_TYPE_DURATION_UPDATE = 12 | Message returned when the playback duration changes.<br> If **key** is set to **OH_PLAYER_DURATION**, the value type is int64_t. The system uses int64_t to transfer the value, and the application uses int64_t to obtain the value.|
| AV_INFO_TYPE_IS_LIVE_STREAM = 13 | Message returned when live streams are played. If **key** is set to **OH_PLAYER_IS_LIVE_STREAM**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. The value **0** means a non-live stream, and **1** means a live stream.|
| AV_INFO_TYPE_TRACKCHANGE = 14 | Message returned when the track changes.<br> If the **key** is set to **OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX**, the value is of the int32_t type and indicates the index of the track after the track change.<br> If the **key** is set to **OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED**, the value is of the int32_t type. The value **1** means that the track is selected, and **0** means that the track is not selected.|
| AV_INFO_TYPE_TRACK_INFO_UPDATE = 15 | Message returned when the track is updated.<br> If **key** is set to **OH_PLAYER_MD_KEY_HAS_VIDEO**, the value type is int32_t. The value **1** indicates that video tracks are included, and the value **0** indicates that video tracks are not included.<br> If **key** is set to **OH_PLAYER_MD_KEY_HAS_AUDIO**, the value type is int32_t. The value **1** indicates that the audio track is included, and the value **0** indicates that the audio track is not included.<br> If **key** is set to **OH_PLAYER_MD_KEY_HAS_SUBTITLE**, the value type is int32_t. The value **1** indicates that the subtitle track is included, and the value **0** indicates that the subtitle track is not included.<br> If **key** is set to **OH_PLAYER_MD_KEY_TRACK_INDEX**, the value type is int32_t, indicating the index of the current track.|
| AV_INFO_TYPE_SUBTITLE_UPDATE = 16 | Message returned when the subtitle information is updated.<br> If **key** is set to **OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION**, the value type is int32_t, indicating the subtitle duration, in ms.<br> If **key** is set to **OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME**, the value type is int32_t, indicating the subtitle start time, in ms.<br> If **key** is set to **OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT**, the value type is string, indicating the subtitle text content.|
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE = 17 | Message returned when the audio output device changes.<br> If **key** is set to **OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_PLAYBACK_RATE_DONE = 18 | Message returned when the playback rate is applied.<br> If **key** is set to **OH_PLAYER_PLAYBACK_RATE**, the value type is float. The system uses float to transfer the value, and the application uses float to obtain the value.<br>**Since**: 20|
| AV_INFO_TYPE_SUPER_RESOLUTION_CHANGED = 19 | Message returned when the super resolution changes.<br> If **key** is set to **OH_PLAYER_SUPER_RESOLUTION_ENABLE_STATE**, the value type is int32_t. The value **1** indicates super resolution is enabled, and the value **0** indicates the opposite.<br>**Since**: 23|

### AVPlayerBufferingType

```c
enum AVPlayerBufferingType
```

**Description**

Enumerates the types of buffer messages of the AVPlayer.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AVPLAYER_BUFFERING_START = 1 | Buffering start message.|
| AVPLAYER_BUFFERING_END | Buffering end message.|
| AVPLAYER_BUFFERING_PERCENT | Buffer execution progress, in percentage. The value is an integer in the range [0, 100].|
| AVPLAYER_BUFFERING_CACHED_DURATION | Duration that cached data can be played, in milliseconds.|

### AVPlayerTrackSwitchMode

```c
enum AVPlayerTrackSwitchMode
```

**Description**

Enumerates the track switching modes.

**Since**: 23

| Enum Item| Description|
| -- | -- |
| AV_TRACK_SWITCH_MODE_SMOOTH = 0 | Switch tracks smoothly.|
| AV_TRACK_SWITCH_MODE_SEGMENT = 1 | Switch tracks by segment.|
| AV_TRACK_SWITCH_MODE_CLOSEST = 2 | Switch to the closest track.|

### OH_VideoOutputResult

```c
enum OH_VideoOutputResult
```

**Description**

Enumerates the video output results.

**Since**: 26.0.0

| Enum Item| Description|
| -- | -- |
| OH_VIDEO_OUTPUT_OK = 0 | A decoded video frame is output.|
| OH_VIDEO_OUTPUT_NO_IMAGE = 1 | No frame is available for rendering.|


## Function Description

### OH_AVPlayerOnInfo()

```c
typedef void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra);
```

**Description**

Called when the AVPlayer receives a message. If **OH_AVPlayerOnInfoCallback** is successfully set, this function will not be called.

> NOTE
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [OH_AVPlayerOnInfoCallback](#oh_avplayeroninfocallback) instead.

The following table lists the mappings between **type** and **extra** values.

| Value of type| Value of extra| 
| -------- | -------- | 
| AV_INFO_TYPE_SEEKDONE | Message returned when seeking to a playback position is complete. **extra** indicates the position after the seek operation.| 
| AV_INFO_TYPE_SPEEDDONE | Message returned when the playback speed setting is complete. **extra** indicates the playback speed. For details about the available options, see [AVPlaybackSpeed](#avplaybackspeed).| 
| AV_INFO_TYPE_BITRATEDONE | Message returned when the bit rate setting is complete. **extra** indicates the bit rate.| 
| AV_INFO_TYPE_EOS | Message returned when the playback is complete.| 
| AV_INFO_TYPE_STATE_CHANGE | Message returned when the AVPlayer state changes. **extra** indicates the new state. For details about the available options, see [AVPlayerState](#avplayerstate).| 
| AV_INFO_TYPE_POSITION_UPDATE | Message returned when the playback position changes. **extra** indicates the current position.| 
| AV_INFO_TYPE_MESSAGE | Message returned when video rendering starts. **extra** indicates the first video frame rendered.| 
| AV_INFO_TYPE_VOLUME_CHANGE | Message returned when the playback volume changes. **extra** is not defined in this scenario.| 
| AV_INFO_TYPE_RESOLUTION_CHANGE | Message returned when the video size is obtained for the first time or the video size is updated. **extra** is not defined in this scenario.| 
| AV_INFO_TYPE_BUFFERING_UPDATE | A buffer update message is returned. In this scenario, **extra** indicates buffer-related data. You are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) to obtain detailed buffer information.| 
| AV_INFO_TYPE_BITRATE_COLLECT  | Message returned to report the HLS video bit rates. Each bit rate has been converted into a uint8_t byte array during the reporting. You need to forcibly convert the uint8_t byte array into a uint32_t integer array.  | 
| AV_INFO_TYPE_INTERRUPT_EVENT | Message returned when the audio focus changes. **extra** indicates the hints provided along with audio interruption. For details about the available options, see [OH_AudioInterrupt_Hint](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_hint). The application can determine whether to perform further processing based on the hint.| 
| AV_INFO_TYPE_DURATION_UPDATE | Message returned when the playback duration changes. **extra** indicates the video duration.| 
| AV_INFO_TYPE_IS_LIVE_STREAM | Message returned when live streams are played. **extra** indicates whether the stream is a live stream. The value **0** means a non-live stream, and **1** means a live stream.| 
| AV_INFO_TYPE_TRACKCHANGE | Message returned when the track changes. **extra** is not defined in this scenario.| 
| AV_INFO_TYPE_TRACK_INFO_UPDATE | Message returned when the track information updates. **extra** has no specific meaning in this scenario.| 
| AV_INFO_TYPE_SUBTITLE_UPDATE | Message returned when the subtitle information changes. **extra** is not defined in this scenario.| 
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE | Message returned when the audio output device changes. **extra** indicates the device change reason. For details about the available options, see [OH_AudioStream_DeviceChangeReason](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason).|

**Since**: 11

**Deprecated from**: 12

**Substitute**: [OH_AVPlayerOnInfoCallback](#oh_avplayeroninfocallback)

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance.|
| [AVPlayerOnInfoType](#avplayeroninfotype) type | Message type. For details about the available options, see [AVPlayerOnInfoType](#avplayeroninfotype). For details about the mappings between **type** and **extra** values, see the function description.|
| int32_t extra | Additional information. The meaning of this parameter is determined by the **type** parameter. Different information types correspond to different additional information. For details about the mappings, see the table in the function description. For example, when **type** is set to **AV_INFO_TYPE_SEEKDONE**, **extra** indicates the playback position (in ms) to which the playback seeks. When **type** is set to **AV_INFO_TYPE_POSITION_UPDATE**, **extra** indicates the current playback position (in ms).|

### OH_AVPlayerOnInfoCallback()

```c
typedef void (*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)
```

**Description**

Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo** function will not be invoked.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance.| 
| [AVPlayerOnInfoType](#avplayeroninfotype) type | Message type. For details, see [AVPlayerOnInfoType](#avplayeroninfotype).| 
| [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md)* infoBody | Pointer to the message. The pointer is valid only in this callback.| 
| void *userData | Pointer to the user data passed in. The same data is returned.|

### OH_AVPlayerOnError()

```c
typedef void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)
```

**Description**

Called when an error occurs in the AVPlayer. This type is available in API version 9 or later. If **OH_AVPlayerOnErrorCallback** is successfully set, this function will not be called.

> NOTE
>
> This API is supported since API version 11 and deprecated since API version 12. You are advised to use [OH_AVPlayerOnErrorCallback](#oh_avplayeronerrorcallback) instead.

**Deprecated from**: 12

**Substitute**: [OH_AVPlayerOnErrorCallback](#oh_avplayeronerrorcallback)

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance.|  
| int32_t errorCode | Error code.<br>**AV_ERR_NO_MEMORY**: No memory. The value is **1**. Possible cause: The system memory is insufficient. Solution: Release unnecessary resources and try again.<br>**AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The value is **2**. Possible causes: The operation is not allowed in the current state. Solution: Check the current state and perform the operation in a proper state.<br>**AV_ERR_INVALID_VAL**: Invalid value. The value is **3**. Possible causes: The input parameter value is invalid. Solution: Check whether the parameter value is within the valid range.<br>**AV_ERR_IO**: I/O error. The value is **4**. Possible causes: The file fails to be read or written, or the network I/O is abnormal. Solution: Check whether the file exists or whether the Internet connection is normal.<br>**AV_ERR_TIMEOUT**: Timeout. The value is **5**. Possible causes: The operation times out. Solution: Check the network status or increase the timeout interval.<br>**AV_ERR_UNKNOWN**: Unknown error. The value is **6**. Possible causes: An unknown error occurred. Solution: View logs or contact technical support.<br>**AV_ERR_SERVICE_DIED**: The service is dead. The value is **7**. Possible causes: The media service is terminated unexpectedly. Solution: Create a player instance again.<br>**AV_ERR_INVALID_STATE**: The operation is not supported in the current state. The value is **8**. Possible causes: The method is called in an incorrect state. Solution: Check whether the current player state supports the operation.<br>**AV_ERR_UNSUPPORT**: The function is not supported. The value is **9**. Possible causes: An unsupported API is called. Solution: Check the API version.<br>**AV_ERR_EXTEND_START**: Initial value for extended error codes. The value is **100**. Possible causes: An extension error occurred. Solution: Rectify the fault based on the specific error code.|
| const char \*errorMsg | Pointer to the error message. This parameter specifies the error description returned by the AVPlayer. The content depends on the error type and may be null or an empty string.|

### OH_AVPlayerOnErrorCallback()

```c
typedef void (*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)
```

**Description**

Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError** function will not be invoked.

**Since**: 12

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance.| 
| int32_t errorCode | Error code.<br>**AV_ERR_NO_MEMORY**: No memory. The value is **1**. Possible cause: The system memory is insufficient. Solution: Release unnecessary resources and try again.<br>**AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The value is **2**. Possible causes: The operation is not allowed in the current state. Solution: Check the current state and perform the operation in a proper state.<br>**AV_ERR_INVALID_VAL**: Invalid value. The value is **3**. Possible causes: The input parameter value is invalid. Solution: Check whether the parameter value is within the valid range.<br>**AV_ERR_IO**: I/O error. For API versions 12 and 13, the value is **4**. Starting from API version 14, it corresponds to more specific error codes ranging from 5411001 to 5411011. Possible causes: The file fails to be read or written, or the network I/O is abnormal. Solution: Check whether the file exists or whether the Internet connection is normal.<br>**AV_ERR_TIMEOUT**: Timeout. The value is **5**. Possible causes: The operation times out. Solution: Check the network status or increase the timeout interval.<br>**AV_ERR_UNKNOWN**: Unknown error. The value is **6**. Possible causes: An unknown error occurred. Solution: View logs or contact technical support.<br>**AV_ERR_SERVICE_DIED**: The service is dead. The value is **7**. Possible causes: The media service is terminated unexpectedly. Solution: Create a player instance again.<br>**AV_ERR_INVALID_STATE**: The operation is not supported in the current state. The value is **8**. Possible causes: The method is called in an incorrect state. Solution: Check whether the current player state supports the operation.<br>**AV_ERR_UNSUPPORT**: The function is not supported. The value is **9**. Possible causes: An unsupported API is called. Solution: Check the API version.<br>**AV_ERR_EXTEND_START**: Initial value for extended error codes. The value is **100**. Possible causes: An extension error occurred. Solution: Rectify the fault based on the specific error code.|
| const char \*errorMsg | Pointer to the error message.| 
| void \*userData | Pointer to the user data passed in. The same data is returned.|

### OH_AVPlayerOnAmplitudeUpdateCallback()

```c
typedef void (*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)
```

**Description**

Called when the maximum audio amplitude is calculated.

**Use scenarios**

In audio player apps, this callback is used to implement audio visualization (such as volume waveform display), audio recording listening, and audio level indicators.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to an OH_AVPlayer instance.|
| double \*amplitudes | Pointer to the array of maximum audio amplitudes. Note: The maximum audio amplitude array is automatically released after the callback. If necessary, you need to copy the data for future use.|
| uint32_t size | Size of the maximum audio amplitude array.|
| void \*userData | Pointer to user-defined data.|

### OH_AVPlayerOnSeiMessageReceivedCallback()

```c
typedef void (*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)
```

**Description**

Called for obtaining SEI messages. You need to call **OH_AVPlayer_EnableSeiMessageReporting** to subscribe to SEI message events. After the subscription, the callback returns detailed SEI information, including the payload type and payload content. It is used to obtain supplementary and enhanced information such as subtitles, time codes, and metadata from camera streams.

**Use scenarios**

In video playback apps, it is used to obtain supplementary and enhanced information embedded in camera streams, such as subtitle data, time codes, and metadata. It is commonly used for time synchronization and video data analysis in live streaming scenarios.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance.|
| OH_AVSeiMessageArray \*message | SEI message array. Note: The SEI message array is automatically released after the callback. If necessary, you need to copy the data for future use.|
| int32_t playbackPosition | Playback position, in ms.|
| void \*userData | Pointer to user-defined data.|

### OH_AVPlayerPCMOutputCallback()

```c
typedef void (*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

If this callback is successfully set, the audio PCM data output will be obtained. The PCM data is the original audio data, and the format (of the sampling rate, number of audio channels, and bit depth) is the same as that of the media source. The callback is triggered after audio decoding. The data is valid only during the callback and needs to be processed or copied in a timely manner. This function applies to scenarios such as audio analysis and special effect processing.

**Use scenarios**

In audio processing apps, this callback is used to implement audio data analysis, audio special effect processing, audio recording and transcoding, and real-time audio visualization.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to an OH_AVPlayer instance.|
| OH_AVBuffer \*pcmBuffer | Audio PCM data. The audio PCM data is valid only during this callback and is released by the player after the callback.|
| void \*userData | Pointer to user data.|

### OH_AVPlayerPCMProcessorCallback()

```c
typedef void (*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

If this callback is successfully set, AVPlayer needs to use the processed data for audio playback, and the processing must be completed before the callback is returned. Otherwise, the playback will be blocked.<br> Do not change the sampling rate, number of audio channels, or sampling format when using this method to avoid failure to obtain data.

**Since**: 26.0.0

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to an OH_AVPlayer instance.|
| OH_AVBuffer \*pcmBuffer | Audio PCM data. The audio PCM data is valid only during this callback and is released by the player after the callback.|
| void \*userData | Pointer to user data.|
