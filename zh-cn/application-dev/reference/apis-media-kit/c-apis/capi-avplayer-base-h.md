# avplayer_base.h

## 概述

定义AVPlayer的结构体和枚举。

**库：** libavplayer.so

**起始版本：** 11

**相关模块：** [AVPlayer](capi-avplayer.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) | AVPlayerCallback | 包含了OH_AVPlayerOnInfo和OH_AVPlayerOnError回调函数指针的集合。应用需注册此实例结构体到OH_AVPlayer实例中，并对回调上报的信息进行处理，保证AVPlayer的正常运行。(API12废弃) |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) | OH_AVSeiMessageArray | SEI消息数组的结构体类型。 |
| [OH_AVPlaybackStrategy](capi-avplayer-oh-avplaybackstrategy.md) | OH_AVPlaybackStrategy | 音视频播放策略的结构体类型。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AVPlayerState](#avplayerstate) | AVPlayerState | 播放状态。 |
| [AVPlayerSeekMode](#avplayerseekmode) | AVPlayerSeekMode | 跳转模式。 |
| [AVPlaybackSpeed](#avplaybackspeed) | AVPlaybackSpeed | 播放速度。 |
| [AVPlayerOnInfoType](#avplayeroninfotype) | AVPlayerOnInfoType | OnInfo类型。可用于OH_AVPlayerOnInfoCallback和OH_AVPlayerOnInfo(已废弃)，用于表示收到的播放器信息类型。从API version 12开始，推荐用户使用[OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)。不同的OnInfo类型，可获取到不同信息（infoBody），infoBody中包含key-value关系表，详见下述枚举值表。使用API version 11版本的开发者，需要使用旧接口。针对已废弃接口OH_AVPlayerOnInfo中使用的对应关系，可直接参考[OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo)的API说明。 |
| [AVPlayerBufferingType](#avplayerbufferingtype) | AVPlayerBufferingType | 播放缓冲消息类型定义。 |
| [AVPlayerTrackSwitchMode](#avplayertrackswitchmode) | AVPlayerTrackSwitchMode | 枚举轨道切换模式。 |
| [OH_VideoOutputResult](#oh_videooutputresult) | OH_VideoOutputResult | Result of Video output. |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)](#oh_avplayeroninfo) | OH_AVPlayerOnInfo | 收到播放器消息时调用。(API12废弃) |
| [typedef void (\*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)](#oh_avplayeroninfocallback) | OH_AVPlayerOnInfoCallback | 收到播放器消息时被调用。如果应用成功设置该回调，则不会回调OH_AVPlayerOnInfo函数。 |
| [typedef void (\*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)](#oh_avplayeronerror) | OH_AVPlayerOnError | 在API version 9以上的版本发生错误时调用。(API12废弃) |
| [typedef void (\*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)](#oh_avplayeronerrorcallback) | OH_AVPlayerOnErrorCallback | 发生错误时被调用。如果应用成功设置该回调，则不会调用OH_AVPlayerOnError函数。 |
| [typedef void (\*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)](#oh_avplayeronamplitudeupdatecallback) | OH_AVPlayerOnAmplitudeUpdateCallback | 当计算出最大音频电平值时调用。 |
| [typedef void (\*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)](#oh_avplayeronseimessagereceivedcallback) | OH_AVPlayerOnSeiMessageReceivedCallback | 用于获取SEI消息的回调处理函数。在订阅SEI消息事件时使用，回调返回详细的SEI信息。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| const char * OH_PLAYER_STATE | 获取播放状态的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_STATE_CHANGE_REASON | 获取播放状态变更原因的关键字，对应值类型是int32_t。1：用户操作触发；2：系统变更触发。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VOLUME | 获取音量的关键字，对应值类型是float。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BITRATE_ARRAY | 获取比特率列表的关键字，对应值类型是uint8_t字节数组。通过该关键字获取信息时：需要先使用uint8_t类型指针变量保存比特率列表，使用size_t类型变量保存字节数组长度。然后分配若干个uint32_t类型的存储空间，接收将uint8_t字节数组转换为uint32_t类型比特率整数值。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_TYPE | 获取音频打断类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_FORCE | 获取音频打断FORCE类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_HINT | 获取音频打断HINT类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON | 获取音频设备变更原因的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BUFFERING_TYPE | 获取缓冲更新消息类型的关键字，对应值类型是[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。通过该关键字获取信息时，需要先使用int32_t类型变量保存结果，再转换为AVPlayerBufferingType类型。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BUFFERING_VALUE | 获取缓冲更新消息数值的关键字，对应值类型是int32_t，参见[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。当缓冲更新消息类型是AVPLAYER_BUFFERING_PERCENT、AVPLAYER_BUFFERING_CACHED_DURATION时有效。<br>**起始版本：** 12 |
| const char * OH_PLAYER_SEEK_POSITION | 获取Seek后播放进度的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_PLAYBACK_SPEED | 获取播放倍速信息的关键字, 对应值类型是[AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed)。通过该关键字获取信息时，需要先使用int32_t类型变量保存结果，再转换为AVPlaybackSpeed类型。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BITRATE | 获取比特率列表的关键字，对应值类型是uint8_t字节数组。通过该关键字获取信息时：需要先使用uint8_t类型指针变量保存比特率列表，使用size_t类型变量保存字节数组长度。然后分配若干个uint32_t类型的存储空间，接收将uint8_t字节数组转换为uint32_t类型比特率整数值。<br>**起始版本：** 12 |
| const char * OH_PLAYER_CURRENT_POSITION | 获取播放进度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_DURATION | 获取媒体资源时长信息的关键字，对应值类型是int64_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VIDEO_WIDTH | 获取视频宽度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VIDEO_HEIGHT | 获取视频高度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_MESSAGE_TYPE | 获取播放器消息信息的关键字，对应值类型是int32_t。1：视频帧开始渲染。<br>**起始版本：** 12 |
| const char * OH_PLAYER_IS_LIVE_STREAM | 获取媒体资源是否为直播类型信息的关键字，对应值类型是int32_t。1：直播。<br>**起始版本：** 12 |
| const char * OH_PLAYER_SEI_PAYLOAD_TYPE |  |
| const char * OH_PLAYER_SEI_PAYLOAD_CONTENT |  |
| const char * OH_PLAYER_SUPER_RESOLUTION_ENABLE_STATE | 超分辨率功能启用状态关键字，值类型为int32_t。值为1表示已启用，0表示未启用；用于超分辨率状态变化时的信息回调。<br>**起始版本：** 23 |
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_INDEX | 轨道切换信息中表示轨道索引的关键字，值类型为int32_t。<br>**起始版本：** 23 |
| const char * OH_PLAYER_TRACH_CHANGE_INFO_TRACK_SELECTED | 轨道切换信息中表示轨道是否被选中的标志关键字，值类型为int32_t。<br>**起始版本：** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_DURATION | 字幕更新信息中表示持续时间的关键字，值类型为int32_t。<br>**起始版本：** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_START_TIME | 字幕更新信息中表示起始时间的关键字，值类型为int32_t。<br>**起始版本：** 23 |
| const char * OH_PLAYER_SUBTITLE_UPDATE_INFO_TEXT | 字幕更新信息中表示字幕文本内容的关键字，值类型为字符串（string）。<br>**起始版本：** 23 |
| const char * OH_PLAYER_PLAYBACK_RATE | 获取有效播放速率的关键字，对应值类型是浮点数。<br>**起始版本：** 20 |
| const char * OH_PLAYER_MD_KEY_HAS_VIDEO | 获取媒体资源是否包含视频轨信息的关键字，对应值类型int32_t。1：包含视频轨，0：不包含视频轨。<br>**起始版本：** 22 |
| const char * OH_PLAYER_MD_KEY_HAS_AUDIO | 获取媒体资源是否包含音频轨信息的关键字，对应值类型int32_t。1：包含音频轨，0：不包含音频轨。<br>**起始版本：** 22 |
| const char * OH_PLAYER_MD_KEY_HAS_SUBTITLE | 获取媒体资源是否包含字幕轨信息的关键字，对应值类型int32_t。1：包含字幕轨，0：不包含字幕轨。<br>**起始版本：** 22 |
| const char * OH_PLAYER_MD_KEY_TRACK_INDEX | 获取媒体资源轨道下标信息的关键字，对应值类型int32_t。<br>**起始版本：** 22 |
| const char * OH_MEDIA_EVENT_INFO_PREPARE_DURATION | 获取统计指标信息中的准备时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_RESOURCE_CONNECTION_DURATION | 获取统计指标信息中的资源链接建立时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_FIRST_FRAME_DECAPSULATION_DURATION | 获取统计指标信息中的首帧解封装时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_TOTAL_PLAYING_TIME | 获取统计指标信息中的累计播放时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_REQUEST_COUNT | 获取统计指标信息中的媒体资源加载请求累计次数的关键字，对应值类型为uint32_t。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_TIME | 获取统计指标信息中的媒体资源加载总时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_DOWNLOAD_TOTAL_SIZE | 获取统计指标信息中的已加载媒体资源累计字节数的关键字，对应值类型为int64_t。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_STALLING_COUNT | 获取统计指标信息中的累计卡顿次数的关键字，对应值类型为uint32_t。<br>**起始版本：** 23 |
| const char * OH_MEDIA_EVENT_INFO_TOTAL_STALLING_TIME | 获取统计指标信息中的累计卡顿时长的关键字，对应值类型为uint32_t，单位为毫秒。<br>**起始版本：** 23 |
| const char * OH_PLAYER_SERVER_IP_ADDRESS |  |
| const char * OH_PLAYER_IS_DOWNLOADING |  |
| const char * OH_PLAYER_BUFFER_DURATION |  |
| const char * OH_PLAYER_DOWNLOAD_RATE |  |
| const char * OH_PLAYER_AVG_DOWNLOAD_RATE |  |

## 枚举类型说明

### AVPlayerState

```c
enum AVPlayerState
```

**描述**

播放状态。

**起始版本：** 11

| 枚举项 | 描述 |
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

**描述**

跳转模式。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_SEEK_NEXT_SYNC = 0 | sync to keyframes after the time point. |
| AV_SEEK_PREVIOUS_SYNC | sync to keyframes before the time point. |
| AV_SEEK_CLOSEST = 2 | 同步到距离指定时间点最近的帧。<br>**起始版本：** 12 |
| AV_SEEK_CONTINUOUS = 3 | 连续拖动模式下的跳转（seek）。该模式可提供更流畅的拖拽体验，但要求设备支持对当前流执行连续跳转。在调用连续跳转前，请先检查是否支持，参见{@link OH_AVPlayer_IsSeekContinuousSupported}。**起始版本：** 23 |

### AVPlaybackSpeed

```c
enum AVPlaybackSpeed
```

**描述**

播放速度。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_SPEED_FORWARD_0_75_X | Video playback at 0.75x normal speed |
| AV_SPEED_FORWARD_1_00_X | Video playback at normal speed |
| AV_SPEED_FORWARD_1_25_X | Video playback at 1.25x normal speed |
| AV_SPEED_FORWARD_1_75_X | Video playback at 1.75x normal speed |
| AV_SPEED_FORWARD_2_00_X | Video playback at 2.0x normal speed |
| AV_SPEED_FORWARD_0_50_X | 0.5倍速播放。<br>**起始版本：** 12 |
| AV_SPEED_FORWARD_1_50_X | 1.5倍速播放。<br>**起始版本：** 12 |
| AV_SPEED_FORWARD_3_00_X | 3.0倍速播放。<br>**起始版本：** 13 |
| AV_SPEED_FORWARD_0_25_X | 0.25倍速播放。<br>**起始版本：** 13 |
| AV_SPEED_FORWARD_0_125_X | 0.125倍速播放。<br>**起始版本：** 13 |

### AVPlayerOnInfoType

```c
enum AVPlayerOnInfoType
```

**描述**

OnInfo类型。可用于OH_AVPlayerOnInfoCallback和OH_AVPlayerOnInfo(已废弃)，用于表示收到的播放器信息类型。从API version 12开始，推荐用户使用[OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)。不同的OnInfo类型，可获取到不同信息（infoBody），infoBody中包含key-value关系表，详见下述枚举值表。使用API version 11版本的开发者，需要使用旧接口。针对已废弃接口OH_AVPlayerOnInfo中使用的对应关系，可直接参考[OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo)的API说明。

**起始版本：** 11

| 枚举项 | 描述 |
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
| AV_INFO_TYPE_BITRATE_COLLECT = 10 | return hls bitrate.       Bitrate is to convert data into uint8_t array storage, |
| AV_INFO_TYPE_INTERRUPT_EVENT = 11 | return the message when audio focus changed. |
| AV_INFO_TYPE_DURATION_UPDATE = 12 | return the duration of playback. |
| AV_INFO_TYPE_IS_LIVE_STREAM = 13 | return the playback is live stream. |
| AV_INFO_TYPE_TRACKCHANGE = 14 | return the message when track changes. |
| AV_INFO_TYPE_TRACK_INFO_UPDATE = 15 | return the message when subtitle track info updated. |
| AV_INFO_TYPE_SUBTITLE_UPDATE = 16 | return the subtitle of playback. |
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE = 17 | 音频输出设备改变时返回消息。<br> key为OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。 |
| AV_INFO_TYPE_PLAYBACK_RATE_DONE = 18 | 播放速率成功应用时返回消息。key为OH_PLAYER_PLAYBACK_RATE：取值类型float。系统通过float传递value，应用通过float获取。<br>**起始版本：** 20 |
| AV_INFO_TYPE_SUPER_RESOLUTION_CHANGED = 19 | 超分辨率变化时返回消息。<br>**起始版本：** 23 |

### AVPlayerBufferingType

```c
enum AVPlayerBufferingType
```

**描述**

播放缓冲消息类型定义。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AVPLAYER_BUFFERING_START = 1 | 缓冲开始消息。 |
| AVPLAYER_BUFFERING_END | 缓冲结束消息。 |
| AVPLAYER_BUFFERING_PERCENT | 缓冲执行进度百分比，取值范围：整数，[0, 100]。 |
| AVPLAYER_BUFFERING_CACHED_DURATION | 缓冲数据可播放时长，单位：毫秒。 |

### AVPlayerTrackSwitchMode

```c
enum AVPlayerTrackSwitchMode
```

**描述**

枚举轨道切换模式。

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| AV_TRACK_SWITCH_MODE_SMOOTH = 0 | 平滑切换轨道。 |
| AV_TRACK_SWITCH_MODE_SEGMENT = 1 | 按片段切换轨道。 |
| AV_TRACK_SWITCH_MODE_CLOSEST = 2 | 切换到最接近的轨道。 |

### OH_VideoOutputResult

```c
enum OH_VideoOutputResult
```

**描述**

Result of Video output.

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_VIDEO_OUTPUT_OK = 0 | Output one decoded video frame.<br>**起始版本：** 26.0.0 |
| OH_VIDEO_OUTPUT_NO_IMAGE = 1 | No frame ready to render.<br>**起始版本：** 26.0.0 |


## 函数说明

### OH_AVPlayerOnInfo()

```c
typedef void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)
```

**描述**

收到播放器消息时调用。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | 指向OH_AVPlayer实例的指针。 |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | 信息类型。类型为[AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype)，与extra的对应关系可见方法描述。 |
| int32_t extra | 其他信息，如播放文件的开始时间位置。 |

### OH_AVPlayerOnInfoCallback()

```c
typedef void (*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody, void *userData)
```

**描述**

收到播放器消息时被调用。如果应用成功设置该回调，则不会回调OH_AVPlayerOnInfo函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | 指向OH_AVPlayer实例的指针。 |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | 信息类型。具体请参见[AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype)。 |
| [OH_AVFormat](capi-core-oh-avformat.md)\* infoBody | 指向携带具体消息的指针，仅在该回调方法内有效。 |
| void \*userData | 指向应用调用者设置该回调函数时提供的实例的指针。 |

### OH_AVPlayerOnError()

```c
typedef void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)
```

**描述**

在API version 9以上的版本发生错误时调用。

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnErrorCallback](capi-avplayer-base-h.md#oh_avplayeronerrorcallback)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | 指向OH_AVPlayer实例的指针。 |
| int32_t errorCode | 错误码。AV_ERR_NO_MEMORY：无内存，取值为1。AV_ERR_OPERATE_NOT_PERMIT：操作不允许，取值为2。AV_ERR_INVALID_VAL：无效值，取值为3。AV_ERR_IO：IO错误，取值为4。AV_ERR_TIMEOUT：超时错误，取值为5。AV_ERR_UNKNOWN：未知错误，取值为6。AV_ERR_SERVICE_DIED：服务死亡，取值为7。AV_ERR_INVALID_STATE：当前状态不支持此操作，取值为8。AV_ERR_UNSUPPORT：未支持的接口，取值为9。AV_ERR_EXTEND_START：扩展错误码初始值，取值为100。 |
| const char \*errorMsg | Error message. |

### OH_AVPlayerOnErrorCallback()

```c
typedef void (*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg, void *userData)
```

**描述**

发生错误时被调用。如果应用成功设置该回调，则不会调用OH_AVPlayerOnError函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | 指向OH_AVPlayer实例的指针。 |
| int32_t errorCode | 错误码。AV_ERR_NO_MEMORY：无内存，取值为1。AV_ERR_OPERATE_NOT_PERMIT：操作不允许，取值为2。AV_ERR_INVALID_VAL：无效值，取值为3。AV_ERR_IO：IO错误。API version 12-13取值为4；API version 14及以后，对应错误细化为错误码5411001~5411011。AV_ERR_TIMEOUT：超时错误，取值为5。AV_ERR_UNKNOWN：未知错误，取值为6。AV_ERR_SERVICE_DIED：服务死亡，取值为7。AV_ERR_INVALID_STATE：当前状态不支持此操作，取值为8。AV_ERR_UNSUPPORT：未支持的接口，取值为9。AV_ERR_EXTEND_START：扩展错误码初始值，取值为100。 |
| const char \*errorMsg | Error message, only valid in callback function. |
| void \*userData | Pointer to user specific data. |

### OH_AVPlayerOnAmplitudeUpdateCallback()

```c
typedef void (*OH_AVPlayerOnAmplitudeUpdateCallback)(OH_AVPlayer *player, double *amplitudes, uint32_t size, void *userData)
```

**描述**

当计算出最大音频电平值时调用。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance. |
| double \*amplitudes | The pointer to the maximum audio level values array.Note: the amplitudes array will be released after callback automatically.If necessary, user need copy the data for the further use. |
| uint32_t size | 最大音频电平值数组的大小。 |
| void \*userData | Pointer to user specific data. |

### OH_AVPlayerOnSeiMessageReceivedCallback()

```c
typedef void (*OH_AVPlayerOnSeiMessageReceivedCallback)(OH_AVPlayer *player, OH_AVSeiMessageArray *message, int32_t playbackPosition, void *userData)
```

**描述**

用于获取SEI消息的回调处理函数。在订阅SEI消息事件时使用，回调返回详细的SEI信息。

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AVPlayer \*player | Pointer to an OH_AVPlayer instance |
| [OH_AVSeiMessageArray](capi-avplayer-oh-avseimessagearray.md) \*message | SEI message array.Note: the message array will be released after callback automatically.If necessary, user need copy the data for the further use. |
| int32_t playbackPosition | 播放位置。 |
| void \*userData | Pointer to user specific data |


