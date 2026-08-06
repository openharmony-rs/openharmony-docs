# OH_VideoEncInfo

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:06:45.368Z pushedAt=2026-06-23T06:12:23.718Z -->

```c
typedef struct OH_VideoEncInfo {...} OH_VideoEncInfo
```

## Overview

The struct describes the video encoding information.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_VideoCodecFormat](capi-native-avscreen-capture-base-h.md#oh_videocodecformat) videoCodec | Video encoding format.|
| int32_t videoBitrate | Video capture bitrate. The unit is bits per second (bit/s). |
| int32_t videoFrameRate | Video capture frame rate. The unit is frames per second (FPS). |