# OH_AudioBuffer

```c
typedef struct OH_AudioBuffer {...} OH_AudioBuffer
```

## Overview

The struct describes the configuration such as the size, type, and timestamp of audio data.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t *buf | Audio buffer memory block |
| int32_t size | Audio buffer memory block size |
| int64_t timestamp | Audio buffer timestamp info, in nanosecond |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Audio capture source type |


