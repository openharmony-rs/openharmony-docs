# OH_AudioBuffer

```c
typedef struct OH_AudioBuffer {...} OH_AudioBuffer
```

## Overview

The struct describes the configuration such as the size, type, and timestamp of audio data.

<!--Device-struct OH_AudioBuffer {...}--><!--Device-struct OH_AudioBuffer {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t *buf | Audio buffer memory block<br><!--Device-uint8_t *buf--><!--Device-uint8_t *buf-End--> |
| int32_t size | Audio buffer memory block size<br><!--Device-int32_t size--><!--Device-int32_t size-End--> |
| int64_t timestamp | Audio buffer timestamp info, in nanosecond<br><!--Device-int64_t timestamp--><!--Device-int64_t timestamp-End--> |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Audio capture source type<br><!--Device-OH_AudioCaptureSourceType type--><!--Device-OH_AudioCaptureSourceType type-End--> |


