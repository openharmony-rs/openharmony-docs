# OH_VideoEncInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:58:32.713Z pushedAt=2026-09-20T08:16:49.332Z -->

```c
typedef struct OH_VideoEncInfo {...} OH_VideoEncInfo
```

## Overview

Describes the video encoding information.

This struct is used to configure the video encoding parameters of screen capture, including the encoding format, bitrate, and frame rate. **videoCodec** specifies the encoding format (such as H.264 and H.265). **videoBitrate** affects the video definition and file size. **videoFrameRate** affects the video smoothness. Generally, these parameters are set before the screen capture API is called.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_VideoCodecFormat](capi-native-avscreen-capture-base-h.md#oh_videocodecformat) videoCodec | Video encoding format. The encoding format affects the video compression efficiency and compatibility. For details about the formats, see [OH_VideoCodecFormat](capi-native-avscreen-capture-base-h.md#oh_videocodecformat). |
| int32_t videoBitrate | Bitrate for video encoding, in bit/s. The value range depends on the encoding format and actual requirements. The default value is **10000000**. A larger value indicates better image quality but a larger file size. |
| int32_t videoFrameRate | Frame rate for video encoding, in frames per second (FPS). The value ranges from 15 to 60. |


