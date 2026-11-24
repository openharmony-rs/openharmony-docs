# OH_AudioInfo

```c
typedef struct OH_AudioInfo {...} OH_AudioInfo
```

## Overview

The struct describes the audio information.

<!--Device-struct OH_AudioInfo {...}--><!--Device-struct OH_AudioInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) micCapInfo | Audio capture info of microphone<br><!--Device-OH_AudioCaptureInfo micCapInfo--><!--Device-OH_AudioCaptureInfo micCapInfo-End--> |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) innerCapInfo | Audio capture info of inner<br><!--Device-OH_AudioCaptureInfo innerCapInfo--><!--Device-OH_AudioCaptureInfo innerCapInfo-End--> |
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) audioEncInfo | Audio encoder info, no need to set, while dataType = OH_ORIGINAL_STREAM<br><!--Device-OH_AudioEncInfo audioEncInfo--><!--Device-OH_AudioEncInfo audioEncInfo-End--> |


