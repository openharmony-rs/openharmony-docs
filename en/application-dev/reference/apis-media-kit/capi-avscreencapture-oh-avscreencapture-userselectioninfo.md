# OH_AVScreenCapture_UserSelectionInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:51:52.901Z pushedAt=2026-09-20T03:49:26.568Z -->

```c
typedef struct OH_AVScreenCapture_UserSelectionInfo OH_AVScreenCapture_UserSelectionInfo
```

## Overview

Describes the parameters selected by the user on the authorization UI (selection UI) by using **OH_AVScreenCapture_UserSelectionInfo**, such as the capture type and capture window. For example, in a screen capture app, after the user selects parameters such as the recording area and audio source, the app can use this struct to obtain the user's selection result.

This struct is used to carry the user's selection result in the screen capture authorization process. You can use this struct to read the user's authorization selection information after the authorization is complete. This struct is applicable to scenarios where an app needs to configure screen capture behavior based on the user's authorization selection, helping you flexibly adapt to users' screen capture preferences.

**Since**: 20

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

