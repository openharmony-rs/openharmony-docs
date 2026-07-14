# OH_AudioBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:05:24.484Z pushedAt=2026-06-23T06:12:23.690Z -->

```c
typedef struct OH_AudioBuffer {...} OH_AudioBuffer
```

## Overview

The struct describes the configuration such as the size, type, and timestamp of audio data.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t* buf | Pointer to an audio buffer.|
| int32_t size | Size of the audio buffer.|
| int64_t timestamp | Timestamp of the audio buffer. The unit is nanoseconds (ns). |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio capture source.|