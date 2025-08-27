# OH_VideoCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @zengyawen-->

## 概述

视频录制信息。当videoFrameWidth和videoFrameHeight同时为0时，忽略视频相关参数不录制屏幕数据。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t displayId | 录制物理屏id，使用该参数需要在capturemode为CAPTURE_SPECIFIED_SCREEN模式下使用。 |
| int32_t* missionIDs | 指定窗口id列表，使用该参数需要在capturemode为CAPTURE_SPECIFIED_WINDOW模式下使用。 |
| int32_t missionIDsLen | 指定窗口ID长度，使用该参数需要在capturemode为CAPTURE_SPECIFIED_WINDOW模式下使用。 |
| int32_t videoFrameWidth | 采集视频的宽度设置，单位px。 |
| int32_t videoFrameHeight | 采集视频的高度设置，单位px。 |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | 视频采集格式设置，目前仅支持RGBA格式。 |


