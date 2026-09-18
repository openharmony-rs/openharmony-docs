# AVSession_PlaybackPosition

```c
typedef struct AVSession_PlaybackPosition {...} AVSession_PlaybackPosition
```

## Overview

Defines the playback position.

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

**Header file**: [native_avplaybackstate.h](capi-native-avplaybackstate-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t elapsedTime | Elapsed time(position) of this media set by the app. |
| int64_t updateTime | Record the system time when elapsedTime is set. |


