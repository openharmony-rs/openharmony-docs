# OH_AVScreenCaptureCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:06:13.584Z pushedAt=2026-06-23T06:12:23.707Z -->

```c
typedef struct OH_AVScreenCaptureCallback {...} OH_AVScreenCaptureCallback
```

## Overview

Defines all the asynchronous callback function pointers of an **OH_AVScreenCapture** instance. To ensure the normal running of **OH_AVScreenCapture**, you must register the instance of this struct with the **OH_AVScreenCapture** instance to process the information reported by the callback functions.

Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) and [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror) onError | Callback function invoked when an error occurs during the running of an **OH_AVScreenCapture** instance.<br>Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) instead.|
| [OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable) onAudioBufferAvailable | Callback function invoked when an audio buffer is available during the running of an **OH_AVScreenCapture** instance.<br>Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|
| [OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable) onVideoBufferAvailable | Callback function invoked when a video buffer is available during the running of an **OH_AVScreenCapture** instance.<br>Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.|