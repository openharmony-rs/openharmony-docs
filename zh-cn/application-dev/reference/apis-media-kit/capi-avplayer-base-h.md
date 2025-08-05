# avplayer_base.h
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xushubo; @chennotfound-->
<!--SE: @dongyu_dy-->
<!--TSE: @xchaosioda-->

## 概述

定义AVPlayer的结构体和枚举。

**引用文件：** <multimedia/player_framework/avplayer_base.h>

**库：** libavplayer.so

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

**相关模块：** [AVPlayer](capi-avplayer.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AVPlayerCallback](capi-avplayer-avplayercallback.md) | AVPlayerCallback | 包含了OH_AVPlayerOnInfo和OH_AVPlayerOnInfo回调函数指针的集合。应用需注册此结构体到OH_AVPlayer实例中，并处理回调上报的信息，保证AVPlayer的正常运行。 |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) | OH_AVPlayer | 初始化AVPlayer。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AVPlayerState](#avplayerstate) | AVPlayerState | 播放状态。 |
| [AVPlayerSeekMode](#avplayerseekmode) | AVPlayerSeekMode | 跳转模式。 |
| [AVPlaybackSpeed](#avplaybackspeed) | AVPlaybackSpeed | 播放速度。 |
| [AVPlayerOnInfoType](#avplayeroninfotype) | AVPlayerOnInfoType | OnInfo类型。<br>可用于OH_AVPlayerOnInfoCallback和OH_AVPlayerOnInfo(已废弃)，用于表示收到的播放器信息类型。 |
| [AVPlayerBufferingType](#avplayerbufferingtype) | AVPlayerBufferingType | 播放缓冲消息类型定义。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)](#oh_avplayeroninfo) | OH_AVPlayerOnInfo | 收到播放器消息时调用。 |
| [typedef void (\*OH_AVPlayerOnInfoCallback)(OH_AVPlayer \*player, AVPlayerOnInfoType type, OH_AVFormat* infoBody,void *userData)](#oh_avplayeroninfocallback) | OH_AVPlayerOnInfoCallback | 收到播放器消息时被调用。如果应用成功设置该回调，则不会回调OH_AVPlayerOnInfo函数。 |
| [typedef void (\*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)](#oh_avplayeronerror) | OH_AVPlayerOnError | 在API 9以上的版本发生错误时调用。 |
| [typedef void (\*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg,void *userData)](#oh_avplayeronerrorcallback) | OH_AVPlayerOnErrorCallback | 发生错误时被调用。如果应用成功设置该回调，则不会回调OH_AVPlayerOnError函数。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| const char * OH_PLAYER_STATE | 获取播放状态的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_STATE_CHANGE_REASON | 获取播放状态变更原因的关键字，对应值类型是int32_t。<br>1：用户操作触发；2：系统变更触发。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VOLUME | 获取音量的关键字，对应值类型是float。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BITRATE_ARRAY | 获取比特率列表的关键字，对应值类型是uint8_t字节数组。通过该关键字获取信息时：<br>需要先使用uint8_t类型指针变量保存比特率列表，使用size_t类型变量保存字节数组长度。<br>然后分配若干个uint32_t类型的存储空间，接收将uint8_t字节数组转换为uint32_t类型比特率整数值。<br>可以参考[开发指南](../../media/media/using-ndk-avplayer-for-playback.md)中OHAVPlayerOnInfoCallback函数。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_TYPE | 获取音频打断类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_FORCE | 获取音频打断FORCE类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_INTERRUPT_HINT | 获取音频打断HINT类型的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON | 获取音频设备变更原因的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BUFFERING_TYPE | 获取缓冲更新消息类型的关键字，对应值类型是[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。<br>通过该关键字获取信息时，需要先使用int32_t类型变量保存结果，再转换为AVPlayerBufferingType类型。<br>**起始版本：** 12 |
| const char * OH_PLAYER_BUFFERING_VALUE | 获取缓冲更新消息数值的关键字，对应值类型是int32_t，参见[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。<br>当缓冲更新消息类型是AVPLAYER_BUFFERING_PERCENT、AVPLAYER_BUFFERING_CACHED_DURATION时有效。<br>**起始版本：** 12 |
| const char * OH_PLAYER_SEEK_POSITION | 获取Seek后播放进度的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_PLAYBACK_SPEED | 获取播放倍速信息的关键字, 对应值类型是[AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed)。<br>通过该关键字获取信息时，需要先使用int32_t类型变量保存结果，再转换为AVPlaybackSpeed类型。<br>**起始版本：** 12 |
| const char * OH_PLAYER_PLAYBACK_RATE | 获取有效播放速率的关键字，对应值类型是浮点数。<br>**起始版本：** 20 |
| const char * OH_PLAYER_BITRATE | 获取比特率信息的关键字，对应值类型是uint32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_CURRENT_POSITION | 获取播放进度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_DURATION | 获取媒体资源时长信息的关键字，对应值类型是int64_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VIDEO_WIDTH | 获取视频宽度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_VIDEO_HEIGHT | 获取视频高度信息的关键字，对应值类型是int32_t。<br>**起始版本：** 12 |
| const char * OH_PLAYER_MESSAGE_TYPE | 获取播放器消息信息的关键字，对应值类型是int32_t。<br>1：视频帧开始渲染。<br>**起始版本：** 12 |
| const char * OH_PLAYER_IS_LIVE_STREAM | 获取媒体资源是否为直播类型信息的关键字，对应值类型是int32_t。<br>1：直播。<br>**起始版本：** 12 |

## 枚举类型说明

### AVPlayerState

```
enum AVPlayerState
```

**描述**

播放状态。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_IDLE = 0 | 空闲 |
| AV_INITIALIZED = 1 | 初始化 |
| AV_PREPARED = 2 | 准备 |
| AV_PLAYING = 3 | 播放 |
| AV_PAUSED = 4 | 暂停 |
| AV_STOPPED = 5 | 停止 |
| AV_COMPLETED = 6 | 结束 |
| AV_RELEASED = 7 | 释放 |
| AV_ERROR = 8 | 错误 |

### AVPlayerSeekMode

```
enum AVPlayerSeekMode
```

**描述**

跳转模式。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_SEEK_NEXT_SYNC = 0 | 同步到时间点之后的关键帧。 |
| AV_SEEK_PREVIOUS_SYNC | 同步到时间点之前的关键帧。 |
| AV_SEEK_CLOSEST = 2 | 同步到距离指定时间点最近的帧。<br>**起始版本：** 12 |

### AVPlaybackSpeed

```
enum AVPlaybackSpeed
```

**描述**

播放速度。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_SPEED_FORWARD_0_75_X | 0.75倍速播放。 |
| AV_SPEED_FORWARD_1_00_X | 正常播放。 |
| AV_SPEED_FORWARD_1_25_X | 1.25倍速播放。 |
| AV_SPEED_FORWARD_1_75_X | 1.75倍速播放。 |
| AV_SPEED_FORWARD_2_00_X | 2.0倍速播放。 |
| AV_SPEED_FORWARD_0_50_X | 0.5倍速播放。<br>**起始版本：** 12 |
| AV_SPEED_FORWARD_1_50_X | 1.5倍速播放。<br>**起始版本：** 12 |
| AV_SPEED_FORWARD_3_00_X | 3.0倍速播放。<br>**起始版本：** 13 |
| AV_SPEED_FORWARD_0_25_X | 0.25倍速播放。<br>**起始版本：** 13 |
| AV_SPEED_FORWARD_0_125_X | 0.125倍速播放。<br>**起始版本：** 13 |

### AVPlayerOnInfoType

```
enum AVPlayerOnInfoType
```

**描述**

OnInfo类型。<br>可用于OH_AVPlayerOnInfoCallback和OH_AVPlayerOnInfo(已废弃)，用于表示收到的播放器信息类型。<br>从API 12开始，推荐用户使用[OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)。不同的OnInfo类型，可获取到不同信息（infoBody），infoBody中包含key-value关系表，详见下述枚举值表。<br>使用API 11版本的开发者，需要使用旧接口。针对已废弃接口OH_AVPlayerOnInfo中使用的对应关系，可直接参考[OH_AVPlayerOnInfo](capi-avplayer-base-h.md#oh_avplayeroninfo)的API说明。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| AV_INFO_TYPE_SEEKDONE = 0 | 跳转到对应播放位置时返回消息。<br>key为OH_PLAYER_SEEK_POSITION：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。 |
| AV_INFO_TYPE_SPEEDDONE = 1 | 播放倍速设置完成时返回消息。<br>key为OH_PLAYER_PLAYBACK_SPEED：取值类型[AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed)。系统通过int32_t传递value，应用需先通过int32_t获取，再强制转为[AVPlaybackSpeed](capi-avplayer-base-h.md#avplaybackspeed)。 |
| AV_INFO_TYPE_BITRATEDONE = 2 | 比特率设置完成时返回消息。<br>key为OH_PLAYER_BITRATE：取值类型uint32_t。系统通过int32_t传递value，应用需先通过int32_t获取，再强制为uint32_t。 |
| AV_INFO_TYPE_EOS = 3 | 播放完成时返回消息。 |
| AV_INFO_TYPE_STATE_CHANGE = 4 | 状态改变时返回消息。<br>key为OH_PLAYER_STATE：取值类型int32_t。系统通过int32_t传递value，应用需先通过int32_t获取，再强制转为[AVPlayerState](capi-avplayer-base-h.md#avplayerstate)。<br>key为OH_PLAYER_STATE_CHANGE_REASON：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。1：用户操作触发；2：系统变更触发。 |
| AV_INFO_TYPE_POSITION_UPDATE = 5 | 返回当前播放位置。<br>key为OH_PLAYER_CURRENT_POSITION：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。 |
| AV_INFO_TYPE_MESSAGE = 6 | 视频开始渲染时返回消息。<br>key为OH_PLAYER_MESSAGE_TYPE：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。1表示视频开始渲染。 |
| AV_INFO_TYPE_VOLUME_CHANGE = 7 | 音量改变时返回消息。<br>key为OH_PLAYER_VOLUME：取值类型float。系统通过float传递value，应用需通过float获取。取值范围[0.0, 1.0]。 |
| AV_INFO_TYPE_RESOLUTION_CHANGE = 8 | 首次获取视频大小或视频大小更新时返回消息。<br>key为OH_PLAYER_VIDEO_WIDTH 或 OH_PLAYER_VIDEO_HEIGHT：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。 |
| AV_INFO_TYPE_BUFFERING_UPDATE = 9 | 返回多队列缓冲时间。<br>key为OH_PLAYER_BUFFERING_TYPE：取值类型[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。系统通过int32_t传递value，应用需先通过int32_t获取，再强制转为[AVPlayerBufferingType](capi-avplayer-base-h.md#avplayerbufferingtype)。<br>key为OH_PLAYER_BUFFERING_VALUE：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。<br>当缓冲更新消息类型是AVPLAYER_BUFFERING_PERCENT、AVPLAYER_BUFFERING_CACHED_DURATION时有效，分别表示缓冲进度完成百分比、缓冲数据可播放时长。 |
| AV_INFO_TYPE_BITRATE_COLLECT = 10 | 上报HLS视频比特率列表消息。<br>key为OH_PLAYER_BITRATE_ARRAY：取值类型uint8_t字节数组。应用需要先使用uint8_t类型指针变量保存比特率列表，使用size_t类型变量保存字节数组长度。然后分配若干个uint32_t类型的存储空间，接收将uint8_t字节数组转换为uint32_t类型比特率整数值。 |
| AV_INFO_TYPE_INTERRUPT_EVENT = 11 | 音频焦点改变时返回消息。<br>取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。<br>key为：<br>OH_PLAYER_AUDIO_INTERRUPT_TYPE：取值1表示中断事件开始；2表示结束。<br>OH_PLAYER_AUDIO_INTERRUPT_FORCE：取值0表示强制打断，系统改变音频播放状态；1表示共享打断，应用改变音频播放状态。<br>OH_PLAYER_AUDIO_INTERRUPT_HINT：取值0表示NONE，无提示；1表示RESUME，提示音频恢复；2表示PAUSE，提示音频暂停暂时失去焦点；3表示STOP，提示音频停止；4表示DUCK，音频降低音量；5表示UNDUCK，音频恢复音量。 |
| AV_INFO_TYPE_DURATION_UPDATE = 12 | 返回播放时长。<br>key为OH_PLAYER_DURATION：取值类型int64_t。系统通过int64_t传递value，应用需通过int64_t获取。 |
| AV_INFO_TYPE_IS_LIVE_STREAM = 13 | 播放为直播流时返回消息。key为OH_PLAYER_IS_LIVE_STREAM：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。0表示非直播流，1表示直播流。 |
| AV_INFO_TYPE_TRACKCHANGE = 14 | 轨道改变时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_TRACK_INFO_UPDATE = 15 | 轨道更新时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_SUBTITLE_UPDATE = 16 | 字幕信息更新时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE = 17 | 音频输出设备改变时返回消息。<br>key为OH_PLAYER_AUDIO_DEVICE_CHANGE_REASON：取值类型int32_t。系统通过int32_t传递value，应用需通过int32_t获取。 |
| AV_INFO_TYPE_PLAYBACK_RATE_DONE = 18 | 播放速率成功应用时返回消息。<br>key为OH_PLAYER_PLAYBACK_RATE：取值类型float。系统通过float传递value，应用通过float获取。<br>**起始版本：** 20 |

### AVPlayerBufferingType

```
enum AVPlayerBufferingType
```

**描述**

播放缓冲消息类型定义。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AVPLAYER_BUFFERING_START = 1 | 缓冲开始消息。 |
| AVPLAYER_BUFFERING_END | 缓冲结束消息。 |
| AVPLAYER_BUFFERING_PERCENT | 缓冲执行进度百分比，取值范围：整数，[0, 100]。 |
| AVPLAYER_BUFFERING_CACHED_DURATION | 缓冲数据可播放时长，单位：毫秒。 |


## 函数说明

### OH_AVPlayerOnInfo()

```
typedef void (*OH_AVPlayerOnInfo)(OH_AVPlayer *player, AVPlayerOnInfoType type, int32_t extra)
```

**描述**

收到播放器消息时调用。

信息类型（type）和信息（extra）的对应关系如表所示。

| 信息类型（type） | 对应的extra描述 |
| -------- | -------- |
| AV_INFO_TYPE_SEEKDONE | 跳转到对应播放位置时返回消息，extra表示跳转到的位置。 |
| AV_INFO_TYPE_SPEEDDONE | 播放倍速设置完成时返回消息，extra表示播放倍速信息，具体请参考[AVPlaybackSpeed](#avplaybackspeed)。 |
| AV_INFO_TYPE_BITRATEDONE | 比特率设置完成时返回消息，extra表示比特率信息。 |
| AV_INFO_TYPE_EOS | 播放完成时返回消息。|
| AV_INFO_TYPE_STATE_CHANGE | 状态改变时返回消息，extra表示当前播放状态，具体请参见[AVPlayerState](#avplayerstate)。 |
| AV_INFO_TYPE_POSITION_UPDATE | 返回当前播放位置，extra表示当前位置。 |
| AV_INFO_TYPE_MESSAGE | 视频开始渲染时返回消息，extra表示视频首帧渲染。 |
| AV_INFO_TYPE_VOLUME_CHANGE | 音量改变时返回消息，此场景下extra未定义。 |
| AV_INFO_TYPE_RESOLUTION_CHANGE | 首次获取视频大小或视频大小更新时返回消息，此场景下extra未定义。 |
| AV_INFO_TYPE_BUFFERING_UPDATE | 返回多队列缓冲时间，extra表示视频时长。 |
| AV_INFO_TYPE_BITRATE_COLLECT  | 上报HLS视频比特率列表消息。上报时每个比特率已经转化为uint8_t字节数组，使用者需要将uint8_t字节数组强制转换为uint32_t整型数组。   |
| AV_INFO_TYPE_INTERRUPT_EVENT | 音频焦点改变时返回消息，extra表示音频打断提示，具体请参见[OH_AudioInterrupt_Hint](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiointerrupt_hint)，应用可决定是否根据打断提示作进一步处理。 |
| AV_INFO_TYPE_DURATION_UPDATE | 返回播放时长，extra表示视频时长。 |
| AV_INFO_TYPE_IS_LIVE_STREAM | 播放为直播流时返回消息，extra表示是否为直播流，0表示非直播流，1表示直播流。 |
| AV_INFO_TYPE_TRACKCHANGE | 轨道改变时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_TRACK_INFO_UPDATE |轨道更新时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_SUBTITLE_UPDATE | 字幕信息更新时返回消息，此场景extra未定义。 |
| AV_INFO_TYPE_AUDIO_OUTPUT_DEVICE_CHANGE | 音频输出设备改变时返回消息，extra表示设备改变原因，具体请参见[OH_AudioStream_DeviceChangeReason](../apis-audio-kit/capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason)。 |

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback)


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | 指向OH_AVPlayer实例的指针。 |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | 信息类型。类型为[AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype)，与extra的对应关系可见方法描述。 |
|  int32_t extra | 其他信息，如播放文件的开始时间位置。 |

### OH_AVPlayerOnInfoCallback()

```
typedef void (*OH_AVPlayerOnInfoCallback)(OH_AVPlayer *player, AVPlayerOnInfoType type, OH_AVFormat* infoBody,void *userData)
```

**描述**

收到播放器消息时被调用。如果应用成功设置该回调，则不会回调OH_AVPlayerOnInfo函数。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | 指向OH_AVPlayer实例的指针。 |
| [AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype) type | 信息类型。具体请参见[AVPlayerOnInfoType](capi-avplayer-base-h.md#avplayeroninfotype)。 |
| [OH_AVFormat](../apis-avcodec-kit/_core.md#oh_avformat)* infoBody | 指向携带具体消息的指针，仅在该回调方法内有效。 |
| void *userData | 指向应用调用者设置该回调函数时提供的实例的指针。 |

### OH_AVPlayerOnError()

```
typedef void (*OH_AVPlayerOnError)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg)
```

**描述**

在api9以上的版本发生错误时调用

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 11

**废弃版本：** 12

**替代接口：** [OH_AVPlayerOnInfoCallback](capi-avplayer-base-h.md#oh_avplayeroninfocallback) [OH_AVPlayerOnError](capi-avplayer-base-h.md#oh_avplayeronerror)


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | 指向OH_AVPlayer实例的指针。 |
|  int32_t errorCode | 错误码。<br>AV_ERR_NO_MEMORY：无内存，取值为1。<br>AV_ERR_OPERATE_NOT_PERMIT：操作不允许，取值为2。<br>AV_ERR_INVALID_VAL：无效值，取值为3。<br>AV_ERR_IO：IO错误，取值为4。<br>AV_ERR_TIMEOUT：超时错误，取值为5。<br>AV_ERR_UNKNOWN：未知错误，取值为6。<br>AV_ERR_SERVICE_DIED：服务死亡，取值为7。<br>AV_ERR_INVALID_STATE：当前状态不支持此操作，取值为8。<br>AV_ERR_UNSUPPORT：未支持的接口，取值为9。<br>AV_ERR_EXTEND_START：扩展错误码初始值，取值为100。 |
|  const char *errorMsg | 错误消息。 |

### OH_AVPlayerOnErrorCallback()

```
typedef void (*OH_AVPlayerOnErrorCallback)(OH_AVPlayer *player, int32_t errorCode, const char *errorMsg,void *userData)
```

**描述**

发生错误时被调用。如果应用成功设置该回调，则不会调用OH_AVPlayerOnError函数。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVPlayer](capi-avplayer-oh-avplayer.md) *player | 指向OH_AVPlayer实例的指针。 |
|  int32_t errorCode | 错误码。<br>AV_ERR_NO_MEMORY：无内存，取值为1。<br>AV_ERR_OPERATE_NOT_PERMIT：操作不允许，取值为2。<br>AV_ERR_INVALID_VAL：无效值，取值为3。<br>AV_ERR_IO：IO错误，取值为4。<br>AV_ERR_TIMEOUT：超时错误，取值为5。<br>AV_ERR_UNKNOWN：未知错误，取值为6。<br>AV_ERR_SERVICE_DIED：服务死亡，取值为7。<br>AV_ERR_INVALID_STATE：当前状态不支持此操作，取值为8。<br>AV_ERR_UNSUPPORT：未支持的接口，取值为9。<br>AV_ERR_EXTEND_START：扩展错误码初始值，取值为100。 |
|  const char *errorMsg | 错误消息。 |
| void *userData | 原样返回用户设置回调时传入的userData数据。 |


