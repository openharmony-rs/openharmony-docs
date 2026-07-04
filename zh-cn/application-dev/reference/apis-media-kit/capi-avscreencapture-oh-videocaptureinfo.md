# OH_VideoCaptureInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_VideoCaptureInfo {/* 结构体成员定义详见下方成员变量表格 */ } OH_VideoCaptureInfo;
```

## 概述

视频录制信息。用于配置屏幕录制时的视频参数。适用于屏幕录制应用、视频会议录制、直播推流、游戏录制等场景。当videoFrameWidth和videoFrameHeight同时为0时，忽略视频相关参数不录制屏幕数据。

**起始版本：** 10

**相关模块：** [AVScreenCapture](capi-avscreencapture.md)

**所在头文件：** [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t displayId | 录制物理屏ID，使用该参数需要在captureMode为CAPTURE_SPECIFIED_SCREEN模式下使用，其他模式下此参数不生效。可通过系统显示管理接口获取有效的displayId值。 |
| int32_t* missionIDs | 指定窗口ID列表，适用于仅录制特定应用窗口内容的场景，如录制单个应用操作演示、避免录制桌面背景和隐私信息等。使用该参数需要在captureMode为CAPTURE_SPECIFIED_WINDOW模式下使用，其他模式下此参数不生效。 |
| int32_t missionIDsLen | 指定窗口ID列表的长度，使用该参数需要在captureMode为CAPTURE_SPECIFIED_WINDOW模式下使用，其他模式下此参数不生效。取值需大于0，且与missionIDs列表实际长度一致。 |
| int32_t videoFrameWidth | 采集视频的宽度设置，单位：px。取值范围需大于0。传入负数或超出设备支持分辨率时，屏幕录制将失败。 |
| int32_t videoFrameHeight | 采集视频的高度设置，单位：px。取值范围需大于0。传入负数或超出设备支持分辨率时，屏幕录制将失败。 |
| [OH_VideoSourceType](capi-native-avscreen-capture-base-h.md#oh_videosourcetype) videoSource | 视频采集格式设置，目前仅支持RGBA格式，设置其他格式时不支持该采集行为。 |


