# OH_VideoInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:59:04.168Z pushedAt=2026-09-20T08:52:20.456Z -->

```c
typedef struct OH_VideoInfo {...} OH_VideoInfo
```

## Overview

Describes the video information.

This struct is used to configure the video capture parameters (such as the resolution and capture format) and encoding parameters during screen capture. It is applicable to scenarios where the screen capture video output parameters need to be customized. After configuring related parameters based on actual requirements, you can use this struct when calling screen capture APIs.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_VideoCaptureInfo](capi-avscreencapture-oh-videocaptureinfo.md) videoCapInfo | Video capture information, which is used to configure parameters such as the video capture area and resolution during screen capture. |
| [OH_VideoEncInfo](capi-avscreencapture-oh-videoencinfo.md) videoEncInfo | Video encoding parameters, which are used to configure the encoding format, bitrate, and frame rate of the screen capture output. Different encoding configurations have different image quality, file size, and encoding efficiency of the output video. |


