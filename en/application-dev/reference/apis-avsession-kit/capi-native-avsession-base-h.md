# native_avsession_base.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

Declares the basic information about **AVSession**.

**File to include:** <multimedia/av_session/native_avsession_base.h>

**Library:** libohavsession.so

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVSession_Type](#avsession_type) | AVSession_Type | Enumerates the session types.|
| [AVSession_PlaybackState](#avsession_playbackstate) | AVSession_PlaybackState | Enumerates the properties related to the media playback state.|
| [AVSession_LoopMode](#avsession_loopmode) | AVSession_LoopMode | Enumerates the loop modes of media playback.|
| [AVSession_ControlCommand](#avsession_controlcommand) | AVSession_ControlCommand | Enumerates the playback control commands.|
| [AVMetadata_SkipIntervals](#avmetadata_skipintervals) | AVMetadata_SkipIntervals | Enumerates the fast-forward or rewind skip intervals.|
| [AVMetadata_DisplayTag](#avmetadata_displaytag) | AVMetadata_DisplayTag | Enumerates the display tags for the media asset. The display tag is a special type identifier of the application media audio source.|
| [AVSession_ConnectionState](#avsession_connectionstate) | AVSession_ConnectionState | Enumerates the device connection states.|
| [AVSession_AVCastCategory](#avsession_avcastcategory) | AVSession_AVCastCategory | Enumerates the casting categories in different playback scenarios.|
| [AVSession_DeviceType](#avsession_devicetype) | AVSession_DeviceType | Enumerates the device types.|
| [AVSession_ProtocolType](#avsession_protocoltype) | AVSession_ProtocolType | Enumerates the protocol types.|
| [AVSession_AVCastControlCommandType](#avsession_avcastcontrolcommandtype) | AVSession_AVCastControlCommandType | Enumerates the command types.|
| [AVSession_PlaybackSpeed](#avsession_playbackspeed) | AVSession_PlaybackSpeed | Enumerates the playback speed types.|
| [AVSession_PlaybackFilter](#avsession_playbackfilter) | AVSession_PlaybackFilter | Enumerates the playback state filters.|

## Enum Description

### AVSession_Type

```c
enum AVSession_Type
```

**Description**

Enumerates the session types.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| SESSION_TYPE_AUDIO = 0 | Audio session (media audio, such as music).|
| SESSION_TYPE_VIDEO = 1 | Video session (media casting video).|
| SESSION_TYPE_VOICE_CALL = 2 | Voice call session (human-machine interaction audio, such as voice assistant).|
| SESSION_TYPE_VIDEO_CALL = 3 | Video call session (video call).|
| SESSION_TYPE_PHOTO = 4 | Photo session.|

### AVSession_PlaybackState

```c
enum AVSession_PlaybackState
```

**Description**

Enumerates the properties related to the media playback state.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| PLAYBACK_STATE_INITIAL = 0 | Initial state.|
| PLAYBACK_STATE_PREPARING = 1 | Preparing. The media resource is not ready for playback.|
| PLAYBACK_STATE_PLAYING = 2 | Playing.|
| PLAYBACK_STATE_PAUSED = 3 | Paused.|
| PLAYBACK_STATE_FAST_FORWARDING = 4 | Fast-forwarding.|
| PLAYBACK_STATE_REWINDED = 5 | Rewinding.|
| PLAYBACK_STATE_STOPPED = 6 | Stopped.|
| PLAYBACK_STATE_COMPLETED = 7 | Completed.|
| PLAYBACK_STATE_RELEASED = 8 | Released.|
| PLAYBACK_STATE_ERROR = 9 | Error.|
| PLAYBACK_STATE_IDLE = 10 | Idle.|
| PLAYBACK_STATE_BUFFERING = 11 | Buffering.|
| PLAYBACK_STATE_MAX = 12 | Maximum state. (Error code 401 is returned when the state value is **12**.)|

### AVSession_LoopMode

```c
enum AVSession_LoopMode
```

**Description**

Enumerates the loop modes of media playback.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| LOOP_MODE_SEQUENCE = 0 | Play in sequence.|
| LOOP_MODE_SINGLE = 1 | Single loop.|
| LOOP_MODE_LIST = 2 | Loop by playlist.|
| LOOP_MODE_SHUFFLE = 3 | Shuffle.|
| LOOP_MODE_CUSTOM = 4 | Custom playback.|

### AVSession_ControlCommand

```c
enum AVSession_ControlCommand
```

**Description**

Enumerates the playback control commands.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| CONTROL_CMD_INVALID = -1 | Invalid control command.|
| CONTROL_CMD_PLAY = 0 | Play command.|
| CONTROL_CMD_PAUSE = 1 | Pause command.|
| CONTROL_CMD_STOP = 2 | Stop command.|
| CONTROL_CMD_PLAY_NEXT = 3 | Command for playing the next media asset.|
| CONTROL_CMD_PLAY_PREVIOUS = 4 | Command for playing the previous media asset.|

### AVMetadata_SkipIntervals

```c
enum AVMetadata_SkipIntervals
```

**Description**

Enumerates the fast-forward or rewind skip intervals.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| SECONDS_10 = 10 | The interval is 10 seconds.|
| SECONDS_15 = 15 | The interval is 15 seconds.|
| SECONDS_30 = 30 | The interval is 30 seconds.|

### AVMetadata_DisplayTag

```c
enum AVMetadata_DisplayTag
```

**Description**

Enumerates the display tags for the media asset. The display tag is a special type identifier of the application media audio source.

**Since:** 13

| Enum Item| Description|
| -- | -- |
| AVSESSION_DISPLAYTAG_AUDIO_VIVID = 1 | HD audio.|

### AVSession_ConnectionState

```c
enum AVSession_ConnectionState
```

**Description**

Enumerates the device connection states.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| STATE_CONNECTING = 0 | The device is being connected.|
| STATE_CONNECTED = 1 | The device is connected.|
| STATE_DISCONNECTED = 6 | The device is in the default disconnected state.|

### AVSession_AVCastCategory

```c
enum AVSession_AVCastCategory
```

**Description**

Enumerates the casting categories in different playback scenarios.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| CATEGORY_LOCAL = 0 | Local casting. This value is used by default. Local media routing supports built-in speakers, audio jacks, and Advanced Audio Distribution Profile (A2DP) devices.|
| CATEGORY_REMOTE = 1 | Remote casting. The media is being displayed on a remote device, and the application needs a [OH_AVCastController](capi-ohavsession-oh-avcastcontroller.md) to control remote playback.|

### AVSession_DeviceType

```c
enum AVSession_DeviceType
```

**Description**

Enumerates the device types.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| DEVICE_TYPE_LOCAL = 0 | Built-in speaker or audio jack of the device.|
| DEVICE_TYPE_TV = 2 | TV.|
| DEVICE_TYPE_SMART_SPEAKER = 3 | Smart speaker.|
| DEVICE_TYPE_BLUETOOTH = 10 | Bluetooth device.|

### AVSession_ProtocolType

```c
enum AVSession_ProtocolType
```

**Description**

Enumerates the protocol types.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| TYPE_LOCAL = 0 | Local device, which is used by default. It includes the device's built-in speaker, audio jack, and A2DP (Advanced Audio Distribution Profile) devices.|
| TYPE_CAST_PLUS_STREAM = 2 | Cast+ stream mode. It indicates that the media is being displayed on another device. The application needs an **AVCastController** to control remote playback.|
| TYPE_DLNA = 4 | Digital Living Network Alliance (DLNA) protocol. It indicates that the device supports the DLNA protocol. The application needs an **AVCastController** to control remote playback.|
| TYPE_CAST_PLUS_AUDIO = 8 | Used to indicate that the device supports high-definition audio casting for better sound quality.|

### AVSession_AVCastControlCommandType

```c
enum AVSession_AVCastControlCommandType
```

**Description**

Enumerates the command types.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| CAST_CONTROL_CMD_PLAY = 0 | Play command.|
| CAST_CONTROL_CMD_PAUSE = 1 | Pause command.|
| CAST_CONTROL_CMD_STOP = 2 | Stop command.|
| CAST_CONTROL_CMD_PLAY_NEXT = 3 | Command for playing the next media asset.|
| CAST_CONTROL_CMD_PLAY_PREVIOUS = 4 | Command for playing the previous media asset.|
| CAST_CONTROL_CMD_FAST_FORWARD = 5 | Fast-forward command.|
| CAST_CONTROL_CMD_REWIND = 6 | Rewind command.|
| CAST_CONTROL_CMD_SEEK = 7 | Command for seeking to a playback position.|
| CAST_CONTROL_CMD_SET_VOLUME = 8 | Command for setting the volume.|
| CAST_CONTROL_CMD_SET_SPEED = 9 | Command for setting the playback speed.|

### AVSession_PlaybackSpeed

```c
enum AVSession_PlaybackSpeed
```

**Description**

Enumerates the playback speed types.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| SPEED_FORWARD_0_75_X = 0 | Plays the video at 0.75 times the normal speed.|
| SPEED_FORWARD_1_00_X = 1 | Plays the video at the normal speed (1.00x).|
| SPEED_FORWARD_1_25_X = 2 | Plays the video at 1.25 times the normal speed.|
| SPEED_FORWARD_1_75_X = 3 | Plays the video at 1.75 times the normal speed.|
| SPEED_FORWARD_2_00_X = 4 | Plays the video at 2 times the normal speed.|
| SPEED_FORWARD_0_50_X = 5 | Plays the video at 0.5 times the normal speed.|
| SPEED_FORWARD_1_50_X = 6 | Plays the video at 1.5 times the normal speed.|

### AVSession_PlaybackFilter

```c
enum AVSession_PlaybackFilter
```

**Description**

Enumerates the playback state filters.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| FILTER_STATE = 1 << 0 | State filter.|
| FILTER_POSITION = 1 << 1 | Position filter.|
| FILTER_SPEED = 1 << 2 | Speed filter.|
| FILTER_VOLUME = 1 << 3 | Volume filter.|
