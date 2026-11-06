# Camera_Rect
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct Camera_Rect {...} Camera_Rect
```

## 概述

相机矩形。用于各类检测对象的矩形框绘制。<br> 检测点坐标系以设备横向位置（充电口朝右）为基准。<br> 坐标系原点位于左上角 (0, 0)，右下角对应相机预览流的像素分辨率。<br> 所有参数均为整型像素值，其中topLeftX与topLeftY表示矩形左上角坐标，width与height分别表示矩形的宽高。

**起始版本：** 11

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t topLeftX | 矩形左上角的X坐标。<br>取值范围：[0, 预览流宽度]，例如对于1920*1440的预览流，取值范围为[0,1920]。 |
| int32_t topLeftY | 矩形左上角的Y坐标。<br>取值范围：[0, 预览流高度]，例如对于 1920*1440 的预览流，取值范围为[0,1440]。|
| int32_t width | 矩形宽度。<br>该值不超过坐标系X轴的上限，即topLeftX的最大值。 |
| int32_t height | 矩形高度。<br>该值不超过坐标系Y轴的上限，即topLeftY的最大值。 |


