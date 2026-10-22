# OH_AVScreenCapture_CaptureStrategy
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:50:36.455Z pushedAt=2026-09-20T02:32:37.575Z -->

```c
typedef struct OH_AVScreenCapture_CaptureStrategy OH_AVScreenCapture_CaptureStrategy
```

## Overview

Describes the screen capture strategy configured by using **OH_AVScreenCapture_CaptureStrategy**. This method can be used to configure screen capture behaviors, such as the recording scope, output format, and performance parameters. You can use this method to set screen capture parameters, adjust screen capture quality, and manage screen capture resources.

The screen capture strategy must be set by using the **OH_AVScreenCapture_SetCaptureStrategy** API before screen capture is started. The setting will not take effect after screen capture is started.

You can flexibly configure screen capture behaviors based on service requirements. This method is applicable to scenarios where screen capture strategies need to be customized, improving the applicability and controllability of the screen capture function.

**Since**: 20

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

