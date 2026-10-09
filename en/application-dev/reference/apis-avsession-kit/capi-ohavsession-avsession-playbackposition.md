# AVSession_PlaybackPosition
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=23c78283c2fbf556eb3d88353a7151aeb7aecf0d translatedAt=2026-09-01T13:09:11.483Z pushedAt=2026-09-07T10:27:30.322Z -->

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
| int64_t elapsedTime | Elapsed time, in milliseconds. |
| int64_t updateTime | Updated time, in milliseconds. |


