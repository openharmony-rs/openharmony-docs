# Camera_OcclusionDetectionResult
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} Camera_OcclusionDetectionResult
```

## 概述

相机镜头遮挡、脏污检测结果。

**起始版本：** 23

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool isCameraOccluded | 检查相机镜头是否被遮挡。true表示被遮挡，false表示未被遮挡。 |
| bool isCameraLensDirty | 检查相机相机镜头是否有脏污。true表示有脏污，false表示没有脏污。 |
