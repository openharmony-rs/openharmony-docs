# OH_AVScreenCapture
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:52:45.130Z pushedAt=2026-09-20T02:09:11.683Z -->

```c
typedef struct OH_AVScreenCapture OH_AVScreenCapture
```

## Overview

Describes a screen capture instance used to obtain original video and audio streams.

You need to create an instance and set capture parameters through related APIs, and then perform screen capture to obtain the stream data. For details about the design logic and implementation mechanism of the module, see [AVScreenCapture](capi-avscreencapture.md). It is applicable to scenarios where screen content and system/microphone audio need to be captured, such as screen capture and live streaming. It helps apps implement high-quality screen capture and obtain audio and video data.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

