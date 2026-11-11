# avplayer_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chennotfound-->
<!--Designer: @chennotfound-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=2d56846da3109c6542705ceefa4aed0cf271c3b1 translatedAt=2026-11-10T08:40:38.482Z pushedAt=2026-11-10T10:44:36.506Z nl=1 -->

## Overview

The file declares the structs and enums of the AVPlayer.

**File to include**: <multimedia/player_framework/avplayer_base.h>

**Library**: libavplayer.so

**System capability:** SystemCapability.Multimedia.Media.AVPlayer 

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) | AVPlayerCallback | Defines a collection of the [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo) and [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror) callback function pointers. The application needs to register this struct with the OH_AVPlayer instance and process the information reported by the callbacks to ensure the normal running of AVPlayer. |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) | OH_AVPlayer | Defines an initialized AVPlayer.|
| [OH_AVSeiMessageArray](./capi-avplayer-oh-avseimessagearray.md) | OH_AVSeiMessageArray | Defines the SEI message array.|
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) | OH_AVPlaybackStrategy | Defines the audio and video playback strategy.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVPlayerState](#avplayerstate) | AVPlayerState | Enumerates the AVPlayer states.|
| [AVPlayerSeekMode](#avplayerseekmode) | AVPlayerSeekMode | Enumerates the seek modes.|
| [AVPlaybackSpeed](#avplaybackspeed) | AVPlaybackSpeed | Enumerates the playback speeds of the AVPlayer.|
| [AVPlayerOnInfoType](#avplayeroninfotype) | AVPlayerOnInfoType | Enumerates the OnInfo types.<br> It can be used in OH_AVPlayerOnInfoCallback and OH_AVPlayerOnInfo (deprecated) to indicate the type of player information received.<br> Since API version 12, users are recommended to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback). Different OnInfo types provide different information (infoBody), which contains a key-value relationship table. For details, see the enum value table below.<br> For developers targeting API version 11, the old API needs to be used. For the corresponding relationship used in the deprecated API OH_AVPlayerOnInfo, see the API description of [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo). |
| [AVPlayerBufferingType](#avplayerbufferingtype) | AVPlayerBufferingType | Enumerates the types of buffer messages of the AVPlayer.|
| [AVPlayerTrackSwitchMode](#avplayertrackswitchmode) | AVPlayerTrackSwitchMode | Enumerates the track switching modes.|
| [OH_VideoOutputResult](#oh_videooutputresult) | OH_VideoOutputResult | Enumerates the video output results.|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)](#oh_avplayeroninfo) | OH_AVPlayerOnInfo | Called when a player message is received.<br>Deprecated since API version 12. |
| [typedef void (\*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)](#oh_avplayeroninfocallback) | OH_AVPlayerOnInfoCallback | Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo** function will not be invoked.|
| [typedef void (\*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)](#oh_avplayeronerror) | OH_AVPlayerOnError | Called when an error occurs in API version 9 or later.<br>Deprecated since API version 12. |
| [typedef void (\*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avplayeronerrorcallback) | OH_AVPlayerOnErrorCallback | Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError** function will not be invoked.|
| [typedef void (\*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)](#oh_avplayeronamplitudeupdatecallback) | OH_AVPlayerOnAmplitudeUpdateCallback | Called when the maximum audio amplitude is calculated.|
| [typedef void (\*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)](#oh_avplayeronseimessagereceivedcallback) | OH_AVPlayerOnSeiMessageReceivedCallback | Called for obtaining SEI messages. This function is used to subscribe to SEI message events and returns detailed SEI information.|
| [typedef void (\*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmoutputcallback) | OH_AVPlayerPCMOutputCallback | Called to obtain audio PCM data output. |
| [typedef void (\*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmprocessorcallback) | OH_AVPlayerPCMProcessorCallback | Called to obtain audio PCM data for post-processing. AVPlayer needs to use the processed data for audio playback, and the processing must be completed in a timely manner; otherwise, playback will be blocked.<br> Do not change the sample rate, number of channels, or sample format while using this method to avoid exceptions in data acquisition. |

### Variables

| Name| Description|
| -- | -- |
| const char * OH_PLAYER_STATE | Keyword for obtaining the playback state. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_STATE_CHANGE_REASON | Keyword for obtaining the reason for the playback state change. The corresponding value type is int32_t.<br> 1: triggered by a user operation; 2: triggered by a system change.<br>**Since:** 12 |
| const char * OH_PLAYER_VOLUME | Keyword for obtaining the volume. The corresponding value type is float, with a value range of [0.0, 1.0].<br>**Since:** 12 |
| const char * OH_PLAYER_BITRATE_ARRAY | Keyword for obtaining the bitrate list. The corresponding value type is a uint8_t byte array. When obtaining information through this keyword:<br> First, use a uint8_t pointer variable to store the bitrate list, and use a size_t variable to store the length of the byte array.<br> Then, allocate several uint32_t storage spaces to receive the bitrate integer values converted from the uint8_t byte array.<br>**Since:** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_TYPE | Keyword for obtaining the audio interruption type. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_FORCE | Keyword for obtaining the FORCE type of audio interruption. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_HINT | Keyword for obtaining the HINT type of audio interruption. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON | Keyword for obtaining the reason for the audio device change. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_BUFFERING_TYPE | Keyword for obtaining the buffering update message type. The corresponding value type is [AVPlayerBufferingType](#avplayerbufferingtype).<br> When obtaining information through this keyword, first use an int32_t variable to store the result, and then convert it to the AVPlayerBufferingType type.<br>**Since:** 12 |
| const char * OH_PLAYER_BUFFERING_VALUE | Keyword for obtaining the buffering update message value. The corresponding value type is int32_t. See [AVPlayerBufferingType](#avplayerbufferingtype).<br> This keyword is valid when the buffering update message type is AVPLAYER_BUFFERING_PERCENT or AVPLAYER_BUFFERING_CACHED_DURATION.<br>**Since:** 12 |
| const char * OH_PLAYER_SEEK_POSITION | Keyword for obtaining the playback position after seeking. The corresponding value type is int32_t, in milliseconds (ms).<br>**Since:** 12 |
| const char * OH_PLAYER_PLAYBACK_SPEED | Keyword for obtaining the playback speed information. The corresponding value type is [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed).<br> When obtaining information through this keyword, first use an int32_t variable to store the result, and then convert it to the AVPlaybackSpeed type.<br>**Since:** 12 |
| const char * OH_PLAYER_PLAYBACK_RATE | Keyword for obtaining the effective playback rate. The corresponding value type is a floating-point number.<br>**Since:** 20 |
| const char * OH_PLAYER_BITRATE | Keyword for obtaining the bitrate information. The corresponding value type is uint32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_CURRENT_POSITION | Keyword for obtaining the playback position information. The corresponding value type is int32_t, in milliseconds.<br>**Since:** 12 |
| const char * OH_PLAYER_DURATION | Keyword for obtaining the duration information of the media resource. The corresponding value type is int64_t, in milliseconds.<br>**Since:** 12 |
| const char * OH_PLAYER_VIDEO_WIDTH | Keyword for obtaining the video width information. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_VIDEO_HEIGHT | Keyword for obtaining the video height information. The corresponding value type is int32_t.<br>**Since:** 12 |
| const char * OH_PLAYER_MESSAGE_TYPE | Keyword for obtaining the player message information. The corresponding value type is int32_t.<br> 1: the video frame starts rendering.<br>**Since:** 12 |
| const char * OH_PLAYER_IS_LIVE_STREAM | Keyword for obtaining the information about whether the media resource is a live stream. The corresponding value type is int32_t.<br> 1: live stream.<br>**Since:** 12 |
| const char * OH_PLAYER_MD_KEY_HAS_VIDEO | Pointer to the key for obtaining whether the media resource contains video tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains video tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_HAS_AUDIO | Pointer to the key for obtaining whether the media resource contains audio tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains audio tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_HAS_SUBTITLE | Pointer to the key for obtaining whether the media resource contains subtitle tracks. The value is of the int32_t type.<br> The value **1** means that the media resource contains subtitle tracks, and the value **0** means the opposite.<br>**Since**: 22|
| const char * OH_PLAYER_MD_KEY_TRACK_INDEX | Pointer to the key for obtaining the track index information of a media resource. The value is of the int32_t type.<br>**Since**: 22|
| const char * OH_PLAYER_SEI_PAYLOAD_TYPE | Pointer to the key for indicating the payload type in an SEI message.<br>**Since:** 23 |
| const char * OH_PLAYER_SEI_PAYLOAD_CONTENT | Pointer to the key for indicating the payload content in an SEI message.<br>**Since:** 23 |
| const char * OH_PLAYER_SUPER_RESOLUTION_ENABLE_STATE | Pointer to the key for indicating the enable state of the super resolution feature. The value type is int32_t. The value **1** indicates that the feature is enabled, and **0** indicates the opposite. It is used for information callback when the super resolution state changes.<br>**Since**: 23|
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX | Pointer to the key for indicating the track index in the track change information. The value type is int32_t.<br>**Since**: 23|
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED | Flag keyword in the track change information indicating whether the track is selected. The value type is int32_t. A value of 1 indicates selected, and 0 indicates not selected.<br>**Since:** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION | Keyword in the subtitle update information indicating the duration. The value type is int32_t, in milliseconds.<br>**Since:** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME | Keyword in the subtitle update information indicating the start time. The value type is int32_t, in milliseconds.<br>**Since:** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT | Pointer to the key for indicating the subtitle text content in the subtitle update information. The value type is string.<br>**Since**: 23|
| const char * OH_PLAYER_SERVER_IP_ADDRESS | Pointer to the key for indicating the server IP address in the playback information.<br>**Since**: 23|
| const char * OH_PLAYER_IS_DOWNLOADING | Keyword in the playback information indicating whether the current state is downloading. The value type is int32_t. A value of 1 indicates downloading, and 0 indicates not downloading.<br>**Since:** 23 |
| const char * OH_PLAYER_BUFFER_DURATION | Keyword in the playback information indicating the buffer duration. The value type is int32_t, in milliseconds.<br>**Since:** 23 |
| const char * OH_PLAYER_DOWNLOAD_RATE | Pointer to the key for indicating the current download rate in the playback information. The download rate unit is bit/s (bps).<br>**Since**: 23|
| const char * OH_PLAYER_AVG_DOWNLOAD_RATE | Pointer to the key for indicating the average download rate in the playback information. The download rate unit is bit/s (bps).<br>**Since**: 23|
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
| AV_SEEK_CONTINUOUS = 3 | Seek in continuous dragging mode. This mode provides a smoother dragging experience, but requires the device to support continuous seek on the current stream. Before calling continuous seek, check whether it is supported. See [OH_AVPlayer_IsSeekContinuousSupported](capi-avplayer-h.md#oh_avplayer_isseekcontinuoussupported).<br>**Since:** 23 |


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

OnInfo type.<br> It can be used in OH_AVPlayerOnInfoCallback and OH_AVPlayerOnInfo (deprecated) to indicate the type of player information received.<br> Since API version 12, you are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback). Different OnInfo types provide different information (infoBody). The infoBody contains a key-value relationship table. For details, see the enum value table below.<br> For developers using API version 11, the old API must be used. For the corresponding relationship used in the deprecated API OH_AVPlayerOnInfo, see the API description of [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).

**Since**: 11

| Enum Item| Description|
| -- | -- |
| AV_INFO_TYPE_SEEKDONE = 0 | Message returned when seeking to a playback position is complete.<br> If **key** is set to **OH_PLAYER_SEEK_POSITION**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_SPEEDDONE = 1 | Returns a message when the playback speed setting is complete.<br> The key is OH_PLAYER_PLAYBACK_SPEED, and the value type is [AVPlaybackSpeed](#avplaybackspeed). The system passes the value through int32_t. The application needs to obtain it through int32_t first and then cast it to [AVPlaybackSpeed](#avplaybackspeed). |
| AV_INFO_TYPE_BITRATEDONE = 2 | Message returned when the bit rate setting is complete.<br> If **key** is set to **OH_PLAYER_BITRATE**, the value type is uint32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value and forcibly converts the value to the uint32_t type.|
| AV_INFO_TYPE_EOS = 3 | Message returned when the playback is complete.|
| AV_INFO_TYPE_STATE_CHANGE = 4 | Returns a message when the state changes.<br> The key is OH_PLAYER_STATE, and the value type is int32_t. The system passes the value through int32_t. The application needs to obtain it through int32_t first and then cast it to [AVPlayerState](#avplayerstate).<br> The key is OH_PLAYER_STATE_CHANGE_REASON, and the value type is int32_t. The system passes the value through int32_t. The application needs to obtain it through int32_t. 1: triggered by a user operation; 2: triggered by a system change. |
| AV_INFO_TYPE_POSITION_UPDATE = 5 | Message returned when the playback position changes.<br> If **key** is set to **OH_PLAYER_CURRENT_POSITION**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_MESSAGE = 6 | Message returned when video rendering starts.<br> If **key** is set to **OH_PLAYER_MESSAGE_TYPE**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. The value **1** means that video rendering starts.|
| AV_INFO_TYPE_VOLUME_CHANGE = 7 | Message returned when the playback volume changes.<br> If **key** is set to **OH_PLAYER_VOLUME**, the value type is float. The system uses float to transfer the value, and the application uses float to obtain the value. The value range is [0.0, 1.0].|
| AV_INFO_TYPE_RESOLUTION_CHANGE = 8 | Message returned when the video size is obtained for the first time or the video size is updated.<br> If **key** is set to **OH_PLAYER_VIDEO_WIDTH** or **OH_PLAYER_VIDEO_HEIGHT**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_BUFFERING_UPDATE = 9 | Returns the buffering time of multiple queues.<br> The key is OH_PLAYER_BUFFERING_TYPE, and the value type is [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype). The system passes the value through int32_t. The application needs to obtain it through int32_t first and then cast it to [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype).<br> The key is OH_PLAYER_BUFFERING_VALUE, and the value type is int32_t. The system passes the value through int32_t. The application needs to obtain it through int32_t.<br> This is valid when the buffering update message type is AVPLAYER_BUFFERING_PERCENT or AVPLAYER_BUFFERING_CACHED_DURATION, indicating the buffering progress completion percentage and the playable duration of the buffered data, respectively. The unit is millisecond (ms). |
| AV_INFO_TYPE_BITRATE_COLLECT = 10 | Message returned to report the HLS video bit rates.<br> If **key** is set to **OH_PLAYER_BITRATE_ARRAY**, the value type is uint8_t. The application uses a pointer variable of the uint8_t type to store the bit rate list and uses a variable of the size_t type to store the byte array length. Then it allocates several storage spaces of the uint32_t type to receive the bit rate integer of the uint32_t type, which is converted from the uint8_t byte array.|
| AV_INFO_TYPE_INTERRUPT_EVENT = 11 | Message returned when the audio focus changes.<br> The value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.<br> **key** can be set to any of the following values:<br> **OH_PLAYER_AUDIO_INTERRUPT_TYPE**: The value **1** means that the audio interruption event starts, and **2** means that the event ends.<br> **OH_PLAYER_AUDIO_INTERRUPT_FORCE**: The value **0** means forcible interruption (the system changes the audio playback status), and **1** means sharing interruption (the application changes the audio playback status).<br> **OH_PLAYER_AUDIO_INTERRUPT_HINT**: The value **0** (NONE) means no hint; **1** (RESUME) means that the audio playback is resumed; **2** (PAUSE) means that the audio playback is paused and loses focus; **3** (STOP) means that the audio playback is stopped; **4** (DUCK) means that the audio volume is reduced; **5** (UNDUCK) means that the audio volume is restored.|
| AV_INFO_TYPE_DURATION_UPDATE = 12 | Message returned when the playback duration changes.<br> If **key** is set to **OH_PLAYER_DURATION**, the value type is int64_t. The system uses int64_t to transfer the value, and the application uses int64_t to obtain the value.|
| AV_INFO_TYPE_IS_LIVE_STREAM = 13 | Message returned when live streams are played. If **key** is set to **OH_PLAYER_IS_LIVE_STREAM**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. The value **0** means a non-live stream, and **1** means a live stream.|
| AV_INFO_TYPE_TRACKCHANGE = 14 | Returns a message when the track changes.<br> The key is OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX, and the value type is int32_t, indicating the track index after the switch.<br> The key is OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED, and the value type is int32_t. A value of 1 indicates that the track is selected, and 0 indicates that it is not selected. |
| AV_INFO_TYPE_TRACK_INFO_UPDATE = 15 | Returns a message when the track is updated.<br> The key is OH_PLAYER_MD_KEY_HAS_VIDEO, and the value type is int32_t. A value of 1 indicates that a video track is included, and 0 indicates that no video track is included.<br> The key is OH_PLAYER_MD_KEY_HAS_AUDIO, and the value type is int32_t. A value of 1 indicates that an audio track is included, and 0 indicates that no audio track is included.<br> The key is OH_PLAYER_MD_KEY_HAS_SUBTITLE, and the value type is int32_t. A value of 1 indicates that a subtitle track is included, and 0 indicates that no subtitle track is included.<br> The key is OH_PLAYER_MD_KEY_TRACK_INDEX, and the value type is int32_t, indicating the current track index. |
| AV_INFO_TYPE_SUBTITLE_UPDATE = 16 | Returns a message when the subtitle information is updated.<br> The key is OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION, and the value type is int32_t, indicating the subtitle duration in milliseconds.<br> The key is OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME, and the value type is int32_t, indicating the subtitle start time in milliseconds.<br> The key is OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT, and the value type is string, indicating the subtitle text content. |
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE = 17 | Message returned when the audio output device changes.<br> If **key** is set to **OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value.|
| AV_INFO_TYPE_PLAYBACK_RATE_DONE = 18 | Message returned when the playback rate is applied.<br> If **key** is set to **OH_PLAYER_PLAYBACK_RATE**, the value type is float. The system uses float to transfer the value, and the application uses float to obtain the value.<br>**Since**: 20|
| AV_INFO_TYPE_SUPER_RESOLUTION_CHANGED = 19 | Message returned when the super resolution changes.<br>**Since**: 23|

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
typedef void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)
```

**Description**

Called when the AVPlayer receives a message.

The correspondence between the info type (**type**) and the info (**extra**) is shown in the table. 

| type| Description of extra|
| -------- | -------- |
| AV_INFO_TYPE_SEEKDONE | Message returned when seeking to a playback position is complete. **extra** indicates the position after the seek operation.|
| AV_INFO_TYPE_SPEEDDONE | Message returned when the playback speed setting is complete. **extra** indicates the playback speed. For details, see [AVPlaybackSpeed](#avplaybackspeed).|
| AV_INFO_TYPE_BITRATEDONE | Message returned when the bit rate setting is complete. **extra** indicates the bit rate.|
| AV_INFO_TYPE_EOS | Message returned when the playback is complete.|
| AV_INFO_TYPE_STATE_CHANGE | Message returned when the AVPlayer state changes. **extra** indicates the new state. For details, see [AVPlayerState](#avplayerstate).|
| AV_INFO_TYPE_POSITION_UPDATE | Message returned when the playback position changes. **extra** indicates the current position.|
| AV_INFO_TYPE_MESSAGE | Message returned when video rendering starts. **extra** indicates the first video frame rendered.|
| AV_INFO_TYPE_VOLUME_CHANGE | Message returned when the playback volume changes. **extra** is not defined in this scenario.|
| AV_INFO_TYPE_RESOLUTION_CHANGE | Message returned when the video size is obtained for the first time or the video size is updated. **extra** is not defined in this scenario.|
| AV_INFO_TYPE_BUFFERING_UPDATE | Returns a buffering update message. In this scenario, extra indicates the buffering-related data. You are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) to obtain detailed buffering information. |
| AV_INFO_TYPE_BITRATE_COLLECT  | Message returned to report the HLS video bit rates. Each bit rate has been converted into a uint8_t byte array during the reporting. You need to forcibly convert the uint8_t byte array into a uint32_t integer array.  |
| AV_INFO_TYPE_INTERRUPT_EVENT | Message returned when the audio focus changes. **extra** indicates the hints provided along with audio interruption. For details, see [OH_AudioInterrupt_Hint](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_hint). The application can determine whether to perform further processing based on the hint.|
| AV_INFO_TYPE_DURATION_UPDATE | Message indicating the playback duration. **extra** indicates the video duration.|
| AV_INFO_TYPE_IS_LIVE_STREAM | Message returned when live streams are played. **extra** indicates whether the stream is a live stream. The value **0** means a non-live stream, and **1** means a live stream.|
| AV_INFO_TYPE_TRACKCHANGE | Message returned when the track changes. **extra** is not defined in this scenario.|
| AV_INFO_TYPE_TRACK_INFO_UPDATE | Returns a message when the track is updated. In this scenario, the extra parameter has no specific meaning. |
| AV_INFO_TYPE_SUBTITLE_UPDATE | Message returned when the subtitle information changes. **extra** is not defined in this scenario.|
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE | Message returned when the audio output device changes. **extra** indicates the device change reason. For details, see [OH_AudioStream_DeviceChangeReason](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason).|

**Since**: 11

**Deprecated from**: 12

**Substitute API:** [OH_AVPlayerOnInfoCallback()](#oh_avplayeroninfocallback)

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an OH_AVPlayer instance.|
| [AVPlayerOnInfoType](#avplayeroninfotype) type | Information type. The type is [AVPlayerOnInfoType](#avplayeroninfotype). For the correspondence between the type and extra, see the method description. |
| int32_t extra | Additional information, whose meaning is determined by the type parameter. Different information types correspond to different additional information. For details about the correspondence, see the table in the method description. For example, when type is AV_INFO_TYPE_SEEKDONE, extra indicates the playback position to seek to (in milliseconds); when type is AV_INFO_TYPE_POSITION_UPDATE, extra indicates the current playback position (in milliseconds). |

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance.|
| [AVPlayerOnInfoType](#avplayeroninfotype) type | Information type. For details, see [AVPlayerOnInfoType](#avplayeroninfotype). |
| [OH_AVFormat](../apis-avcodec-kit/capi-core-oh-avformat.md)* infoBody | Pointer to the message. The pointer is valid only in this callback.|
| void *userData | Returns the userData data passed in when the user sets the callback, without modification. |

### OH_AVPlayerOnError()

```c
typedef void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)
```

**Description**

Called when an error occurs in API version 9 or later.

**Since**: 11

**Deprecated from**: 12

**Substitute API:** [OH_AVPlayerOnErrorCallback()](#oh_avplayeronerrorcallback)

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance.|
| int32_t errorCode | Error code.<br>                  **AV_ERR_NO_MEMORY**: No memory. The value is **1**.<br>                  **AV_ERR_OPERATE_NOT_PERMIT**: The operation is not allowed. The value is **2**.<br>                  **AV_ERR_INVALID_VAL**: Invalid value. The value is **3**.<br>                  **AV_ERR_IO**: I/O error. The value is **4**.<br>                  **AV_ERR_TIMEOUT**: Timeout. The value is **5**.<br>                  **AV_ERR_UNKNOWN**: Unknown error. The value is **6**.<br>                  **AV_ERR_SERVICE_DIED**: The service is dead. The value is **7**.<br>                  **AV_ERR_INVALID_STATE**: The operation is not supported in the current state. The value is **8**.<br>                  **AV_ERR_UNSUPPORT**: The function is not supported. The value is **9**.<br>                  **AV_ERR_EXTEND_START**: Initial value for extended error codes. The value is **100**.|
| const char \*errorMsg | Pointer to the error message.|

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
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | Pointer to an **OH_AVPlayer** instance.|
| int32_t errorCode | Result code.<br>AV_ERR_NO_MEMORY: no memory. The value is 1. Possible cause: insufficient system memory. Handling: release unnecessary resources and retry.<br>AV_ERR_OPERATE_NOT_PERMIT: operation not permitted. The value is 2. Possible cause: the operation is not allowed in the current state. Handling: check the current state and perform the operation in an appropriate state.<br>AV_ERR_INVALID_VAL: invalid value. The value is 3. Possible cause: the input parameter value is invalid. Handling: check whether the parameter value is within the valid range.<br>AV_ERR_IO: I/O error. The value is 4 in API version 12-13; in API version 14 and later, the corresponding error is refined into error codes 5411001 to 5411011. Possible cause: file read/write failure or network I/O exception. Handling: check whether the file exists or whether the network connection is normal.<br>AV_ERR_TIMEOUT: timeout error. The value is 5. Possible cause: the operation timed out. Handling: check the network condition or increase the timeout period.<br>AV_ERR_UNKNOWN: unknown error. The value is 6. Possible cause: an unknown error occurred. Handling: check the logs or contact technical support.<br>AV_ERR_SERVICE_DIED: service died. The value is 7. Possible cause: the media service terminated abnormally. Handling: recreate the player instance.<br>AV_ERR_INVALID_STATE: the current state does not support this operation. The value is 8. Possible cause: the method is called in an incorrect state. Handling: check whether the current state of the player supports the operation.<br>AV_ERR_UNSUPPORT: unsupported API. The value is 9. Possible cause: an unsupported API is called. Handling: check the API version support.<br>AV_ERR_EXTEND_START: initial value of the extended error code. The value is 100. Possible cause: extended error. Handling: handle the error based on the specific error code. |
| const char \*errorMsg | Pointer to the error message.|
| void \*userData | Pointer to the user data passed in by the user when setting the callback.|

### OH_AVPlayerOnAmplitudeUpdateCallback()

```c
typedef void (*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)
```

**Description**

Called when the maximum audio amplitude is calculated.

**Use scenarios**

In audio player applications, it is used to implement audio visualization effects (such as volume waveform display), audio recording monitoring, audio level indicators, and other scenarios.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to the OH_AVPlayer instance. |
| double \*amplitudes | Pointer to the array of maximum audio amplitudes. Note: The maximum audio amplitude array is automatically released after the callback. If necessary, you need to copy the data for future use.|
| uint32_t size | Size of the maximum audio amplitude array.|
| void \*userData | Pointer to user-defined data.|

### OH_AVPlayerOnSeiMessageReceivedCallback()

```c
typedef void (*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)
```

**Description**

Called for obtaining SEI messages. This function is used to subscribe to SEI message events and returns detailed SEI information.

**Use scenarios**

In video playback applications, it is used to obtain supplemental enhancement information embedded in the video stream, such as subtitle data, timecodes, and metadata. It is commonly used for time synchronization and video data analysis in live streaming scenarios.

**Since**: 23

**Parameters**

| Parameter| Description|
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance.|
| OH_AVSeiMessageArray \*message | SEI message array. Note: The SEI message array is automatically released after the callback. If necessary, you need to copy the data for future use.|
| int32_t playbackPosition | Playback position, in milliseconds. |
| void \*userData | Pointer to user-defined data.|

### OH_AVPlayerPCMOutputCallback()

```c
typedef void (*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

Called to obtain audio PCM data output.

**Use scenarios**

In audio processing applications, it is used to implement audio data analysis, audio effect processing, audio recording transcoding, real-time audio visualization, and other scenarios.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to an **OH_AVPlayer** instance. |
| OH_AVBuffer \*pcmBuffer | Pointer to audio PCM data. The audio PCM data is valid only during this callback and is released by the player after the callback returns. |
| void \*userData | Pointer to user data. |

### OH_AVPlayerPCMProcessorCallback()

```c
typedef void (*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

Called to obtain audio PCM data for post-processing. AVPlayer needs to use the processed data for audio playback, and the processing must be completed in a timely manner; otherwise, playback will be blocked.<br> During the use of this method, do not change the sample rate, number of channels, or sample format to avoid exceptions in data acquisition.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) \*player | Pointer to an OH_AVPlayer instance. |
| OH_AVBuffer \*pcmBuffer | Pointer to audio PCM data. The audio PCM data is valid only during this callback and is released by the player after the callback returns. |
| void \*userData | Pointer to user data. |