# OH_AVScreenCaptureCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:53:23.725Z pushedAt=2026-09-20T02:21:57.921Z -->

```c
typedef struct OH_AVScreenCaptureCallback {...} OH_AVScreenCaptureCallback
```

## Overview

Defines all the asynchronous callback function pointers of an **OH_AVScreenCapture** instance. To ensure the normal running of **OH_AVScreenCapture**, the app must register the instance of this struct with the **OH_AVScreenCapture** instance to process the information reported by the callback functions. This callback set is used to monitor errors and the generation of audio and video data during screen capture. It is applicable to scenarios where screen capture data needs to be obtained and processed in real time. Through asynchronous processing, this method can effectively improve the efficiency of screen capture data processing.

Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) and [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AVScreenCaptureOnError](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonerror) onError | Callback triggered when an error occurs during screen capture, such as missing permissions or encoding errors. You can retry the operation or notify the user based on the error type. You need to register the struct instance that contains the callback with the **OH_AVScreenCapture** instance before receiving the error message reported using the callback. For details about the error codes, see [OH_AVSCREEN_CAPTURE_ErrCode](capi-native-avscreen-capture-errors-h.md#oh_avscreen_capture_errcode). Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnError](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onerror) instead. |
| [OH_AVScreenCaptureOnAudioBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonaudiobufferavailable) onAudioBufferAvailable | Callback triggered when data is available in the audio buffer during screen capture. You can obtain the audio buffer data in this callback for audio capture, encoding, or live streaming. You need to register the struct instance that contains the callback with the **OH_AVScreenCapture** instance before receiving the audio data reported using the callback. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |
| [OH_AVScreenCaptureOnVideoBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencaptureonvideobufferavailable) onVideoBufferAvailable | Callback triggered when data is available in the video buffer during screen capture. You can obtain the video buffer data in this callback for video capture, encoding, or live streaming. You need to register the struct instance that contains the callback with the **OH_AVScreenCapture** instance before receiving the video data reported using the callback. Starting from API version 12, you are advised to use [OH_AVScreenCapture_OnBufferAvailable](capi-native-avscreen-capture-base-h.md#oh_avscreencapture_onbufferavailable) instead. |


