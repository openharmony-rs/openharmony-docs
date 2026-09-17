# OH_VideoCaptureInfo

```c
typedef struct OH_VideoCaptureInfo {...} OH_VideoCaptureInfo
```

## Overview

The struct describes the video capture information. When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t displayId | Display id, should be set while captureMode = CAPTURE_SPECIFIED_SCREEN |
| int32_t *missionIDs | The ids of mission, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW |
| int32_t missionIDsLen | Mission ids length, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW |
| int32_t videoFrameWidth | Video frame width of avscreeencapture, in px |
| int32_t videoFrameHeight | Video frame height of avscreeencapture, in px |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | Video source type of avscreeencapture |


