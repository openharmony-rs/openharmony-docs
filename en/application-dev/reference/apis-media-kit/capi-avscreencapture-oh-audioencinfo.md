# OH_AudioEncInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:05:41.523Z pushedAt=2026-06-23T06:12:23.695Z -->

```c
typedef struct OH_AudioEncInfo {...} OH_AudioEncInfo
```

## Overview

The struct describes the audio encoding information.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t audioBitrate | Audio encoding bitrate. The unit is bits per second (bit/s). |
| [OH_AudioCodecFormat](capi-native-avscreen-capture-base-h.md#oh_audiocodecformat) audioCodecformat | Audio encoding format.|