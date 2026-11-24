# native_avsession_base.h

## 概述

声明AVSession基本信息。

**库：** libohavsession.so

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

**相关模块：** [OHAVSession](capi-avsession-kit-ohavsession.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AVSession_Type](#avsession_type) | AVSession_Type | 会话类型枚举。 |
| [AVSession_PlaybackState](#avsession_playbackstate) | AVSession_PlaybackState | 媒体播放状态的相关属性枚举。 |
| [AVSession_LoopMode](#avsession_loopmode) | AVSession_LoopMode | 定义媒体播放循环模式。 |
| [AVSession_ControlCommand](#avsession_controlcommand) | AVSession_ControlCommand | 播控命令枚举。 |
| [AVMetadata_SkipIntervals](#avmetadata_skipintervals) | AVMetadata_SkipIntervals | 定义快进或快退的时间间隔。 |
| [AVMetadata_DisplayTag](#avmetadata_displaytag) | AVMetadata_DisplayTag | 当前媒体资源的金标枚举，即应用媒体音源的特殊类型标识。 |
| [AVSession_ConnectionState](#avsession_connectionstate) | AVSession_ConnectionState | 设备连接状态枚举。 |
| [AVSession_AVCastCategory](#avsession_avcastcategory) | AVSession_AVCastCategory | 表示不同播放场景的投播类别枚举。 |
| [AVSession_DeviceType](#avsession_devicetype) | AVSession_DeviceType | 设备类型枚举。 |
| [AVSession_ProtocolType](#avsession_protocoltype) | AVSession_ProtocolType | 协议类型枚举。 |
| [AVSession_AVCastControlCommandType](#avsession_avcastcontrolcommandtype) | AVSession_AVCastControlCommandType | 命令类型枚举。 |
| [AVSession_PlaybackSpeed](#avsession_playbackspeed) | AVSession_PlaybackSpeed | 播放倍速类型枚举。 |
| [AVSession_PlaybackFilter](#avsession_playbackfilter) | AVSession_PlaybackFilter | 播放状态过滤器枚举。 |

## 枚举类型说明

### AVSession_Type

```c
enum AVSession_Type
```

**描述：**

会话类型枚举。

<!--Device-enum AVSession_Type--><!--Device-enum AVSession_Type-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| SESSION_TYPE_AUDIO = 0 | 音频会话类型（指媒体类音频，如音乐）。<br><!--Device-SESSION_TYPE_AUDIO = 0--><!--Device-SESSION_TYPE_AUDIO = 0-End--> |
| SESSION_TYPE_VIDEO = 1 | 视频会话类型（指媒体类投屏视频）。<br><!--Device-SESSION_TYPE_VIDEO = 1--><!--Device-SESSION_TYPE_VIDEO = 1-End--> |
| SESSION_TYPE_VOICE_CALL = 2 | 音频通话会话类型（指人机交互相关的音频，如语音助手）。<br><!--Device-SESSION_TYPE_VOICE_CALL = 2--><!--Device-SESSION_TYPE_VOICE_CALL = 2-End--> |
| SESSION_TYPE_VIDEO_CALL = 3 | 视频通话会话类型（指视频电话）。<br><!--Device-SESSION_TYPE_VIDEO_CALL = 3--><!--Device-SESSION_TYPE_VIDEO_CALL = 3-End--> |
| SESSION_TYPE_PHOTO = 4 | 相片会话类型。<br><!--Device-SESSION_TYPE_PHOTO = 4--><!--Device-SESSION_TYPE_PHOTO = 4-End--> |

### AVSession_PlaybackState

```c
enum AVSession_PlaybackState
```

**描述：**

媒体播放状态的相关属性枚举。

<!--Device-enum AVSession_PlaybackState--><!--Device-enum AVSession_PlaybackState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| PLAYBACK_STATE_INITIAL = 0 | 初始状态。<br><!--Device-PLAYBACK_STATE_INITIAL = 0--><!--Device-PLAYBACK_STATE_INITIAL = 0-End--> |
| PLAYBACK_STATE_PREPARING = 1 | 准备播放状态。表示媒体资源还未处于可播放状态。<br><!--Device-PLAYBACK_STATE_PREPARING = 1--><!--Device-PLAYBACK_STATE_PREPARING = 1-End--> |
| PLAYBACK_STATE_PLAYING = 2 | 正在播放状态。<br><!--Device-PLAYBACK_STATE_PLAYING = 2--><!--Device-PLAYBACK_STATE_PLAYING = 2-End--> |
| PLAYBACK_STATE_PAUSED = 3 | 暂停播放状态。<br><!--Device-PLAYBACK_STATE_PAUSED = 3--><!--Device-PLAYBACK_STATE_PAUSED = 3-End--> |
| PLAYBACK_STATE_FAST_FORWARDING = 4 | 快进状态。<br><!--Device-PLAYBACK_STATE_FAST_FORWARDING = 4--><!--Device-PLAYBACK_STATE_FAST_FORWARDING = 4-End--> |
| PLAYBACK_STATE_REWINDED = 5 | 快退状态。<br><!--Device-PLAYBACK_STATE_REWINDED = 5--><!--Device-PLAYBACK_STATE_REWINDED = 5-End--> |
| PLAYBACK_STATE_STOPPED = 6 | 停止状态。<br><!--Device-PLAYBACK_STATE_STOPPED = 6--><!--Device-PLAYBACK_STATE_STOPPED = 6-End--> |
| PLAYBACK_STATE_COMPLETED = 7 | 播放完成状态。<br><!--Device-PLAYBACK_STATE_COMPLETED = 7--><!--Device-PLAYBACK_STATE_COMPLETED = 7-End--> |
| PLAYBACK_STATE_RELEASED = 8 | 释放状态。<br><!--Device-PLAYBACK_STATE_RELEASED = 8--><!--Device-PLAYBACK_STATE_RELEASED = 8-End--> |
| PLAYBACK_STATE_ERROR = 9 | 错误状态。<br><!--Device-PLAYBACK_STATE_ERROR = 9--><!--Device-PLAYBACK_STATE_ERROR = 9-End--> |
| PLAYBACK_STATE_IDLE = 10 | 空闲状态。<br><!--Device-PLAYBACK_STATE_IDLE = 10--><!--Device-PLAYBACK_STATE_IDLE = 10-End--> |
| PLAYBACK_STATE_BUFFERING = 11 | 缓冲状态。<br><!--Device-PLAYBACK_STATE_BUFFERING = 11--><!--Device-PLAYBACK_STATE_BUFFERING = 11-End--> |
| PLAYBACK_STATE_MAX = 12 | 最大状态（当状态值为12时，返回错误码401）。<br><!--Device-PLAYBACK_STATE_MAX = 12--><!--Device-PLAYBACK_STATE_MAX = 12-End--> |

### AVSession_LoopMode

```c
enum AVSession_LoopMode
```

**描述：**

定义媒体播放循环模式。

<!--Device-enum AVSession_LoopMode--><!--Device-enum AVSession_LoopMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| LOOP_MODE_SEQUENCE = 0 | 按顺序播放。<br><!--Device-LOOP_MODE_SEQUENCE = 0--><!--Device-LOOP_MODE_SEQUENCE = 0-End--> |
| LOOP_MODE_SINGLE = 1 | 单曲循环。<br><!--Device-LOOP_MODE_SINGLE = 1--><!--Device-LOOP_MODE_SINGLE = 1-End--> |
| LOOP_MODE_LIST = 2 | 按表单循环。<br><!--Device-LOOP_MODE_LIST = 2--><!--Device-LOOP_MODE_LIST = 2-End--> |
| LOOP_MODE_SHUFFLE = 3 | 随机播放。<br><!--Device-LOOP_MODE_SHUFFLE = 3--><!--Device-LOOP_MODE_SHUFFLE = 3-End--> |
| LOOP_MODE_CUSTOM = 4 | 自定义播放。<br><!--Device-LOOP_MODE_CUSTOM = 4--><!--Device-LOOP_MODE_CUSTOM = 4-End--> |

### AVSession_ControlCommand

```c
enum AVSession_ControlCommand
```

**描述：**

播控命令枚举。

<!--Device-enum AVSession_ControlCommand--><!--Device-enum AVSession_ControlCommand-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| CONTROL_CMD_INVALID = -1 | 无效控制命令。<br><!--Device-CONTROL_CMD_INVALID = -1--><!--Device-CONTROL_CMD_INVALID = -1-End--> |
| CONTROL_CMD_PLAY = 0 | 播放命令。<br><!--Device-CONTROL_CMD_PLAY = 0--><!--Device-CONTROL_CMD_PLAY = 0-End--> |
| CONTROL_CMD_PAUSE = 1 | 暂停命令。<br><!--Device-CONTROL_CMD_PAUSE = 1--><!--Device-CONTROL_CMD_PAUSE = 1-End--> |
| CONTROL_CMD_STOP = 2 | 停止命令。<br><!--Device-CONTROL_CMD_STOP = 2--><!--Device-CONTROL_CMD_STOP = 2-End--> |
| CONTROL_CMD_PLAY_NEXT = 3 | 播放下一首命令。<br><!--Device-CONTROL_CMD_PLAY_NEXT = 3--><!--Device-CONTROL_CMD_PLAY_NEXT = 3-End--> |
| CONTROL_CMD_PLAY_PREVIOUS = 4 | 播放上一首命令。<br><!--Device-CONTROL_CMD_PLAY_PREVIOUS = 4--><!--Device-CONTROL_CMD_PLAY_PREVIOUS = 4-End--> |

### AVMetadata_SkipIntervals

```c
enum AVMetadata_SkipIntervals
```

**描述：**

定义快进或快退的时间间隔。

<!--Device-enum AVMetadata_SkipIntervals--><!--Device-enum AVMetadata_SkipIntervals-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| SECONDS_10 = 10 | 时间间隔为10秒。<br><!--Device-SECONDS_10 = 10--><!--Device-SECONDS_10 = 10-End--> |
| SECONDS_15 = 15 | 时间间隔为15秒。<br><!--Device-SECONDS_15 = 15--><!--Device-SECONDS_15 = 15-End--> |
| SECONDS_30 = 30 | 时间间隔为30秒。<br><!--Device-SECONDS_30 = 30--><!--Device-SECONDS_30 = 30-End--> |

### AVMetadata_DisplayTag

```c
enum AVMetadata_DisplayTag
```

**描述：**

当前媒体资源的金标枚举，即应用媒体音源的特殊类型标识。

<!--Device-enum AVMetadata_DisplayTag--><!--Device-enum AVMetadata_DisplayTag-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1 | 高清音频。<br><!--Device-AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1--><!--Device-AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1-End--> |

### AVSession_ConnectionState

```c
enum AVSession_ConnectionState
```

**描述：**

设备连接状态枚举。

<!--Device-enum AVSession_ConnectionState--><!--Device-enum AVSession_ConnectionState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| STATE_CONNECTING = 0 | 表示设备正处于连接状态。<br>**起始版本：** 23<br><!--Device-STATE_CONNECTING = 0--><!--Device-STATE_CONNECTING = 0-End--> |
| STATE_CONNECTED = 1 | 表示设备处于已连接状态。<br>**起始版本：** 23<br><!--Device-STATE_CONNECTED = 1--><!--Device-STATE_CONNECTED = 1-End--> |
| STATE_DISCONNECTED = 6 | 表示设备已处于断开默认连接的状态。<br>**起始版本：** 23<br><!--Device-STATE_DISCONNECTED = 6--><!--Device-STATE_DISCONNECTED = 6-End--> |

### AVSession_AVCastCategory

```c
enum AVSession_AVCastCategory
```

**描述：**

表示不同播放场景的投播类别枚举。

<!--Device-enum AVSession_AVCastCategory--><!--Device-enum AVSession_AVCastCategory-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| CATEGORY_LOCAL = 0 | 默认投播类别是本地。 默认投屏类型为本地。媒体本地路由支持内置扬声器、音频插孔、A2DP（Advanced Audio Distribution Profile）设备。<br><!--Device-CATEGORY_LOCAL = 0--><!--Device-CATEGORY_LOCAL = 0-End--> |
| CATEGORY_REMOTE = 1 | 远程类别。 表示媒体正在远程设备上展示，应用需要一个[OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md)来控制远程播放。<br><!--Device-CATEGORY_REMOTE = 1--><!--Device-CATEGORY_REMOTE = 1-End--> |

### AVSession_DeviceType

```c
enum AVSession_DeviceType
```

**描述：**

设备类型枚举。

<!--Device-enum AVSession_DeviceType--><!--Device-enum AVSession_DeviceType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| DEVICE_TYPE_LOCAL = 0 | 一种设备类型，标识音频路由为设备自身的内置扬声器或音频插孔。<br>**起始版本：** 23<br><!--Device-DEVICE_TYPE_LOCAL = 0--><!--Device-DEVICE_TYPE_LOCAL = 0-End--> |
| DEVICE_TYPE_TV = 2 | 一种设备类型，标识音频路由为电视端。<br>**起始版本：** 23<br><!--Device-DEVICE_TYPE_TV = 2--><!--Device-DEVICE_TYPE_TV = 2-End--> |
| DEVICE_TYPE_SMART_SPEAKER = 3 | 一种设备类型，标识音频路由为智能音箱端。<br>**起始版本：** 23<br><!--Device-DEVICE_TYPE_SMART_SPEAKER = 3--><!--Device-DEVICE_TYPE_SMART_SPEAKER = 3-End--> |
| DEVICE_TYPE_BLUETOOTH = 10 | 一种设备类型，标识音频路由为蓝牙设备端。<br>**起始版本：** 23<br><!--Device-DEVICE_TYPE_BLUETOOTH = 10--><!--Device-DEVICE_TYPE_BLUETOOTH = 10-End--> |

### AVSession_ProtocolType

```c
enum AVSession_ProtocolType
```

**描述：**

协议类型枚举。

<!--Device-enum AVSession_ProtocolType--><!--Device-enum AVSession_ProtocolType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| TYPE_LOCAL = 0 | 默认为本地设备。 包括设备本身的内置扬声器或音频插孔，A2DP（Advanced Audio Distribution Profile）设备。<br>**起始版本：** 23<br><!--Device-TYPE_LOCAL = 0--><!--Device-TYPE_LOCAL = 0-End--> |
| TYPE_CAST_PLUS_STREAM = 2 | Cast+的Stream模式。 表示媒体正在其他设备上展示，应用需要一个AVCastController来控制远程播放。<br>**起始版本：** 23<br><!--Device-TYPE_CAST_PLUS_STREAM = 2--><!--Device-TYPE_CAST_PLUS_STREAM = 2-End--> |
| TYPE_DLNA = 4 | DLNA（DIGITAL LIVING NETWORK ALLIANCE）协议。 表示设备支持DLNA协议，应用需要一个AVCastController来控制远程播放。<br>**起始版本：** 23<br><!--Device-TYPE_DLNA = 4--><!--Device-TYPE_DLNA = 4-End--> |
| TYPE_CAST_PLUS_AUDIO = 8 | 表示该设备支持高清晰度的音频投播，以获得更好的音质。<br>**起始版本：** 23<br><!--Device-TYPE_CAST_PLUS_AUDIO = 8--><!--Device-TYPE_CAST_PLUS_AUDIO = 8-End--> |

### AVSession_AVCastControlCommandType

```c
enum AVSession_AVCastControlCommandType
```

**描述：**

命令类型枚举。

<!--Device-enum AVSession_AVCastControlCommandType--><!--Device-enum AVSession_AVCastControlCommandType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| CAST_CONTROL_CMD_PLAY = 0 | 播放命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_PLAY = 0--><!--Device-CAST_CONTROL_CMD_PLAY = 0-End--> |
| CAST_CONTROL_CMD_PAUSE = 1 | 暂停命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_PAUSE = 1--><!--Device-CAST_CONTROL_CMD_PAUSE = 1-End--> |
| CAST_CONTROL_CMD_STOP = 2 | 停止命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_STOP = 2--><!--Device-CAST_CONTROL_CMD_STOP = 2-End--> |
| CAST_CONTROL_CMD_PLAY_NEXT = 3 | 下一首命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_PLAY_NEXT = 3--><!--Device-CAST_CONTROL_CMD_PLAY_NEXT = 3-End--> |
| CAST_CONTROL_CMD_PLAY_PREVIOUS = 4 | 上一首命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_PLAY_PREVIOUS = 4--><!--Device-CAST_CONTROL_CMD_PLAY_PREVIOUS = 4-End--> |
| CAST_CONTROL_CMD_FAST_FORWARD = 5 | 快进命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_FAST_FORWARD = 5--><!--Device-CAST_CONTROL_CMD_FAST_FORWARD = 5-End--> |
| CAST_CONTROL_CMD_REWIND = 6 | 快退命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_REWIND = 6--><!--Device-CAST_CONTROL_CMD_REWIND = 6-End--> |
| CAST_CONTROL_CMD_SEEK = 7 | 跳转到指定播放位置命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_SEEK = 7--><!--Device-CAST_CONTROL_CMD_SEEK = 7-End--> |
| CAST_CONTROL_CMD_SET_VOLUME = 8 | 设置音量命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_SET_VOLUME = 8--><!--Device-CAST_CONTROL_CMD_SET_VOLUME = 8-End--> |
| CAST_CONTROL_CMD_SET_SPEED = 9 | 设置播放倍速命令。<br>**起始版本：** 23<br><!--Device-CAST_CONTROL_CMD_SET_SPEED = 9--><!--Device-CAST_CONTROL_CMD_SET_SPEED = 9-End--> |

### AVSession_PlaybackSpeed

```c
enum AVSession_PlaybackSpeed
```

**描述：**

播放倍速类型枚举。

<!--Device-enum AVSession_PlaybackSpeed--><!--Device-enum AVSession_PlaybackSpeed-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| SPEED_FORWARD_0_75_X = 0 | 以正常播速的0.75倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_0_75_X = 0--><!--Device-SPEED_FORWARD_0_75_X = 0-End--> |
| SPEED_FORWARD_1_00_X = 1 | 以正常播速（1.00x）播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_1_00_X = 1--><!--Device-SPEED_FORWARD_1_00_X = 1-End--> |
| SPEED_FORWARD_1_25_X = 2 | 以正常播速的1.25倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_1_25_X = 2--><!--Device-SPEED_FORWARD_1_25_X = 2-End--> |
| SPEED_FORWARD_1_75_X = 3 | 以正常播速的1.75倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_1_75_X = 3--><!--Device-SPEED_FORWARD_1_75_X = 3-End--> |
| SPEED_FORWARD_2_00_X = 4 | 以正常播速的2倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_2_00_X = 4--><!--Device-SPEED_FORWARD_2_00_X = 4-End--> |
| SPEED_FORWARD_0_50_X = 5 | 以正常播速的0.5倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_0_50_X = 5--><!--Device-SPEED_FORWARD_0_50_X = 5-End--> |
| SPEED_FORWARD_1_50_X = 6 | 以正常播速的1.5倍速播放音视频。<br>**起始版本：** 23<br><!--Device-SPEED_FORWARD_1_50_X = 6--><!--Device-SPEED_FORWARD_1_50_X = 6-End--> |

### AVSession_PlaybackFilter

```c
enum AVSession_PlaybackFilter
```

**描述：**

播放状态过滤器枚举。

<!--Device-enum AVSession_PlaybackFilter--><!--Device-enum AVSession_PlaybackFilter-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**起始版本：** 23

| 枚举项 | 描述 |
| -- | -- |
| FILTER_STATE = 1 << 0 | 过滤状态。<br>**起始版本：** 23<br><!--Device-FILTER_STATE = 1 << 0--><!--Device-FILTER_STATE = 1 << 0-End--> |
| FILTER_POSITION = 1 << 1 | 过滤位置。<br>**起始版本：** 23<br><!--Device-FILTER_POSITION = 1 << 1--><!--Device-FILTER_POSITION = 1 << 1-End--> |
| FILTER_SPEED = 1 << 2 | 过滤倍速。<br>**起始版本：** 23<br><!--Device-FILTER_SPEED = 1 << 2--><!--Device-FILTER_SPEED = 1 << 2-End--> |
| FILTER_VOLUME = 1 << 3 | 过滤音量。<br>**起始版本：** 23<br><!--Device-FILTER_VOLUME = 1 << 3--><!--Device-FILTER_VOLUME = 1 << 3-End--> |


