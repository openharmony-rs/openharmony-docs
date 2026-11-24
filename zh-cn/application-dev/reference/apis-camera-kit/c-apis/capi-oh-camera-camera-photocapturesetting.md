# Camera_PhotoCaptureSetting

```c
typedef struct Camera_PhotoCaptureSetting {...} Camera_PhotoCaptureSetting
```

## 概述

要设置的拍照捕获选项。

<!--Device-struct Camera_PhotoCaptureSetting {...}--><!--Device-struct Camera_PhotoCaptureSetting {...}-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 11

**相关模块：** [OH_Camera](capi-camera-kit-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Camera_QualityLevel](capi-camera-h.md#camera_qualitylevel) quality | 拍照图像质量。<br><!--Device-Camera_QualityLevel quality--><!--Device-Camera_QualityLevel quality-End--> |
| [Camera_ImageRotation](capi-camera-h.md#camera_imagerotation) rotation | 拍照旋转角度。<br><!--Device-Camera_ImageRotation rotation--><!--Device-Camera_ImageRotation rotation-End--> |
| [Camera_Location*](capi-oh-camera-camera-location.md) location | 拍照位置。<br><!--Device-Camera_Location* location--><!--Device-Camera_Location* location-End--> |
| bool mirror | 设置镜像拍照功能开关。<br> true为打开，false为关闭，默认为false。<br><!--Device-bool mirror--><!--Device-bool mirror-End--> |


