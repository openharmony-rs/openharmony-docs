# OH_VideoCaptureInfo

```c
typedef struct OH_VideoCaptureInfo {...} OH_VideoCaptureInfo
```

## Overview

The struct describes the video capture information. When **videoFrameWidth** and **videoFrameHeight** are both **0**, video-related parameters are ignored and screen data is not recorded.

<!--Device-struct OH_VideoCaptureInfo {...}--><!--Device-struct OH_VideoCaptureInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t displayId | Display id, should be set while captureMode = CAPTURE_SPECIFIED_SCREEN<br><!--Device-uint64_t displayId--><!--Device-uint64_t displayId-End--> |
| int32_t *missionIDs | The ids of mission, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW<br><!--Device-int32_t *missionIDs--><!--Device-int32_t *missionIDs-End--> |
| int32_t missionIDsLen | Mission ids length, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW<br><!--Device-int32_t missionIDsLen--><!--Device-int32_t missionIDsLen-End--> |
| int32_t videoFrameWidth | Video frame width of avscreeencapture, in px<br><!--Device-int32_t videoFrameWidth--><!--Device-int32_t videoFrameWidth-End--> |
| int32_t videoFrameHeight | Video frame height of avscreeencapture, in px<br><!--Device-int32_t videoFrameHeight--><!--Device-int32_t videoFrameHeight-End--> |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | Video source type of avscreeencapture<br><!--Device-OH_VideoSourceType videoSource--><!--Device-OH_VideoSourceType videoSource-End--> |


