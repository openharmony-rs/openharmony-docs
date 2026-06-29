# AVSession_PlaybackPosition
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct AVSession_PlaybackPosition {...} AVSession_PlaybackPosition
```

## Overview

The struct describes the information related to the playback position.

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

**Header file**: [native_avplaybackstate.h](capi-native-avplaybackstate-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int64_t elapsedTime | Elapsed time, in ms.|
| int64_t updateTime | Updated time, in ms.|
