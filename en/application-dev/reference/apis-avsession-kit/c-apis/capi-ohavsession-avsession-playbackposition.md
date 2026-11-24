# AVSession_PlaybackPosition

```c
typedef struct AVSession_PlaybackPosition {...} AVSession_PlaybackPosition
```

## Overview

Defines the playback position.

<!--Device-struct AVSession_PlaybackPosition {...}--><!--Device-struct AVSession_PlaybackPosition {...}-End-->

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-avsession-kit-ohavsession.md)

**Header file**: [native_avplaybackstate.h](capi-native-avplaybackstate-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t elapsedTime | Elapsed time(position) of this media set by the app.<br><!--Device-int64_t elapsedTime--><!--Device-int64_t elapsedTime-End--> |
| int64_t updateTime | Record the system time when elapsedTime is set.<br><!--Device-int64_t updateTime--><!--Device-int64_t updateTime-End--> |


