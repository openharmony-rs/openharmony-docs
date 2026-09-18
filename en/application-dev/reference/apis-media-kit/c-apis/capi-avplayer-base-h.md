# avplayer_base.h

## Overview

The file declares the structs and enums of the AVPlayer.

**Library**: libavplayer.so

**Since**: 11

**Related module**: [AVPlayer](capi-avplayer.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) | AVPlayerCallback | The struct contains the set of the **OH_AVPlayerOnInfo** and **OH_AVPlayerOnError** callback function pointers. To ensure the normal running of OH_AVPlayer, you must register the instance of this struct with the OH_AVPlayer instance and process the information reported by the callback functions. |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) | OH_AVSeiMessageArray | Defines a struct for the SEI message array. |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) | OH_AVPlaybackStrategy | Defines a struct for the audio and video playback strategy. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVPlayerState](#avplayerstate) | AVPlayerState | Enumerates the AVPlayer states. |
| [AVPlayerSeekMode](#avplayerseekmode) | AVPlayerSeekMode | Enumerates the seek modes. |
| [AVPlaybackSpeed](#avplaybackspeed) | AVPlaybackSpeed | Enumerates the playback speeds of the AVPlayer. |
| [AVPlayerOnInfoType](#avplayeroninfotype) | AVPlayerOnInfoType | Enumerates the types of messages received by the AVPlayer. The enum can be used in **OH_AVPlayerOnInfoCallback** and **OH_AVPlayerOnInfo** (deprecated) to indicate the type of information received by the AVPlayer. Starting from API version 12, you are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) instead. Different information (**infoBody**) can be obtained for different **OnInfo** types. **infoBody** contains the key-value pairs. For details, see the following enumerated value table. If you are using API version 11 for development, use **OH_AVPlayerOnInfo (deprecated)**. For details about the mappings used in this deprecated API, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo). |
| [AVPlayerBufferingType](#avplayerbufferingtype) | AVPlayerBufferingType | Enumerates the types of buffer messages of the AVPlayer. |
| [AVPlayerTrackSwitchMode](#avplayertrackswitchmode) | AVPlayerTrackSwitchMode | Enumerates the track switching modes. |
| [OH_VideoOutputResult](#oh_videooutputresult) | OH_VideoOutputResult | Result of Video output. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)](#oh_avplayeroninfo) | OH_AVPlayerOnInfo | Called when the AVPlayer receives a message.(Deprecated in API12) |
| [typedef void (\*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)](#oh_avplayeroninfocallback) | OH_AVPlayerOnInfoCallback | Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo**<br>function will not be invoked. |
| [typedef void (\*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)](#oh_avplayeronerror) | OH_AVPlayerOnError | Called when an error occurs in the AVPlayer. This callback is available in API version 9 or later.(Deprecated in API12) |
| [typedef void (\*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avplayeronerrorcallback) | OH_AVPlayerOnErrorCallback | Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError**<br>function will not be invoked. |
| [typedef void (\*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)](#oh_avplayeronamplitudeupdatecallback) | OH_AVPlayerOnAmplitudeUpdateCallback | Called when the maximum audio amplitude is calculated. |
| [typedef void (\*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)](#oh_avplayeronseimessagereceivedcallback) | OH_AVPlayerOnSeiMessageReceivedCallback | Called for obtaining SEI messages. This function is used to subscribe to SEI message events and returns detailed SEI information. |
| [typedef void (\*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmoutputcallback) | OH_AVPlayerPCMOutputCallback | Describes the handle used to obtain the decoded audio PCM data. |
| [typedef void (\*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)](#oh_avplayerpcmprocessorcallback) | OH_AVPlayerPCMProcessorCallback | This callback provides a PCM buffer for processing. AVPlayer needs to use the processed data for audio playback, and processing must be completed in a timely manner, otherwise it will block playback. Do not change sampling rate, channels, or sampling format. |

### Variable

| Name | Description |
| -- | -- |
| const char *OH_PLAYER_STATE | Pointer to the key for obtaining the AVPlayer state. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_STATE_CHANGE_REASON | Pointer to the key for obtaining the AVPlayer state change reason. The value is of the int32_t type. The value **1** means that the change is triggered by user operations, and **2** means that the change is triggered by the system.<br>**Since**: 12 |
| const char *OH_PLAYER_VOLUME | Pointer to the key for obtaining the volume. The value type is float.<br>**Since**: 12 |
| const char *OH_PLAYER_BITRATE_ARRAY | Pointer to the key for obtaining the bit rate array. The value is of the uint8_t byte array type. When this key is used to obtain information, you need to: Use a pointer variable of the uint8_t type to store the bit rate list and use a variable of the size_t type to store the byte array length. Then it allocates several storage spaces of the uint32_t type to receive the bit rate integer of the uint32_t type, which is converted from the uint8_t byte array.<br>**Since**: 12 |
| const char *OH_PLAYER_AUDIO_INTERRUPT_TYPE | Pointer to the key for obtaining the audio interruption type. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_AUDIO_INTERRUPT_FORCE | Pointer to the key for obtaining the FORCE type of audio interruption. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_AUDIO_INTERRUPT_HINT | Pointer to the key for obtaining the HINT type of audio interruption. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON | Pointer to the key for obtaining the audio device change reason. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_BUFFERING_TYPE | Pointer to the key for obtaining the type of the buffer update message. The value type is [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype). When this key is used to obtain information, you must use a variable of the int32_t type to save the result and then convert the result to a value of AVPlayerBufferingType.<br>**Since**: 12 |
| const char *OH_PLAYER_BUFFERING_VALUE | Pointer to the key for obtaining the value of the buffer update message. The value is of the int32_t type. For details, see [AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype). This parameter is valid only when the buffer update message type is **AVPLAYER_BUFFERING_PERCENT** or **<br>AVPLAYER_BUFFERING_CACHED_DURATION**.<br>**Since**: 12 |
| const char *OH_PLAYER_SEEK_POSITION | Pointer to the key for obtaining the playback progress after the seek operation. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_PLAYBACK_SPEED | Pointer to the key for obtaining the playback speed. The value type is [AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed). When this key is used to obtain information, you must use a variable of the int32_t type to save the result and then convert the result to a value of AVPlaybackSpeed.<br>**Since**: 12 |
| const char *OH_PLAYER_BITRATE | Pointer to the key for obtaining the bit rate array. The value is of the uint8_t byte array type. When this key is used to obtain information, you need to: Use a pointer variable of the uint8_t type to store the bit rate list and use a variable of the size_t type to store the byte array length. Then it allocates several storage spaces of the uint32_t type to receive the bit rate integer of the uint32_t type, which is converted from the uint8_t byte array.<br>**Since**: 12 |
| const char *OH_PLAYER_CURRENT_POSITION | Pointer to the key for obtaining the playback progress information. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_DURATION | Pointer to the key for obtaining the media asset duration. The value type is int64_t.<br>**Since**: 12 |
| const char *OH_PLAYER_VIDEO_WIDTH | Pointer to the key for obtaining the video width. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_VIDEO_HEIGHT | Pointer to the key for obtaining the video height. The value is of the int32_t type.<br>**Since**: 12 |
| const char *OH_PLAYER_MESSAGE_TYPE | Pointer to the key for obtaining the type of message received by the AVPlayer. The value is of the int32_t type. The value **1** means that the video frame starts to be rendered.<br>**Since**: 12 |
| const char *OH_PLAYER_IS_LIVE_STREAM | Pointer to the key for checking whether a media asset is live streaming. The value is of the int32_t type. The value **1** means live streaming.<br>**Since**: 12 |
| const char *OH_PLAYER_SEI_PAYLOAD_TYPE |  |
| const char *OH_PLAYER_SEI_PAYLOAD_CONTENT |  |
| const char *OH_PLAYER_SUPER_RESOLUTION_ENABLE_STATE | Pointer to the key for indicating the enable state of the super resolution feature. The value type is int32_t. The value **1** indicates that the feature is enabled, and **0** indicates the opposite. It is used for information callback when the super resolution state changes.<br>**Since**: 23 |
| const char *OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX | Pointer to the key for indicating the track index in the track change information. The value type is int32_t.<br>**Since**: 23 |
| const char *OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED | Pointer to the key for indicating whether the track is selected in the track change information. The value type is int32_t.<br>**Since**: 23 |
| const char *OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION | Pointer to the key for indicating the duration in the subtitle update information. The value type is int32_t.<br>**Since**: 23 |
| const char *OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME | Pointer to the key for indicating the start time in the subtitle update information. The value type is int32_t.<br>**Since**: 23 |
| const char *OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT | Pointer to the key for indicating the subtitle text content in the subtitle update information. The value type is string.<br>**Since**: 23 |
| const char *OH_PLAYER_PLAYBACK_RATE | Pointer to the key for obtaining the playback rate. The value is a floating-point number.<br>**Since**: 20 |
| const char *OH_PLAYER_MD_KEY_HAS_VIDEO | Pointer to the key for obtaining whether the media resource contains video tracks. The value is of the int32_t type. The value **1** means that the media resource contains video tracks, and the value **0** means the opposite.<br>**Since**: 22 |
| const char *OH_PLAYER_MD_KEY_HAS_AUDIO | Pointer to the key for obtaining whether the media resource contains audio tracks. The value is of the int32_t type. The value **1** means that the media resource contains audio tracks, and the value **0** means the opposite.<br>**Since**: 22 |
| const char *OH_PLAYER_MD_KEY_HAS_SUBTITLE | Pointer to the key for obtaining whether the media resource contains subtitle tracks. The value is of the int32_t type. The value **1** means that the media resource contains subtitle tracks, and the value **0** means the opposite.<br>**Since**: 22 |
| const char *OH_PLAYER_MD_KEY_TRACK_INDEX | Pointer to the key for obtaining the track index information of a media resource. The value is of the int32_t type.<br>**Since**: 22 |
| const char *OH_MEDIA_EVENT_INFO_PREPARE_DURATION | Pointer to the key for obtaining the preparation duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_RESOURCE_CONNECTION_DURATION | Pointer to the key for obtaining the resource connection duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_FIRST_FRAME_DECAPSULATION_DURATION | Pointer to the key for obtaining the first-frame decapsulation duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_TOTAL_PLAYING_TIME | Pointer to the key for obtaining the total playback duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_DOWNLOAD_REQUEST_COUNT | Pointer to the key for obtaining the total number of media resource loading requests in the statistic metric information. The value type is uint32_t.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_TIME | Pointer to the key for obtaining the total media resource loading duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_SIZE | Pointer to the key for obtaining the total size of loaded media resources in the statistic metric information. The value type is int64_t.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_STALLING_COUNT | Pointer to the key for obtaining the total number of stalling times in the statistic metric information. The value type is uint32_t.<br>**Since**: 23 |
| const char *OH_MEDIA_EVENT_INFO_TOTAL_STALLING_TIME | Pointer to the key for obtaining the total stalling duration in the statistic metric information. The value type is uint32_t, and the unit is millisecond.<br>**Since**: 23 |
| const char *OH_PLAYER_SERVER_IP_ADDRESS |  |
| const char *OH_PLAYER_IS_DOWNLOADING |  |
| const char *OH_PLAYER_BUFFER_DURATION |  |
| const char *OH_PLAYER_DOWNLOAD_RATE |  |
| const char *OH_PLAYER_AVG_DOWNLOAD_RATE |  |
| void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra) | Called when the AVPlayer receives a message.<br>**Since**: 11<br>**Deprecated**: 12<br>**Replaced by**: [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) |
| void (*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData) | Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo**<br>function will not be invoked.<br>**Since**: 12 |
| void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg) | Called when an error occurs in the AVPlayer. This callback is available in API version 9 or later.<br>**Since**: 11<br>**Deprecated**: 12<br>**Replaced by**: [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback) |
| void (*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData) | Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError**<br>function will not be invoked.<br>**Since**: 12 |
| void (*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData) | Called when the maximum audio amplitude is calculated.<br>**Since**: 23 |
| void (*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData) | Called for obtaining SEI messages. This function is used to subscribe to SEI message events and returns detailed SEI information.<br>**Since**: 23 |
| void (*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData) | Describes the handle used to obtain the decoded audio PCM data.<br>**Since**: 26.0.0 |
| void (*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData) | This callback provides a PCM buffer for processing. AVPlayer needs to use the processed data for audio playback, and processing must be completed in a timely manner, otherwise it will block playback. Do not change sampling rate, channels, or sampling format.<br>**Since**: 26.0.0 |

## Enum type description

### AVPlayerState

```c
enum AVPlayerState
```

**Description**

Enumerates the AVPlayer states.

**Since**: 11

| Enum item | Description |
| -- | -- |
| AV_IDLE = 0 | idle states |
| AV_INITIALIZED = 1 | initialized states |
| AV_PREPARED = 2 | prepared states |
| AV_PLAYING = 3 | playing states |
| AV_PAUSED = 4 | paused states |
| AV_STOPPED = 5 | stopped states |
| AV_COMPLETED = 6 | Play to the end states |
| AV_RELEASED = 7 | released states |
| AV_ERROR = 8 | error states |

### AVPlayerSeekMode

```c
enum AVPlayerSeekMode
```

**Description**

Enumerates the seek modes.

**Since**: 11

| Enum item | Description |
| -- | -- |
| AV_SEEK_NEXT_SYNC = 0 | sync to keyframes after the time point. |
| AV_SEEK_PREVIOUS_SYNC | sync to keyframes before the time point. |
| AV_SEEK_CLOSEST = 2 | Seeks to the frame closest to the specified position.<br>**Since**: 12 |
| AV_SEEK_CONTINUOUS = 3 |  |

### AVPlaybackSpeed

```c
enum AVPlaybackSpeed
```

**Description**

Enumerates the playback speeds of the AVPlayer.

**Since**: 11

| Enum item | Description |
| -- | -- |
| AV_SPEED_FORWARD_0_75_X | Video playback at 0.75x normal speed |
| AV_SPEED_FORWARD_1_00_X | Video playback at normal speed |
| AV_SPEED_FORWARD_1_25_X | Video playback at 1.25x normal speed |
| AV_SPEED_FORWARD_1_75_X | Video playback at 1.75x normal speed |
| AV_SPEED_FORWARD_2_00_X | Video playback at 2.0x normal speed |
| AV_SPEED_FORWARD_0_50_X | Plays the video at 0.5 times the normal speed.<br>**Since**: 12 |
| AV_SPEED_FORWARD_1_50_X | Plays the video at 1.5 times the normal speed.<br>**Since**: 12 |
| AV_SPEED_FORWARD_3_00_X | Plays the video at 3.0 times the normal speed.<br>**Since**: 13 |
| AV_SPEED_FORWARD_0_25_X | Plays the video at 0.25 times the normal speed.<br>**Since**: 13 |
| AV_SPEED_FORWARD_0_125_X | Plays the video at 0.125 times the normal speed.<br>**Since**: 13 |

### AVPlayerOnInfoType

```c
enum AVPlayerOnInfoType
```

**Description**

Enumerates the types of messages received by the AVPlayer. The enum can be used in **OH_AVPlayerOnInfoCallback** and **OH_AVPlayerOnInfo** (deprecated) to indicate the type of information received by the AVPlayer. Starting from API version 12, you are advised to use [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) instead. Different information (**infoBody**) can be obtained for different **OnInfo** types. **infoBody** contains the key-value pairs. For details, see the following enumerated value table. If you are using API version 11 for development, use **OH_AVPlayerOnInfo (deprecated)**. For details about the mappings used in this deprecated API, see [OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo).

**Since**: 11

| Enum item | Description |
| -- | -- |
| AV_INFO_TYPE_SEEKDONE = 0 | return the message when seeking done. |
| AV_INFO_TYPE_SPEEDDONE = 1 | return the message when speeding done. |
| AV_INFO_TYPE_BITRATEDONE = 2 | return the message when select bitrate done |
| AV_INFO_TYPE_EOS = 3 | return the message when playback is end of steam. |
| AV_INFO_TYPE_STATE_CHANGE = 4 | return the message when PlayerStates changed. |
| AV_INFO_TYPE_POSITION_UPDATE = 5 | return the current posion of playback automatically. |
| AV_INFO_TYPE_MESSAGE = 6 | return the playback message. |
| AV_INFO_TYPE_VOLUME_CHANGE = 7 | return the message when volume changed. |
| AV_INFO_TYPE_RESOLUTION_CHANGE = 8 | return the message when video size is first known or updated. |
| AV_INFO_TYPE_BUFFERING_UPDATE = 9 | return multiqueue buffering time. |
| AV_INFO_TYPE_BITRATE_COLLECT = 10 | return hls bitrate. Bitrate is to convert data into uint8_t array storage, |
| AV_INFO_TYPE_INTERRUPT_EVENT = 11 | return the message when audio focus changed. |
| AV_INFO_TYPE_DURATION_UPDATE = 12 | return the duration of playback. |
| AV_INFO_TYPE_IS_LIVE_STREAM = 13 | return the playback is live stream. |
| AV_INFO_TYPE_TRACKCHANGE = 14 | return the message when track changes. |
| AV_INFO_TYPE_TRACK_INFO_UPDATE = 15 | return the message when subtitle track info updated. |
| AV_INFO_TYPE_SUBTITLE_UPDATE = 16 | return the subtitle of playback. |
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE = 17 | Message returned when the audio output device changes.<br> If **key** is set to **<br>OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON**, the value type is int32_t. The system uses int32_t to transfer the value, and the application uses int32_t to obtain the value. |
| AV_INFO_TYPE_PLAYBACK_RATE_DONE = 18 | Message returned when the playback rate is applied. If **key** is set to **OH_PLAYER_PLAYBACK_RATE**, the value type is float. The system uses float to transfer the value, and the application uses float to obtain the value.<br>**Since**: 20 |
| AV_INFO_TYPE_SUPER_RESOLUTION_CHANGED = 19 | Message returned when the super resolution changes.<br>**Since**: 23 |

### AVPlayerBufferingType

```c
enum AVPlayerBufferingType
```

**Description**

Enumerates the types of buffer messages of the AVPlayer.

**Since**: 12

| Enum item | Description |
| -- | -- |
| AVPLAYER_BUFFERING_START = 1 | Buffering start message. |
| AVPLAYER_BUFFERING_END | Buffering end message. |
| AVPLAYER_BUFFERING_PERCENT | Buffer execution progress, in percentage. The value is an integer in the range [0, 100]. |
| AVPLAYER_BUFFERING_CACHED_DURATION | Duration that cached data can be played, in milliseconds. |

### AVPlayerTrackSwitchMode

```c
enum AVPlayerTrackSwitchMode
```

**Description**

Enumerates the track switching modes.

**Since**: 23

| Enum item | Description |
| -- | -- |
| AV_TRACK_SWITCH_MODE_SMOOTH = 0 | Switch tracks smoothly. |
| AV_TRACK_SWITCH_MODE_SEGMENT = 1 | Switch tracks by segment. |
| AV_TRACK_SWITCH_MODE_CLOSEST = 2 | Switch to the closest track. |

### OH_VideoOutputResult

```c
enum OH_VideoOutputResult
```

**Description**

Result of Video output.

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_VIDEO_OUTPUT_OK = 0 | Output one decoded video frame.<br>**Since**: 26.0.0 |
| OH_VIDEO_OUTPUT_NO_IMAGE = 1 | No frame ready to render.<br>**Since**: 26.0.0 |


## Function description

### OH_AVPlayerOnInfo()

```c
typedef void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)
```

**Description**

Called when the AVPlayer receives a message.

**Since**: 11

**Deprecated**: 12

**Replaced by**: [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | Message type. For details about the available options, see [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype). For details about the mappings between **type** and **extra** values, see the function description. |
| int32_t extra | Other information, such as the start time and position of the media file to play. |

### OH_AVPlayerOnInfoCallback()

```c
typedef void (*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)
```

**Description**

Called when the AVPlayer receives a message. If this callback is successfully set, the **OH_AVPlayerOnInfo**<br>function will not be invoked.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | Message type. For details about the available options, see [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype). |
| OH_AVFormat\* infoBody | Pointer to the message. The pointer is valid only in this callback. |
| void \*userData | Pointer to the instance provided by the caller when setting the callback function. |

### OH_AVPlayerOnError()

```c
typedef void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)
```

**Description**

Called when an error occurs in the AVPlayer. This callback is available in API version 9 or later.

**Since**: 11

**Deprecated**: 12

**Replaced by**: [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| int32_t errorCode | Error code. **AV_ERR_NO_MEMORY**: No memory. The value is **1**. {@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The value is **2**.<br>{@link AV_ERR_INVALID_VA}: Invalid value. The value is **3**.<br>**AV_ERR_IO**: I/O error. The value is **4**.<br>**AV_ERR_TIMEOUT**: Timeout. The value is **5**.<br>**AV_ERR_UNKNOWN**: Unknown error. The value is **6**.<br>{@link AV_ERR_SERVICE_DIED}: The service is dead. The value is **7**.<br>**AV_ERR_INVALID_STATE**: The operation is not supported in the current state. The value is **8**.<br>{@link AV_ERR_UNSUPPORT}: The function is not supported. The value is **9**. **AV_ERR_EXTEND_START**: Initial value for extended error codes. The value is **100**. |
| const char \*errorMsg | Error message. |

### OH_AVPlayerOnErrorCallback()

```c
typedef void (*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)
```

**Description**

Called when an error occurs in the AVPlayer. If this callback is successfully set, the **OH_AVPlayerOnError**<br>function will not be invoked.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| int32_t errorCode | Error code. **AV_ERR_NO_MEMORY**: No memory. The value is **1**. {@link AV_ERR_OPERATE_NOT_PERMIT}: The operation is not allowed. The value is **2**.<br>{@link AV_ERR_INVALID_VA}: Invalid value. The value is **3**.<br>**AV_ERR_IO**: I/O error. For API versions 12 and 13, the value is **4**. Starting from API version 14, it<br>corresponds to more specific error codes ranging from 5411001 to 5411011.<br>**AV_ERR_TIMEOUT**: Timeout. The value is **5**.<br>**AV_ERR_UNKNOWN**: Unknown error. The value is **6**.<br>{@link AV_ERR_SERVICE_DIED}: The service is dead. The value is **7**.<br>**AV_ERR_INVALID_STATE**: The operation is not supported in the current state. The value is **8**.<br>{@link AV_ERR_UNSUPPORT}: The function is not supported. The value is **9**. **AV_ERR_EXTEND_START**: Initial value for extended error codes. The value is **100**. |
| const char \*errorMsg | Error message, only valid in callback function. |
| void \*userData | Pointer to user specific data. |

### OH_AVPlayerOnAmplitudeUpdateCallback()

```c
typedef void (*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)
```

**Description**

Called when the maximum audio amplitude is calculated.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| double \*amplitudes | The pointer to the maximum audio level values array. Note: the amplitudes array will be released after callback automatically. If necessary, user need copy the data for the further use. |
| uint32_t size | Size of the maximum audio amplitude array. |
| void \*userData | Pointer to user specific data. |

### OH_AVPlayerOnSeiMessageReceivedCallback()

```c
typedef void (*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)
```

**Description**

Called for obtaining SEI messages. This function is used to subscribe to SEI message events and returns detailed SEI information.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) \*message | SEI message array. Note: the message array will be released after callback automatically. If necessary, user need copy the data for the further use. |
| int32_t playbackPosition | Playback position. |
| void \*userData | Pointer to user specific data |

### OH_AVPlayerPCMOutputCallback()

```c
typedef void (*OH_AVPlayerPCMOutputCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

Describes the handle used to obtain the decoded audio PCM data.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance |
| OH_AVBuffer \*pcmBuffer | Decoded PCM audio data. The pcmBuffer is valid only within this callback,  and released by the player after the callback returns. |
| void \*userData | Pointer to user specific data |

### OH_AVPlayerPCMProcessorCallback()

```c
typedef void (*OH_AVPlayerPCMProcessorCallback)(OH_AVPlayer *player, OH_AVBuffer *pcmBuffer, void *userData)
```

**Description**

This callback provides a PCM buffer for processing. AVPlayer needs to use the processed data for audio playback, and processing must be completed in a timely manner, otherwise it will block playback. Do not change sampling rate, channels, or sampling format.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance |
| OH_AVBuffer \*pcmBuffer | Decoded PCM audio data. The pcmBuffer is valid only within this callback,  and released by the player after the callback returns. |
| void \*userData | Pointer to user specific data |


