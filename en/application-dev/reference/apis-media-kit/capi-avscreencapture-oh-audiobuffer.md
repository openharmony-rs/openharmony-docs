# OH_AudioBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=8a57bc09feb27a50652bff415f7d1214f3810a03 translatedAt=2026-09-15T16:45:37.529Z pushedAt=2026-09-20T01:27:36.005Z -->

```c
typedef struct OH_AudioBuffer {...} OH_AudioBuffer
```

## Overview

Defines the audio buffer data and its attributes such as the size, type, and timestamp.

During screen capture, this struct is filled with data by the system through the audio data callback. You can read the recorded audio frame data and its timestamp from this struct for subsequent audio processing or encoding. This struct is applicable to scenarios where the audio frame data needs to be obtained during screen capture.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t *buf | Pointer to the audio buffer memory. The memory is allocated and released by the system. You do not need to manually manage it. The audio buffer is used to store the recorded audio sample data in the format of original PCM byte stream. The data length needs to be determined based on this parameter and the **size** field. |
| int32_t size | Size of the audio buffer memory, in bytes. It indicates the length of the audio data pointed to by the **buf** pointer. The value must be greater than or equal to 0 and is filled by the system. If the value is negative, an error is reported. |
| int64_t timestamp | Timestamp of the audio buffer, in ns, indicating the time position of the audio frame. |
| [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) type | Type of the audio capture source. The value is determined by [OH_AudioCaptureSourceType](capi-native-avscreen-capture-base-h.md#oh_audiocapturesourcetype) configured in **OH_AudioCaptureInfo**. |


