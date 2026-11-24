# native_avsession_base.h

## Overview

Declare avsession base info.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

**Related module**: [OHAVSession](capi-avsession-kit-ohavsession.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVSession_Type](#avsession_type) | AVSession_Type | Enum for avsession type. |
| [AVSession_PlaybackState](#avsession_playbackstate) | AVSession_PlaybackState | Enum for playback state. |
| [AVSession_LoopMode](#avsession_loopmode) | AVSession_LoopMode | Defines the playback mode. |
| [AVSession_ControlCommand](#avsession_controlcommand) | AVSession_ControlCommand | Enum for different control command. |
| [AVMetadata_SkipIntervals](#avmetadata_skipintervals) | AVMetadata_SkipIntervals | Defines the skip interval when fastforward or rewind. |
| [AVMetadata_DisplayTag](#avmetadata_displaytag) | AVMetadata_DisplayTag | Display tag |
| [AVSession_ConnectionState](#avsession_connectionstate) | AVSession_ConnectionState | Enum for device connection state. |
| [AVSession_AVCastCategory](#avsession_avcastcategory) | AVSession_AVCastCategory | Enum for cast category indicating different playback scenes. |
| [AVSession_DeviceType](#avsession_devicetype) | AVSession_DeviceType | Enum for Device type . |
| [AVSession_ProtocolType](#avsession_protocoltype) | AVSession_ProtocolType | Enum for Protocol type . |
| [AVSession_AVCastControlCommandType](#avsession_avcastcontrolcommandtype) | AVSession_AVCastControlCommandType | Enum for command type . |
| [AVSession_PlaybackSpeed](#avsession_playbackspeed) | AVSession_PlaybackSpeed | Enum for playback speed type. |
| [AVSession_PlaybackFilter](#avsession_playbackfilter) | AVSession_PlaybackFilter | Enum for playbackstate filter. |

## Enum type description

### AVSession_Type

```c
enum AVSession_Type
```

**Description**

Enum for avsession type.

<!--Device-enum AVSession_Type--><!--Device-enum AVSession_Type-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| SESSION_TYPE_AUDIO = 0 | audio session type.<br><!--Device-SESSION_TYPE_AUDIO = 0--><!--Device-SESSION_TYPE_AUDIO = 0-End--> |
| SESSION_TYPE_VIDEO = 1 | video session type.<br><!--Device-SESSION_TYPE_VIDEO = 1--><!--Device-SESSION_TYPE_VIDEO = 1-End--> |
| SESSION_TYPE_VOICE_CALL = 2 | voice call session type.<br><!--Device-SESSION_TYPE_VOICE_CALL = 2--><!--Device-SESSION_TYPE_VOICE_CALL = 2-End--> |
| SESSION_TYPE_VIDEO_CALL = 3 | video call session type.<br><!--Device-SESSION_TYPE_VIDEO_CALL = 3--><!--Device-SESSION_TYPE_VIDEO_CALL = 3-End--> |
| SESSION_TYPE_PHOTO = 4 | photo session type.<br><!--Device-SESSION_TYPE_PHOTO = 4--><!--Device-SESSION_TYPE_PHOTO = 4-End--> |

### AVSession_PlaybackState

```c
enum AVSession_PlaybackState
```

**Description**

Enum for playback state.

<!--Device-enum AVSession_PlaybackState--><!--Device-enum AVSession_PlaybackState-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| PLAYBACK_STATE_INITIAL = 0 | Initial state.<br><!--Device-PLAYBACK_STATE_INITIAL = 0--><!--Device-PLAYBACK_STATE_INITIAL = 0-End--> |
| PLAYBACK_STATE_PREPARING = 1 | Preparing state. Indicates that the media file is not ready to play.<br><!--Device-PLAYBACK_STATE_PREPARING = 1--><!--Device-PLAYBACK_STATE_PREPARING = 1-End--> |
| PLAYBACK_STATE_PLAYING = 2 | Playing state.<br><!--Device-PLAYBACK_STATE_PLAYING = 2--><!--Device-PLAYBACK_STATE_PLAYING = 2-End--> |
| PLAYBACK_STATE_PAUSED = 3 | Pause state.<br><!--Device-PLAYBACK_STATE_PAUSED = 3--><!--Device-PLAYBACK_STATE_PAUSED = 3-End--> |
| PLAYBACK_STATE_FAST_FORWARDING = 4 | Fast forward state.<br><!--Device-PLAYBACK_STATE_FAST_FORWARDING = 4--><!--Device-PLAYBACK_STATE_FAST_FORWARDING = 4-End--> |
| PLAYBACK_STATE_REWINDED = 5 | Rewind state.<br><!--Device-PLAYBACK_STATE_REWINDED = 5--><!--Device-PLAYBACK_STATE_REWINDED = 5-End--> |
| PLAYBACK_STATE_STOPPED = 6 | Stopped state.<br><!--Device-PLAYBACK_STATE_STOPPED = 6--><!--Device-PLAYBACK_STATE_STOPPED = 6-End--> |
| PLAYBACK_STATE_COMPLETED = 7 | Complete state.<br><!--Device-PLAYBACK_STATE_COMPLETED = 7--><!--Device-PLAYBACK_STATE_COMPLETED = 7-End--> |
| PLAYBACK_STATE_RELEASED = 8 | Release state.<br><!--Device-PLAYBACK_STATE_RELEASED = 8--><!--Device-PLAYBACK_STATE_RELEASED = 8-End--> |
| PLAYBACK_STATE_ERROR = 9 | Error state.<br><!--Device-PLAYBACK_STATE_ERROR = 9--><!--Device-PLAYBACK_STATE_ERROR = 9-End--> |
| PLAYBACK_STATE_IDLE = 10 | Idle state.<br><!--Device-PLAYBACK_STATE_IDLE = 10--><!--Device-PLAYBACK_STATE_IDLE = 10-End--> |
| PLAYBACK_STATE_BUFFERING = 11 | Buffering state.<br><!--Device-PLAYBACK_STATE_BUFFERING = 11--><!--Device-PLAYBACK_STATE_BUFFERING = 11-End--> |
| PLAYBACK_STATE_MAX = 12 | Max state.<br><!--Device-PLAYBACK_STATE_MAX = 12--><!--Device-PLAYBACK_STATE_MAX = 12-End--> |

### AVSession_LoopMode

```c
enum AVSession_LoopMode
```

**Description**

Defines the playback mode.

<!--Device-enum AVSession_LoopMode--><!--Device-enum AVSession_LoopMode-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| LOOP_MODE_SEQUENCE = 0 | sequential playback mode<br><!--Device-LOOP_MODE_SEQUENCE = 0--><!--Device-LOOP_MODE_SEQUENCE = 0-End--> |
| LOOP_MODE_SINGLE = 1 | single playback mode<br><!--Device-LOOP_MODE_SINGLE = 1--><!--Device-LOOP_MODE_SINGLE = 1-End--> |
| LOOP_MODE_LIST = 2 | list playback mode<br><!--Device-LOOP_MODE_LIST = 2--><!--Device-LOOP_MODE_LIST = 2-End--> |
| LOOP_MODE_SHUFFLE = 3 | shuffle playback mode<br><!--Device-LOOP_MODE_SHUFFLE = 3--><!--Device-LOOP_MODE_SHUFFLE = 3-End--> |
| LOOP_MODE_CUSTOM = 4 | custom playback mode<br><!--Device-LOOP_MODE_CUSTOM = 4--><!--Device-LOOP_MODE_CUSTOM = 4-End--> |

### AVSession_ControlCommand

```c
enum AVSession_ControlCommand
```

**Description**

Enum for different control command.

<!--Device-enum AVSession_ControlCommand--><!--Device-enum AVSession_ControlCommand-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| CONTROL_CMD_INVALID = -1 | invalid control command<br><!--Device-CONTROL_CMD_INVALID = -1--><!--Device-CONTROL_CMD_INVALID = -1-End--> |
| CONTROL_CMD_PLAY = 0 | play command<br><!--Device-CONTROL_CMD_PLAY = 0--><!--Device-CONTROL_CMD_PLAY = 0-End--> |
| CONTROL_CMD_PAUSE = 1 | pause command<br><!--Device-CONTROL_CMD_PAUSE = 1--><!--Device-CONTROL_CMD_PAUSE = 1-End--> |
| CONTROL_CMD_STOP = 2 | stop command<br><!--Device-CONTROL_CMD_STOP = 2--><!--Device-CONTROL_CMD_STOP = 2-End--> |
| CONTROL_CMD_PLAY_NEXT = 3 | playnext command<br><!--Device-CONTROL_CMD_PLAY_NEXT = 3--><!--Device-CONTROL_CMD_PLAY_NEXT = 3-End--> |
| CONTROL_CMD_PLAY_PREVIOUS = 4 | playprevious command<br><!--Device-CONTROL_CMD_PLAY_PREVIOUS = 4--><!--Device-CONTROL_CMD_PLAY_PREVIOUS = 4-End--> |

### AVMetadata_SkipIntervals

```c
enum AVMetadata_SkipIntervals
```

**Description**

Defines the skip interval when fastforward or rewind.

<!--Device-enum AVMetadata_SkipIntervals--><!--Device-enum AVMetadata_SkipIntervals-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| SECONDS_10 = 10 | 10 seconds<br><!--Device-SECONDS_10 = 10--><!--Device-SECONDS_10 = 10-End--> |
| SECONDS_15 = 15 | 15 seconds<br><!--Device-SECONDS_15 = 15--><!--Device-SECONDS_15 = 15-End--> |
| SECONDS_30 = 30 | 30 seconds<br><!--Device-SECONDS_30 = 30--><!--Device-SECONDS_30 = 30-End--> |

### AVMetadata_DisplayTag

```c
enum AVMetadata_DisplayTag
```

**Description**

Display tag

<!--Device-enum AVMetadata_DisplayTag--><!--Device-enum AVMetadata_DisplayTag-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1 | Indicate the audio vivid property.<br><!--Device-AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1--><!--Device-AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1-End--> |

### AVSession_ConnectionState

```c
enum AVSession_ConnectionState
```

**Description**

Enum for device connection state.

<!--Device-enum AVSession_ConnectionState--><!--Device-enum AVSession_ConnectionState-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| STATE_CONNECTING = 0 | A connection state indicating the device is in the process of connecting.<br>**Since**: 23<br><!--Device-STATE_CONNECTING = 0--><!--Device-STATE_CONNECTING = 0-End--> |
| STATE_CONNECTED = 1 | A connection state indicating the device is connected.<br>**Since**: 23<br><!--Device-STATE_CONNECTED = 1--><!--Device-STATE_CONNECTED = 1-End--> |
| STATE_DISCONNECTED = 6 | The default connection state indicating the device is disconnected.<br>**Since**: 23<br><!--Device-STATE_DISCONNECTED = 6--><!--Device-STATE_DISCONNECTED = 6-End--> |

### AVSession_AVCastCategory

```c
enum AVSession_AVCastCategory
```

**Description**

Enum for cast category indicating different playback scenes.

<!--Device-enum AVSession_AVCastCategory--><!--Device-enum AVSession_AVCastCategory-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| CATEGORY_LOCAL = 0 | The default cast type "local", media can be routed on the same device, including internal speakers or audio jack on the device itself, A2DP devices.<br><!--Device-CATEGORY_LOCAL = 0--><!--Device-CATEGORY_LOCAL = 0-End--> |
| CATEGORY_REMOTE = 1 | The remote category indicating the media is presenting on a remote device, the application needs to get an AVCastController to control remote playback.<br><!--Device-CATEGORY_REMOTE = 1--><!--Device-CATEGORY_REMOTE = 1-End--> |

### AVSession_DeviceType

```c
enum AVSession_DeviceType
```

**Description**

Enum for Device type .

<!--Device-enum AVSession_DeviceType--><!--Device-enum AVSession_DeviceType-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| DEVICE_TYPE_LOCAL = 0 | A device type indicating the route is on internal speakers or audio jack on the device itself.<br>**Since**: 23<br><!--Device-DEVICE_TYPE_LOCAL = 0--><!--Device-DEVICE_TYPE_LOCAL = 0-End--> |
| DEVICE_TYPE_TV = 2 | A device type indicating the route is on a TV.<br>**Since**: 23<br><!--Device-DEVICE_TYPE_TV = 2--><!--Device-DEVICE_TYPE_TV = 2-End--> |
| DEVICE_TYPE_SMART_SPEAKER = 3 | A device type indicating the route is on a smart speaker.<br>**Since**: 23<br><!--Device-DEVICE_TYPE_SMART_SPEAKER = 3--><!--Device-DEVICE_TYPE_SMART_SPEAKER = 3-End--> |
| DEVICE_TYPE_BLUETOOTH = 10 | A device type indicating the route is on a bluetooth device.<br>**Since**: 23<br><!--Device-DEVICE_TYPE_BLUETOOTH = 10--><!--Device-DEVICE_TYPE_BLUETOOTH = 10-End--> |

### AVSession_ProtocolType

```c
enum AVSession_ProtocolType
```

**Description**

Enum for Protocol type .

<!--Device-enum AVSession_ProtocolType--><!--Device-enum AVSession_ProtocolType-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| TYPE_LOCAL = 0 | The default cast type "local", media can be routed on the same device, including internal speakers or audio jack on the device itself, A2DP devices.<br>**Since**: 23<br><!--Device-TYPE_LOCAL = 0--><!--Device-TYPE_LOCAL = 0-End--> |
| TYPE_CAST_PLUS_STREAM = 2 | The Cast+ Stream indicating the media is presenting on a different device the application need get an AVCastController to control remote playback.<br>**Since**: 23<br><!--Device-TYPE_CAST_PLUS_STREAM = 2--><!--Device-TYPE_CAST_PLUS_STREAM = 2-End--> |
| TYPE_DLNA = 4 | The DLNA type indicates the device supports DLNA protocol, the application needs to get an AVCastController to control remote playback.<br>**Since**: 23<br><!--Device-TYPE_DLNA = 4--><!--Device-TYPE_DLNA = 4-End--> |
| TYPE_CAST_PLUS_AUDIO = 8 | This type indicates the device supports audio casting with high defination to get a better sound quality.<br>**Since**: 23<br><!--Device-TYPE_CAST_PLUS_AUDIO = 8--><!--Device-TYPE_CAST_PLUS_AUDIO = 8-End--> |

### AVSession_AVCastControlCommandType

```c
enum AVSession_AVCastControlCommandType
```

**Description**

Enum for command type .

<!--Device-enum AVSession_AVCastControlCommandType--><!--Device-enum AVSession_AVCastControlCommandType-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| CAST_CONTROL_CMD_PLAY = 0 | Play Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_PLAY = 0--><!--Device-CAST_CONTROL_CMD_PLAY = 0-End--> |
| CAST_CONTROL_CMD_PAUSE = 1 | Pause Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_PAUSE = 1--><!--Device-CAST_CONTROL_CMD_PAUSE = 1-End--> |
| CAST_CONTROL_CMD_STOP = 2 | Stop Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_STOP = 2--><!--Device-CAST_CONTROL_CMD_STOP = 2-End--> |
| CAST_CONTROL_CMD_PLAY_NEXT = 3 | Play next Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_PLAY_NEXT = 3--><!--Device-CAST_CONTROL_CMD_PLAY_NEXT = 3-End--> |
| CAST_CONTROL_CMD_PLAY_PREVIOUS = 4 | Play previous Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_PLAY_PREVIOUS = 4--><!--Device-CAST_CONTROL_CMD_PLAY_PREVIOUS = 4-End--> |
| CAST_CONTROL_CMD_FAST_FORWARD = 5 | Fast forward Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_FAST_FORWARD = 5--><!--Device-CAST_CONTROL_CMD_FAST_FORWARD = 5-End--> |
| CAST_CONTROL_CMD_REWIND = 6 | Rewind Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_REWIND = 6--><!--Device-CAST_CONTROL_CMD_REWIND = 6-End--> |
| CAST_CONTROL_CMD_SEEK = 7 | Seek Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_SEEK = 7--><!--Device-CAST_CONTROL_CMD_SEEK = 7-End--> |
| CAST_CONTROL_CMD_SET_VOLUME = 8 | Set volume Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_SET_VOLUME = 8--><!--Device-CAST_CONTROL_CMD_SET_VOLUME = 8-End--> |
| CAST_CONTROL_CMD_SET_SPEED = 9 | Set speed Command<br>**Since**: 23<br><!--Device-CAST_CONTROL_CMD_SET_SPEED = 9--><!--Device-CAST_CONTROL_CMD_SET_SPEED = 9-End--> |

### AVSession_PlaybackSpeed

```c
enum AVSession_PlaybackSpeed
```

**Description**

Enum for playback speed type.

<!--Device-enum AVSession_PlaybackSpeed--><!--Device-enum AVSession_PlaybackSpeed-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| SPEED_FORWARD_0_75_X = 0 | Video playback at 0.75x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_0_75_X = 0--><!--Device-SPEED_FORWARD_0_75_X = 0-End--> |
| SPEED_FORWARD_1_00_X = 1 | Video playback at 1.00x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_1_00_X = 1--><!--Device-SPEED_FORWARD_1_00_X = 1-End--> |
| SPEED_FORWARD_1_25_X = 2 | Video playback at 1.25x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_1_25_X = 2--><!--Device-SPEED_FORWARD_1_25_X = 2-End--> |
| SPEED_FORWARD_1_75_X = 3 | Video playback at 1.75x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_1_75_X = 3--><!--Device-SPEED_FORWARD_1_75_X = 3-End--> |
| SPEED_FORWARD_2_00_X = 4 | Video playback at 2.00x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_2_00_X = 4--><!--Device-SPEED_FORWARD_2_00_X = 4-End--> |
| SPEED_FORWARD_0_50_X = 5 | Video playback at 0.50x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_0_50_X = 5--><!--Device-SPEED_FORWARD_0_50_X = 5-End--> |
| SPEED_FORWARD_1_50_X = 6 | Video playback at 1.50x normal speed.<br>**Since**: 23<br><!--Device-SPEED_FORWARD_1_50_X = 6--><!--Device-SPEED_FORWARD_1_50_X = 6-End--> |

### AVSession_PlaybackFilter

```c
enum AVSession_PlaybackFilter
```

**Description**

Enum for playbackstate filter.

<!--Device-enum AVSession_PlaybackFilter--><!--Device-enum AVSession_PlaybackFilter-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| FILTER_STATE = 1 << 0 | filter state<br>**Since**: 23<br><!--Device-FILTER_STATE = 1 << 0--><!--Device-FILTER_STATE = 1 << 0-End--> |
| FILTER_POSITION = 1 << 1 | filter position<br>**Since**: 23<br><!--Device-FILTER_POSITION = 1 << 1--><!--Device-FILTER_POSITION = 1 << 1-End--> |
| FILTER_SPEED = 1 << 2 | filter Speed<br>**Since**: 23<br><!--Device-FILTER_SPEED = 1 << 2--><!--Device-FILTER_SPEED = 1 << 2-End--> |
| FILTER_VOLUME = 1 << 3 | filter volume<br>**Since**: 23<br><!--Device-FILTER_VOLUME = 1 << 3--><!--Device-FILTER_VOLUME = 1 << 3-End--> |


