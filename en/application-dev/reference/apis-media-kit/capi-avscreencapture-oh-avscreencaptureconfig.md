# OH_AVScreenCaptureConfig
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:53:55.384Z pushedAt=2026-09-20T03:13:43.843Z -->

```c
typedef struct OH_AVScreenCaptureConfig {...} OH_AVScreenCaptureConfig
```

## Overview

Describes the screen capture configuration.

This method is used to configure the screen capture mode, data format, audio parameters, video parameters, and recording file parameters. It is applicable to scenarios where screen capture behavior needs to be customized, for example, selecting the recording mode, specifying the data output format, and setting audio and video encoding parameters.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_CaptureMode](capi-native-avscreen-capture-base-h.md#oh_capturemode) captureMode | Screen capture mode. The **captureMode** value determines the scope and the interaction mode of screen capture. You need to select a proper mode based on the screen area to be captured and interaction requirements. The options include **OH_CAPTURE_HOME_SCREEN** (capturing the home screen) and **OH_CAPTURE_SPECIFIED_WINDOW** (capturing a specified window). For details about the enumerated values, see [OH_CaptureMode](capi-native-avscreen-capture-base-h.md#oh_capturemode). |
| [OH_DataType](capi-native-avscreen-capture-base-h.md#oh_datatype) dataType | Data format of the screen capture stream. For example, if the recording stream data needs to be processed in real time, you can select the stream data format. If the data needs to be saved as a file, you can select the file data format. For details, see [OH_DataType](capi-native-avscreen-capture-base-h.md#oh_datatype). When the data format is **OH_CAPTURE_FILE**, [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) must be set. |
| [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md) audioInfo | Audio recording parameters, which are used to configure audio recording attributes. The parameters include the audio encoding format, sampling rate, and number of audio channels. For details, see [OH_AudioInfo](capi-avscreencapture-oh-audioinfo.md). |
| [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md) videoInfo | Video recording parameters, which are used to configure video recording attributes. The parameters include the video encoding format, resolution, and frame rate. For details, see [OH_VideoInfo](capi-avscreencapture-oh-videoinfo.md). |
| [OH_RecorderInfo](capi-avscreencapture-oh-recorderinfo.md) recorderInfo | Recording file information. This member variable is mandatory when the data type is **OH_CAPTURE_FILE**. If this parameter is not set, the recording cannot be started. |


