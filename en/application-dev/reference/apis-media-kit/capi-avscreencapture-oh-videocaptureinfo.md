# OH_VideoCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=320793da1b58e6a20565f5e582fc3e50f69572ee translatedAt=2026-06-22T03:38:29.552Z pushedAt=2026-06-22T09:23:26.599Z -->

```c
typedef struct OH_VideoCaptureInfo {...} OH_VideoCaptureInfo
```

## Overview

The struct describes the video capture information. When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t displayId | ID of the physical screen to capture. This member variable is valid when **capturemode** is set to **CAPTURE_SPECIFIED_SCREEN**.|
| int32_t* missionIDs | Mission ID list. This member variable is valid when **capturemode** is set to **CAPTURE_SPECIFIED_WINDOW**.|
| int32_t missionIDsLen | Length of the mission ID list. This member variable is valid when **capturemode** is set to **CAPTURE_SPECIFIED_WINDOW**.|
| int32_t videoFrameWidth | Width of the video to capture, in px.|
| int32_t videoFrameHeight | Height of the video to capture, in px.|
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | Video source type. Currently, only RGBA is supported.|