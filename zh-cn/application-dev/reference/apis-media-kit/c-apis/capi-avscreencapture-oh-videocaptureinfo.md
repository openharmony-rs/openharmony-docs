# OH_VideoCaptureInfo

```c
typedef struct OH_VideoCaptureInfo {...} OH_VideoCaptureInfo
```

## 概述

视频录制信息。当videoFrameWidth和videoFrameHeight同时为0时，忽略视频相关参数不录制屏幕数据。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t displayId | Display id, should be set while captureMode = CAPTURE_SPECIFIED_SCREEN |
| int32_t *missionIDs | The  ids of mission, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW |
| int32_t missionIDsLen | Mission ids length, should be set while captureMode = CAPTURE_SPECIFIED_WINDOW |
| int32_t videoFrameWidth | Video frame width of avscreeencapture, in px |
| int32_t videoFrameHeight | Video frame height of avscreeencapture, in px |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | Video source type of avscreeencapture |


