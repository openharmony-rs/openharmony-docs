# OH_NativeBuffer
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:44:41.954Z pushedAt=2026-09-18T10:07:39.216Z -->

```c
typedef struct OH_NativeBuffer OH_NativeBuffer
```

## Overview

Describes the original data buffer for screen capture. **OH_NativeBuffer** provides the capability of processing the original video data generated during screen capture. It can encapsulate, transmit, and manage the original video data.

It is used to carry the original video frame data obtained in the **AVScreenCapture** scenario. It can be used for secondary processing of screen capture data, such as pixel-level operations on screen capture frame data in video editing apps and encoding and pushing of original streams in live streaming scenarios.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

