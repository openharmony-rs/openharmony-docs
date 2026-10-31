# OH_VideoCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=37606c47a60d87c9daa80c6dd44ee31d834641f3 translatedAt=2026-09-15T16:57:59.854Z pushedAt=2026-09-20T07:50:05.551Z -->

```c
typedef struct OH_VideoCaptureInfo {...} OH_VideoCaptureInfo
```

## Overview

Defines the video capture information. This struct is used to configure the video parameters for screen capture. This struct must be used together with **captureMode**. In **CAPTURE_SPECIFIED_SCREEN** mode, **displayId** must be set to specify the physical screen. In **CAPTURE_SPECIFIED_WINDOW** mode, **missionIDs** must be set to specify the window. It is applicable to scenarios such as screen capture apps, video conference recording, live streaming, and game recording. When both **videoFrameWidth** and **videoFrameHeight** are set to **0**, the system ignores the configuration parameters for video capture and does not record the screen video data. This struct can be used to flexibly control the video capture behavior during screen capture.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t displayId | ID of the physical screen to be captured. After this parameter is set, the content of the specified physical screen is recorded. This parameter is valid only when **captureMode** is set to **CAPTURE_SPECIFIED_SCREEN**. You can obtain a valid **displayId** value by calling the system display management API. The value must be greater than or equal to 0. If an invalid ID is passed, the recording fails. |
| int32_t *missionIDs | Window ID array. After this parameter is set, the content of the specified window is recorded. This parameter is applicable to scenarios where only the content of a specific app window needs to be recorded, such as recording a single app operation demo or avoiding recording the desktop background and privacy information. This parameter is valid only when **captureMode** is set to **CAPTURE_SPECIFIED_WINDOW**. You can obtain a valid **missionID** value by calling the window API [getWindowProperties](../../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9). The array length must match **missionIDsLen**. The ID value must be an integer. If an invalid ID is passed, the recording fails. |
| int32_t missionIDsLen | Length of the window ID array. This parameter is valid only when **captureMode** is set to **CAPTURE_SPECIFIED_WINDOW**. The value must be greater than 0 and consistent with the actual length of the **missionIDs** array. |
| int32_t videoFrameWidth | Width of the video to capture, in pixels (px). The value must be greater than or equal to 0. If a negative value is passed or the value exceeds the resolution supported by the device, screen capture will fail. When both **videoFrameWidth** and **videoFrameHeight** are set to **0**, the system ignores the configuration parameters for video capture and does not record the screen video data. |
| int32_t videoFrameHeight | Height of the video to capture, in px. The value must be greater than or equal to 0. If a negative value is passed or the value exceeds the resolution supported by the device, screen capture will fail. When both **videoFrameWidth** and **videoFrameHeight** are set to **0**, the system ignores the configuration parameters for video capture and does not record the screen video data. |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | Video source type. Currently, only RGBA is supported. If this parameter is not set, RGBA is used by default. RGBA is applicable to scenarios where the original pixel data needs to be obtained for further processing. For details, see [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype). If other formats are set, this capture behavior is not supported. If both **videoFrameWidth** and **videoFrameHeight** are set to 0, this parameter does not take effect. |


