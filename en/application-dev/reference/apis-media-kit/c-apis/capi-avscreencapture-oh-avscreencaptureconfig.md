# OH_AVScreenCaptureConfig

```c
typedef struct OH_AVScreenCaptureConfig {...} OH_AVScreenCaptureConfig
```

## Overview

The struct describes the screen capture configuration.

<!--Device-struct OH_AVScreenCaptureConfig {...}--><!--Device-struct OH_AVScreenCaptureConfig {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) recorderInfo | should be set, while dataType = OH_CAPTURE_FILE<br><!--Device-OH_RecorderInfo recorderInfo--><!--Device-OH_RecorderInfo recorderInfo-End--> |
| [OH_CaptureMode](capi-native-avscreen-capture-base-h.md#oh_capturemode) captureMode | <!--Device-OH_CaptureMode captureMode--><!--Device-OH_CaptureMode captureMode-End--> |
| [OH_DataType](capi-native-avscreen-capture-base-h.md#oh_datatype) dataType | <!--Device-OH_DataType dataType--><!--Device-OH_DataType dataType-End--> |
| [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md) audioInfo | <!--Device-OH_AudioInfo audioInfo--><!--Device-OH_AudioInfo audioInfo-End--> |
| [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md) videoInfo | <!--Device-OH_VideoInfo videoInfo--><!--Device-OH_VideoInfo videoInfo-End--> |


