# OH_AVScreenCaptureCallback

```c
struct OH_AVScreenCaptureCallback {...}
```

## Overview

Defines all the asynchronous callback function pointers of an **OH_AVScreenCapture** instance. To ensure the normal running of **OH_AVScreenCapture**, you must register the instance of this struct with the **<br>OH_AVScreenCapture** instance to process the information reported by the callback functions.

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-others-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror) onError |  |
| [OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable) onAudioBufferAvailable |  |
| [OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable) onVideoBufferAvailable |  |


